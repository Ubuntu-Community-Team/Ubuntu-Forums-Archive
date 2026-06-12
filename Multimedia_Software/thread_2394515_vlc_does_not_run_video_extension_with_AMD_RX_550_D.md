---
title: "vlc does not run video extension with AMD RX 550 Driver"
date: 2018-06-17
forum: Multimedia Software
---

### Post by pr0m3th3us on 2018-06-17
I use Ubuntu  18.04 64 bit, and I'm having a small problem, where I can not make  videos through Vlc after installing the Video Drive of the AMD Rx 550.
The Vlc will run, but without running any video extensions.
A dream is one test to remove the drive for so really even this, then I noticed that is this same.
The  video drive I downloaded on the AMD website and being a technical  version for the architecture of my Ubuntu that is  [amdgpu-pro-18.20-606296].

I was able to check the system logs for the error that appears.
With the AMD rx 550 Drive installed I can not play the videos. so can you solve this problem without removing the video drive?

 Erro Log
```
 Jun 17 18:48:03 PROMETHEUS org.kde.ActivityManager[2157]: ResourceScoreUpdated: "88c6a776-0059-4c19-8d74-1fdbc8abea8a" "vlc" "/home/well/Downloads/Best Vocal Deep House Mix  December 2016 [720p].mp4"
Jun 17 18:50:35 PROMETHEUS kernel: [14120.194665] vlc[11515]: segfault at 0 ip 00007f32d31ea3db sp 00007f32ec1b6740 error 4 in libQt5Core.so.5.9.5[7f32d3140000+53b000]
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]: Creating the cache for:  "/home/well/Downloads/Headhunterz & Sub Zero Project - Our Church (Official Video) [720p].mp4"
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]: Already in database?  true
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]:       First update :  QDateTime(2018-05-26 21:52:23.000 -03 Qt::TimeSpec(LocalTime))
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]:        Last update :  QDateTime(2018-06-02 12:25:16.000 -03 Qt::TimeSpec(LocalTime))
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]: After the adjustment
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]:      Current score :  1.80152
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]:       First update :  QDateTime(2018-05-26 21:52:23.000 -03 Qt::TimeSpec(LocalTime))
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]:        Last update :  QDateTime(2018-06-02 12:25:16.000 -03 Qt::TimeSpec(LocalTime))
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]: Interval length is  0
Jun 17 18:50:36 PROMETHEUS org.kde.ActivityManager[2157]:          New score :  2.80152


```
```
[SIZE=2]Jun 17 18:53:55 PROMETHEUS org.kde.ActivityManager[2157]: ResourceScoreUpdated: "88c6a776-0059-4c19-8d74-1fdbc8abea8a" "vlc" "/home/well/Downloads/Headhunterz & Sub Zero Project - Our Church (Official Video) [720p].mp4"
Jun 17 18:54:11 PROMETHEUS kernel: [14335.904281] kaffeine[11675]: segfault at 0 ip 00007f8c3eb41fcc sp 00007fff1df13b80 error 4 in libKF5ConfigCore.so.5.44.0[7f8c3eb28000+58000]
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]: Creating the cache for:  "/home/well/Downloads/Headhunterz & Sub Zero Project - Our Church (Official Video) [720p].mp4"
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]: Already in database?  false
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]:       First update :  QDateTime(2018-06-17 18:54:12.000 -03 Qt::TimeSpec(LocalTime))
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]:        Last update :  QDateTime(2018-06-17 18:54:12.000 -03 Qt::TimeSpec(LocalTime))
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]: After the adjustment
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]:      Current score :  0
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]:       First update :  QDateTime(2018-06-17 18:54:12.330 -03 Qt::TimeSpec(LocalTime))
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]:        Last update :  QDateTime(2018-06-17 18:54:12.000 -03 Qt::TimeSpec(LocalTime))
Jun 17 18:54:12 PROMETHEUS org.kde.ActivityManager[2157]:          New score :  0[/SIZE]
```

Device

```
root@PROMETHEUS:~# glxinfo | grep Device
    Device: Radeon 550 Series (POLARIS12 / DRM 3.25.0 AMD 18.20  / 4.15.0-23-generic, LLVM 6.0.1) (0x699f)
```


