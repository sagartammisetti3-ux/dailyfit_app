name: Build Flutter APK

on:
  push:
    branches: [ "main" ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repo
        uses: actions/checkout@v3

      - name: Install Flutter
        uses: subosito/flutter-action@v2
        with:
          channel: "stable"

      - name: Flutter pub get
        run: flutter pub get

      - name: Build APK
        run: flutter build apk --release

      - name: Upload APK
        uses: actions/upload-artifact@v3
        with:
          name: dailyfit_app_apk
          path: build/app/outputs/flutter-apk/app-release.apk# dailyfit_app
fitness and helth details 
