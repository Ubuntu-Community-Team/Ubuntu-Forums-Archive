---
title: "Webcam wroks before but not now"
date: 2008-10-16
forum: Multimedia Software
---

### Post by kkfok1 on 2008-10-16
I got the webcam works before but not now. In between of these few months, there were several recommended updates being made. The problem is Cheese not able to see the video/picture even though the USB webcam is detected without problem. From the below log made by dmesg, the webcam video looading without problem. However, when I start the Cheese program, there were some messages that I have never seen before and Cheese not able to show the picture/video.

Any help is very much appreciated.

Thanks
 

******* dirver loading *****************

[ 2889.828943] usbcore: deregistering interface driver uvcvideo
[ 2918.296171] Linux video capture interface: v2.00
[ 2918.298776] uvcvideo: Adding mapping Brightness to control 00000000-0000-0000-0000-000000000101/2.
[ 2918.298780] uvcvideo: Adding mapping Contrast to control 00000000-0000-0000-0000-000000000101/3.
[ 2918.298783] uvcvideo: Adding mapping Hue to control 00000000-0000-0000-0000-000000000101/6.
[ 2918.298786] uvcvideo: Adding mapping Saturation to control 00000000-0000-0000-0000-000000000101/7.
[ 2918.298789] uvcvideo: Adding mapping Sharpness to control 00000000-0000-0000-0000-000000000101/8.
[ 2918.298792] uvcvideo: Adding mapping Gamma to control 00000000-0000-0000-0000-000000000101/9.
[ 2918.298795] uvcvideo: Adding mapping Backlight Compensation to control 00000000-0000-0000-0000-000000000101/1.
[ 2918.298798] uvcvideo: Adding mapping Gain to control 00000000-0000-0000-0000-000000000101/4.
[ 2918.298801] uvcvideo: Adding mapping Power Line Frequency to control 00000000-0000-0000-0000-000000000101/5.
[ 2918.298805] uvcvideo: Adding mapping Hue, Auto to control 00000000-0000-0000-0000-000000000101/16.
[ 2918.298808] uvcvideo: Adding mapping Exposure, Auto to control 00000000-0000-0000-0000-000000000001/2.
[ 2918.298812] uvcvideo: Adding mapping Exposure, Auto Priority to control 00000000-0000-0000-0000-000000000001/3.
[ 2918.298815] uvcvideo: Adding mapping Exposure (Absolute) to control 00000000-0000-0000-0000-000000000001/4.
[ 2918.298819] uvcvideo: Adding mapping White Balance Temperature, Auto to control 00000000-0000-0000-0000-000000000101/11.
[ 2918.298823] uvcvideo: Adding mapping White Balance Temperature to control 00000000-0000-0000-0000-000000000101/10.
[ 2918.298826] uvcvideo: Adding mapping Focus (absolute) to control 00000000-0000-0000-0000-000000000001/6.
[ 2918.298830] uvcvideo: Adding mapping Focus, Auto to control 00000000-0000-0000-0000-000000000001/8.
[ 2918.298855] uvcvideo: Probing generic UVC device 2
[ 2918.298862] uvcvideo: Found format YUV 4:2:2 (YUYV).
[ 2918.298864] uvcvideo: - 640x480 (30.0 fps)
[ 2918.298865] uvcvideo: - 160x120 (30.0 fps)
[ 2918.298867] uvcvideo: - 320x240 (30.0 fps)
[ 2918.298868] uvcvideo: - 352x288 (30.0 fps)
[ 2918.298869] uvcvideo: - 176x144 (30.0 fps)
[ 2918.298873] uvcvideo: Found a Status endpoint (addr 85).
[ 2918.298875] uvcvideo: Found UVC 1.00 device DEF-299A Camera (1871:0603)
[ 2918.298878] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/2 to device 2 entity 3
[ 2918.298881] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/3 to device 2 entity 3
[ 2918.298884] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/7 to device 2 entity 3
[ 2918.298887] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/8 to device 2 entity 3
[ 2918.298890] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/9 to device 2 entity 3
[ 2918.298893] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/5 to device 2 entity 3
[ 2918.298897] uvcvideo: Scanning UVC chain: OT 2 <- XU 4 <- PU 3 <- IT 1
[ 2918.298900] uvcvideo: Found a valid video chain (1 -> 2).
[ 2918.301321] uvcvideo: UVC device initialized.
[ 2918.301336] usbcore: registered new interface driver uvcvideo
[ 2918.301339] USB Video Class driver (v0.1.0)
[ 2918.306462] uvcvideo: Trying format 0x56595559 (YUYV): 10000x10000.
[ 2918.306467] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).


