## 删减版WebRTC

### Android编译

1. 根据https://webrtc.googlesource.com/src/+/refs/heads/master/docs/native-code/android/index.md准备好编译环境, 并将src切本项目
   git remote add webrtc-client-native https://github.com/tencentyun/webrtc-client-native.git
   git fetch webrtc-client-native
   git checkout webrtc-client-native/master
   gclient sync -r bf053b6f3c7364c8e615b1f678339700be209cf7 --force
2. 生成编译文件夹
   gn gen out/Debug --args='target_os="android" target_cpu="arm"'
3. 替换编译配置文件
   cp args/android_arm.gn out/Debug/args.gn 或 cp args/android_arm64.gn out/Debug/args.gn
4. 编译
   ninja -C out/Debug
5. 拷贝out/Debug/libjingle_peerconnection_so.so到leb-android-sdk/lebwebrtcsdk/src/libs/arm64-v8a 或armeabi-v7a文件夹下
6. 拷贝out/Debug/lib.java/sdk/android/libwebrtc.jar到leb-android-sdk/lebwebrtcsdk/src/libs文件夹下 


### More info

 * Official web site: http://www.webrtc.org
 * Master source code repo: https://webrtc.googlesource.com/src
 * Samples and reference apps: https://github.com/webrtc
 * Mailing list: http://groups.google.com/group/discuss-webrtc
 * Continuous build: http://build.chromium.org/p/client.webrtc
 * [Coding style guide](style-guide.md)
 * [Code of conduct](CODE_OF_CONDUCT.md)
