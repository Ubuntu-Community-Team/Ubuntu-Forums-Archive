---
title: "video download helper"
date: 2023-11-23
forum: Multimedia Software
---

### Post by mv-879 on 2023-11-23
hello.

i am trying to use video download helper extension in firefox - [https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

the extension need "companion app" - it is supposed to be some ffmpeg backend or something. i have used it in the past on windows and it worked.

i have now downloaded and installed the app, but i am not sure how to continue. it doesn't seem to be running. 

```
[FONT=monospace][COLOR=#000000]~/Downloads$ sudo dpkg -i net.downloadhelper.coapp-1.6.3-1_amd64.deb   [/COLOR]
(Reading database ... 301209 files and directories currently installed.) 
Preparing to unpack net.downloadhelper.coapp-1.6.3-1_amd64.deb ... 
Unpacking net.downloadhelper.coapp (1.6.3) over (1.6.3) ... 
Setting up net.downloadhelper.coapp (1.6.3) ... 

$ locate downloadhelper 
/etc/chromium/native-messaging-hosts/net.downloadhelper.coapp.json 
/etc/opt/chrome/native-messaging-hosts/net.downloadhelper.coapp.json 
~/Downloads/net.downloadhelper.coapp-1.6.3-1_amd64.deb 
/opt/net.downloadhelper.coapp 
/opt/net.downloadhelper.coapp/LICENSE.txt 
/opt/net.downloadhelper.coapp/README.txt 
/opt/net.downloadhelper.coapp/bin 
/opt/net.downloadhelper.coapp/config.json 
/opt/net.downloadhelper.coapp/converter 
/opt/net.downloadhelper.coapp/bin/net.downloadhelper.coapp-linux-64 
/opt/net.downloadhelper.coapp/bin/xdg-open 
/opt/net.downloadhelper.coapp/converter/build 
/opt/net.downloadhelper.coapp/converter/build/linux 
/opt/net.downloadhelper.coapp/converter/build/linux/64 
/opt/net.downloadhelper.coapp/converter/build/linux/64/ffmpeg 
/opt/net.downloadhelper.coapp/converter/build/linux/64/ffplay 
/opt/net.downloadhelper.coapp/converter/build/linux/64/ffprobe 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libaom.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libavcodec.so.58 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libavdevice.so.58 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libavfilter.so.7 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libavformat.so.58 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libavresample.so.4 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libavutil.so.56 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libbz2.so.1.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libmp3lame.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libnuma.so.1 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libogg.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libopencore-amrnb.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libopencore-amrwb.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libopenjp2.so.7 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libopus.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/liborc-0.4.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/liborc-test-0.4.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libpostproc.so.55 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libswresample.so.3 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libswscale.so.5 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libtheora.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libtheoradec.so.1 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libtheoraenc.so.1 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libvo-amrwbenc.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libvorbis.so.0 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libvorbisenc.so.2 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libvorbisfile.so.3 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libvpx.so.6 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libwebp.so.7 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libwebpdecoder.so.3 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libwebpdemux.so.2 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libwebpmux.so.3 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libx264.so.161 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libx265.so.188 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libxvidcore.so.4 
/opt/net.downloadhelper.coapp/converter/build/linux/64/libz.so.1 
/usr/lib/mozilla/native-messaging-hosts/net.downloadhelper.coapp.json 
/usr/share/doc/net.downloadhelper.coapp 
/usr/share/doc/net.downloadhelper.coapp/copyright 
/var/lib/dpkg/info/net.downloadhelper.coapp.list 
/var/lib/dpkg/info/net.downloadhelper.coapp.md5sums
[/FONT]
```

there is something that looks like executable, which can be run in terminal, but doesn't give any output and it doesn't change the behaviour of extension in browser.

```
[FONT=monospace][COLOR=#000000]$ /opt/net.downloadhelper.coapp/bin/net.downloadhelper.coapp-linux-64 [/COLOR]
^C[/FONT]
```

[https://i.imgur.com/3M55T2H.png](https://i.imgur.com/3M55T2H.png)

any advice, please? thank you

---

