# Zee5 Launcher (Zee Marathi HD)

An ultra-lightweight, "invisible" Android application designed specifically for Android TVs. This app serves a single purpose: it acts as a launcher that instantly triggers a deep-link intent to open the **Zee Marathi HD** live TV channel directly within the official Zee5 app.

When combined with a utility like Button Mapper, this allows you to create a one-click, physical shortcut button on your TV remote for seamless, hands-free navigation.

## How It Works

The app has no visual interface (UI). When launched, it simply fires an `ACTION_VIEW` intent with the target Zee5 deep-link URL and immediately closes itself. 

- **Target App:** Zee5 (`com.graymatrix.did`)
- **Target URL:** `https://www.zee5.com/live-tv/zee-marathi-hd/0-9-zeemarathi`

## Requirements

- Android Studio or Gradle installed on your build machine (with Java 17+).
- An Android TV (e.g., TCL Android TV) with Developer Options and USB Debugging (ADB) enabled.
- The official **Zee5** app installed on your TV.
- **Button Mapper** (or similar button remapping app) installed on your TV.

## Download Pre-built APK

If you don't want to build the project yourself, you can simply download the pre-compiled APK directly from this repository:
[Download app-debug.apk](https://github.com/pratikgagare03/OneClickZee5LiveTvLauncher/blob/main/app/build/outputs/apk/debug/app-debug.apk)

## Building the APK (Optional)

If you wish to customize and build the APK yourself via the command line using the Gradle wrapper:

```bash
# Ensure JAVA_HOME points to Java 17
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64

# Build the debug APK
./gradlew assembleDebug
```

The compiled APK will be output to:
`app/build/outputs/apk/debug/app-debug.apk`

## Installation via ADB

1. **Connect to your TV:** Find your TV's IP address in your network settings and connect via ADB:
   ```bash
   adb connect <YOUR_TV_IP_ADDRESS>
   ```

2. **Install the APK:**
   ```bash
   adb install -r app/build/outputs/apk/debug/app-debug.apk
   ```

## Usage & Configuration

Once the app is installed on your TV, it will appear in your system as **"Zee Marathi"**, though it may not show up in the standard Leanback launcher UI depending on your TV model.

To map it to your remote:
1. Open the **Button Mapper** app on your Android TV.
2. Select the physical button on your remote that you wish to customize (e.g., a colored button or a redundant dedicated app button).
3. Set the action for the button (Single Tap, Double Tap, or Long Press) to **Open Application**.
4. Scroll through the list and select **Zee Marathi**.
5. Test your remote button—it should seamlessly open the Zee5 app directly to the Zee Marathi HD live stream!

## Customizing for Other Channels

To repurpose this launcher for a different Zee5 channel or another streaming app altogether:
1. Open `app/src/main/java/com/example/zee5launcher/MainActivity.java`.
2. Update the `Uri.parse("...")` string with your desired deep-link URL.
3. Update the `setPackage("...")` string with the target app's package name.
4. Open `app/src/main/AndroidManifest.xml` and change the `android:label="Zee Marathi"` to your new label.
5. Rebuild and install!
