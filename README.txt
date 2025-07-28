# S-Converter Android App

A React Native Android application that provides document conversion functionality including:
- Image to PDF conversion
- PDF to Image extraction
- Camera scanning with document processing

## Features

- **Image → PDF**: Convert multiple images into a single PDF document
- **PDF → Image**: Extract all pages from a PDF as individual images
- **Scan (Camera)**: Use device camera to scan documents and save as PDF or image
- **Mobile-Optimized UI**: Smooth, responsive design with touch-friendly controls
- **Modern Design**: Gradient backgrounds, rounded corners, and smooth animations

## Project Structure

```
SConverterApp/
├── App.tsx                    # Main React Native component with WebView
├── assets/                    # Web application files
│   ├── index.html            # Main HTML file with S-Converter logo
│   ├── style.css             # Enhanced mobile-optimized CSS
│   ├── app.js                # JavaScript functionality
│   └── logo.png              # S-Converter logo
├── android/                   # Android-specific configuration
│   └── app/
│       ├── src/main/
│       │   ├── AndroidManifest.xml  # Permissions and app configuration
│       │   ├── assets/              # Web files for WebView
│       │   └── res/                 # App icons and resources
│       └── build.gradle             # Build configuration
└── package.json              # Dependencies and scripts
```

## Setup Instructions

### Prerequisites
- Node.js (v14 or higher)
- React Native CLI
- Android Studio with Android SDK
- Java 17 JDK

### Installation

1. **Clone/Extract the project**
   ```bash
   cd SConverterApp
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up Android environment**
   ```bash
   export ANDROID_HOME=$HOME/Android/Sdk
   export PATH=$PATH:$ANDROID_HOME/emulator
   export PATH=$PATH:$ANDROID_HOME/tools
   export PATH=$PATH:$ANDROID_HOME/tools/bin
   export PATH=$PATH:$ANDROID_HOME/platform-tools
   export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
   ```

4. **Build the Android app**
   ```bash
   cd android
   ./gradlew assembleDebug
   ```

5. **Run on device/emulator**
   ```bash
   npx react-native run-android
   ```

## Key Enhancements Made

### UI/UX Improvements
- **Mobile-First Design**: Full-screen layout optimized for mobile devices
- **Enhanced Logo Integration**: S-Converter logo prominently displayed in header
- **Gradient Backgrounds**: Modern gradient styling throughout the app
- **Touch-Friendly Controls**: Larger buttons with proper touch targets (48px minimum)
- **Smooth Animations**: CSS transitions and hover effects for better interaction
- **Responsive Layout**: Adapts to different screen sizes and orientations

### Technical Improvements
- **WebView Integration**: Seamless integration of web app in React Native WebView
- **Permission Management**: Proper Android permissions for camera and file access
- **Asset Management**: Optimized asset loading and caching
- **Error Handling**: Comprehensive error handling for WebView operations
- **Performance**: Optimized JavaScript and CSS for mobile performance

### Android-Specific Features
- **App Icon**: Custom S-Converter logo as app icon
- **Splash Screen**: Branded splash screen experience
- **Permissions**: Camera, storage, and internet permissions configured
- **Build Configuration**: Optimized build settings for release

## Permissions Required

The app requests the following permissions:
- `INTERNET`: For loading external libraries and resources
- `CAMERA`: For document scanning functionality
- `READ_EXTERNAL_STORAGE`: For accessing user files
- `WRITE_EXTERNAL_STORAGE`: For saving converted documents
- `READ_MEDIA_IMAGES`: For accessing user images (Android 13+)

## Building for Release

1. **Generate a signing key**
   ```bash
   keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
   ```

2. **Configure signing in android/app/build.gradle**
   ```gradle
   signingConfigs {
       release {
           storeFile file('my-release-key.keystore')
           storePassword 'your-password'
           keyAlias 'my-key-alias'
           keyPassword 'your-password'
       }
   }
   ```

3. **Build release APK**
   ```bash
   cd android
   ./gradlew assembleRelease
   ```

The APK will be generated at: `android/app/build/outputs/apk/release/app-release.apk`

## Troubleshooting

### Common Issues

1. **Java Version Error**
   - Ensure Java 17 is installed and JAVA_HOME is set correctly

2. **Android SDK Not Found**
   - Install Android Studio and set ANDROID_HOME environment variable

3. **WebView Not Loading**
   - Check that assets are properly copied to android/app/src/main/assets/
   - Verify internet permissions in AndroidManifest.xml

4. **Camera Not Working**
   - Ensure camera permissions are granted
   - Test on physical device (camera doesn't work in emulator)

### Performance Tips

- Test on physical devices for accurate performance assessment
- Monitor memory usage during PDF processing
- Optimize image sizes before conversion
- Use appropriate image compression settings

## Development Notes

- The app uses a WebView to display the web-based S-Converter application
- All web assets are bundled with the app for offline functionality
- JavaScript libraries (jsPDF, PDF.js, JSZip) are loaded from CDN
- The UI is optimized for touch interaction with proper button sizing
- Responsive design ensures compatibility across different Android screen sizes

## Future Enhancements

- Native file picker integration
- Cloud storage integration
- Batch processing capabilities
- OCR text recognition
- Document templates
- Dark mode support

## License

All rights reserved of Md. Shohidul Islam

## Support

For technical support or questions about the app, please contact the development team.