*********** after Cheese started ****************

[ 2918.306467] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[ 3693.752164] uvcvideo: Control 0x00980903 not found.
[ 3693.752169] uvcvideo: Control 0x00980904 not found.
[ 3693.752171] uvcvideo: Control 0x00980905 not found.
[ 3693.752173] uvcvideo: Control 0x00980906 not found.
[ 3693.752174] uvcvideo: Control 0x00980907 not found.
[ 3693.752176] uvcvideo: Control 0x00980908 not found.
[ 3693.752178] uvcvideo: Control 0x00980909 not found.
[ 3693.752180] uvcvideo: Control 0x0098090a not found.
[ 3693.752181] uvcvideo: Control 0x0098090b not found.
[ 3693.752183] uvcvideo: Control 0x0098090c not found.
[ 3693.752185] uvcvideo: Control 0x0098090d not found.
[ 3693.752187] uvcvideo: Control 0x0098090e not found.
[ 3693.752189] uvcvideo: Control 0x0098090f not found.
[ 3693.766770] uvcvideo: Control 0x00980911 not found.
[ 3693.766776] uvcvideo: Control 0x00980912 not found.
[ 3693.766778] uvcvideo: Control 0x00980913 not found.
[ 3693.766781] uvcvideo: Control 0x00980914 not found.
[ 3693.766782] uvcvideo: Control 0x00980915 not found.
[ 3693.766784] uvcvideo: Control 0x00980916 not found.
[ 3693.766786] uvcvideo: Control 0x00980917 not found.
[ 3693.767081] uvcvideo: Trying format 0x56595559 (YUYV): 176x144.
[ 3693.767084] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[ 3693.775956] uvcvideo: Setting frame interval to 1/30 (333333).

---

### Post by onfyreforjesus on 2008-10-18
Same problem here.. Just upgraded to Intrepid.
lsusb shows webcam plugged in. Used to work well with hardy. 

In fact, all the other camera apps dont work. and gstreamer video tab says cannot locate /dev/video0.

---

### Post by trusty on 2008-10-20
Since "upgrading" to Intrepid, my webcam(s) have also stopped working:
[FONT="Courier New"][B][SIZE="1"][INDENT]root@stite:~# lsusb
[COLOR="Red"]Bus 005 Device 004: ID 0402:5602 ALi Corp. Video Camera Controller[/COLOR]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 001 Device 003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam[/COLOR]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 147a:e020 Formosa Industrial Computing, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/INDENT][/SIZE][/B][/FONT]
I also have no video device:
[FONT="Courier New"][SIZE="1"][B][INDENT]root@stite:~# ls -l /dev/v*
crw-rw---- 1 root root 7,   0 2008-10-21 17:42 /dev/vcs
crw-rw---- 1 root root 7,   1 2008-10-21 07:42 /dev/vcs1
crw-rw---- 1 root root 7,   2 2008-10-21 07:42 /dev/vcs2
crw-rw---- 1 root root 7,   3 2008-10-21 07:42 /dev/vcs3
crw-rw---- 1 root root 7,   4 2008-10-21 07:42 /dev/vcs4
crw-rw---- 1 root root 7,   5 2008-10-21 07:42 /dev/vcs5
crw-rw---- 1 root root 7,   6 2008-10-21 07:42 /dev/vcs6
crw-rw---- 1 root root 7,   7 2008-10-21 07:42 /dev/vcs7
crw-rw---- 1 root root 7,   8 2008-10-21 17:42 /dev/vcs8
crw-rw---- 1 root root 7, 128 2008-10-21 17:42 /dev/vcsa
crw-rw---- 1 root root 7, 129 2008-10-21 07:42 /dev/vcsa1
crw-rw---- 1 root root 7, 130 2008-10-21 07:42 /dev/vcsa2
crw-rw---- 1 root root 7, 131 2008-10-21 07:42 /dev/vcsa3
crw-rw---- 1 root root 7, 132 2008-10-21 07:42 /dev/vcsa4
crw-rw---- 1 root root 7, 133 2008-10-21 07:42 /dev/vcsa5
crw-rw---- 1 root root 7, 134 2008-10-21 07:42 /dev/vcsa6
crw-rw---- 1 root root 7, 135 2008-10-21 07:42 /dev/vcsa7
crw-rw---- 1 root root 7, 136 2008-10-21 17:42 /dev/vcsa8
root@stite:~# [/INDENT][/B][/SIZE][/FONT]
I have read on other posts that the kernel development team are aware of the problem.  Does anyone know of a workaround for now?

