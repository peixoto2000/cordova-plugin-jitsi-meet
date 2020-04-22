# cordova-plugin-jitsi-meet
Cordova plugin for Jitsi Meet React Native SDK. Works with both iOS and Android, and fixes the 64-bit binary dependency issue with Android found in previous versions of this plugin.

# Summary 
I created this repo as there were multiple versions of this plugin, one which worked for iOS and Android, but neither worked with both. This verison satisfies the 64bit requirement for Android and also works in iOS and is currently being used in production.

# Installation
`cordova plugin add https://github.com/peixoto2000/cordova-plugin-jitsi-meet`

## iOS Settings
In the current version it is no longer necessary WebRTC and JitsiMeet frameworks manually to be embedded in the iOS/Xcode interface.

For iOS, it is necessary to describe the permissions below in the "config.xml" file to access the camera and microphone:
```
<platform name="ios">
  <config-file platform="ios" target="*-Info.plist" parent="NSMicrophoneUsageDescription">
    <string>This application requires access to your microphone in order for you to speak through the service offered.</string>
  </config-file>
  <config-file platform="ios" target="*-Info.plist" parent="NSCameraUsageDescription">
    <string>This application requires access to your Camera in order to take a picture of the service offered.</string>
  </config-file>
</platform>
```


# Usage
```
const roomId = 'your-custom-room-id';

jitsiplugin.loadURL('https://meet.jit.si/' + roomId, roomId, false, function (data) {
    if (data === "CONFERENCE_WILL_LEAVE") {
        jitsiplugin.destroy(function (data) {
            // call finished
        }, function (err) {
            console.log(err);
        });
    }
}, function (err) {
    console.log(err);
});
```