```
root@PROMETHEUS:~# glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 4.5
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
OpenGL core profile version string: 4.5 (Core Profile) Mesa 18.0.0
OpenGL core profile shading language version string: 4.50
OpenGL version string: 3.0 Mesa 18.0.0
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 18.0.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
root@PROMETHEUS:~# 
```

---

### Post by QIII on 2018-06-18
Hello!

Please use the default font size.

Also, please do not assume that everyone here is a male.

---

### Post by Yellow Pasque on 2018-06-18
Your post doesn't make sense to me. You say you've installed amdgpu-pro, but glxinfo shows the default open-source amdgpu driver.
I would recommend sticking with the open-source driver unless you need a feature that the Pro driver offers. 

There are Qt5 segfaults in your logs. There is no indication it is related to the video driver. Maybe if you gave a log from VLC with each driver (and clearly labelled which one was which), it would make more sense.

I'm also wondering how you installed VLC (.deb package or Snap?)

---

### Post by pr0m3th3us on 2018-06-18
greetings everyone.
My  vlc is give version of ubuntu 18.04, it came installed by default was  an apt-get package, it was running until I install this drive from AMD. but  now it does not run the video extensions, but if I just run vlc without  opening any extension it opens without opening any files.

---

### Post by pr0m3th3us on 2018-06-18
I apologize, it was not my intention to want to offend anyone.
I'm really sorry.

---

### Post by pr0m3th3us on 2018-06-19
greetings
With the AMD drive vlc shows this error.Jun 17 18:50:35 PROMETHEUS kernel: [14120.194665] vlc[11515]: segfault at 0 ip 00007f32d31ea3db sp 00007f32ec1b6740 error 4 in libQt5Core.so.5.9.5[7f32d3140000+53b000]

---

### Post by pr0m3th3us on 2018-06-21
```
_Jun 21 22:59:51 PROMETHEUS kernel: [ 1217.388419] vlc[12753]: segfault at 2d ip 00007fac504e9664 sp 00007fac299f56b0 error 4 in amdgpu_dri.so[7fac4f448000+21eb000]_
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]: Creating the cache for:  "/home/well/Downloads/Best Vocal Deep House Mix  December 2016 [720p].mp4"
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]: Already in database?  true
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]:       First update :  QDateTime(2018-05-31 18:31:14.000 -03 Qt::TimeSpec(LocalTime))
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]:        Last update :  QDateTime(2018-06-21 22:30:04.000 -03 Qt::TimeSpec(LocalTime))
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]: After the adjustment
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]:      Current score :  4.76499
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]:       First update :  QDateTime(2018-05-31 18:31:14.000 -03 Qt::TimeSpec(LocalTime))
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]:        Last update :  QDateTime(2018-06-21 22:30:04.000 -03 Qt::TimeSpec(LocalTime))
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]: Interval length is  0
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]:          New score :  5.76499
Jun 21 22:59:52 PROMETHEUS org.kde.ActivityManager[2354]: ResourceScoreUpdated: "88c6a776-0059-4c19-8d74-1fdbc8abea8a" "vlc" "/home/well/Downloads/Best Vocal Deep House Mix  December 2016 [720p].mp4"
```
-----------------------------------end-----------------------------
```
well@PROMETHEUS:~$ vlc -v
VLC media player 4.0.0-dev Otto Chriek (revision 4.0.0~rc1~~git20180621+r76452+146~ubuntu18.04.1)
[000055cf0c2eaff0] main stream filter warning: cannot insert stream filter record
[000055cf0c239580] main libvlc: Executando o VLC com a interface padrão. Use 'cvlc' para usar o VLC sem interface.
[000055cf0c2c7210] main playlist: playlist is empty
[00007fc0b8c07b90] mp4 demux warning: elst box found
[00007fc0b8c07b90] mp4 demux warning: STTS table of 1 entries
[00007fc0b8c07b90] mp4 demux warning: CTTS table of 5339 entries
[00007fc0b8c07b90] mp4 demux warning: STTS table of 1 entries
[00007fc0b8d79d50] faad decoder warning: decoded zero sample
```

---