---

### Post by jdeslip on 2008-10-24
The integrated laption in my Dell 1420 (uses uvcvideo driver) also stopped working after upgrading to intrepid yesterday.  Is uvcvideo just plain broken in intrepid?

---

### Post by jdeslip on 2008-10-24
I found this bug report and can confirm the conclusion that by compiling your own uvcvideo module from svn and replacing the one that shipped with the intrepid kernel fixes the problem.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888)

---

### Post by Samir33 on 2008-10-26
Unfortunately, recompiling fresh uvcvideo driver from SVN didnt solve this one for me. 

My camera (Sanyo W33SA) worked fine in Hardy, it even seems to be working fine in Intrepid when using Ekiga and luvcview. No go in gstreamer apps (cheese).

Could this be a gstreamer bug?

Seems there are regressions with gstreamer and some other webcam drivers concerning the integration with libv4l library (format conversion library recently introduced). Maybe same stuff happens here with uvcvideo / gstreamer / libv4l combination?

---

### Post by HDave on 2008-11-03
I have the same problem -- Intrepid Upgrade breaking Web Cam.

I noticed however that Skype works.  I found a bug report which could explain why Skype works and most everything else doesn't.  Looks like lots of active work and patching is underway.

[https://bugs.launchpad.net/ubuntu/intrepid/+source/amsn/+bug/260918]("https://bugs.launchpad.net/ubuntu/intrepid/+source/amsn/+bug/260918")

---

### Post by patrickballeux on 2008-11-03
You can validate your webcam using this in a terminal

```

gst-launch v4l2src ! video/x-raw-yuv,width=320,height=240 ! ffmpegcolorspace ! ximagesink

```

I found out that sometimes, the uvcmodule needs to be reloaded...

```

sudo rmmod uvcvideo
sudo modprobe uvcvideo

```

Cheese is kind of broken since Hardy for me.  So I simply removed it.  As for other webcam software, they almost only support V4L devices and not V4L2 devices. With the new Flash 10, now V4L2 devices are properly detected.

If you can make it work using the gst-launch, it means that your driver is working (or at least usable by unloading/reloading).

Good luck!

---

### Post by richbl on 2008-11-07
> **patrickballeux said:**
> 

I found out that sometimes, the uvcmodule needs to be reloaded...

```

sudo rmmod uvcvideo
sudo modprobe uvcvideo

```



Thanks for the modprobe reload. This appears to have worked for me. Prior to this, luvcview and mjpg_streamer would fail.

**HOWEVER... I have found something interesting...**

If I reload uvcvideo and test with luvcview and/or mjpg_streamer, things work as expected. 

BUT, if I fire up Skype and do a video test (Options/Video), then close Skype, I once again lose functionality of luvcview and mjpg_streamer.

Only after reloading the uvcvideo driver will I again have functionality.

I'd assert that this would probably be true if I fired up Ekiga or Cheese, or any other application that somehow affects the uvcvideo driver.

Can anyone elaborate on WHY this might be?

Are there any tools that I might be able to use to further troubleshoot this issue? I'd like to either post a bug or add to an existing bug this information.

Thanks.

---

### Post by jdeslip on 2008-11-07
In my case, removing and reloading the uvcvideo module does not solve the problem with the module shipped with intrepid.  

Inserting the module built from svn does solve it, however.

---

