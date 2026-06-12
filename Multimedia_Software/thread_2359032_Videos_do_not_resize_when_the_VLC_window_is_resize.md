---
title: "Videos do not resize when the VLC window is resized, then VLC crashes at video stop"
date: 2017-04-20
forum: Multimedia Software
---

### Post by UbuntuWho on 2017-04-20
I've been having a LOT of problems with VLC lately. Whenever I play videos, they seem to stay in the top left corner at their default resolution even though I resize the VLC window or make it fullscreen. The videos don't grow or shrink no matter how I resize the window, and the weirdest thing is that VLC will crash shortly after stopping the video. I've tried several settings, but nothing seems to work, and I'm not sure what to mess with. I've even completely removed VLC including any settings and reinstalled, but the same issue occurs. I'm running Ubuntu 16.04, and I'm using VLC 2.2.2. What do I do?

I tried playing a DVD. Here is the result when running VLC through a terminal:
```
$ vlc
VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)
[00000000008e4148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

** (vlc:3485): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-49GrnJxlW7: Connection refused
libdvdnav: Using dvdnav version 5.0.3
libdvdnav: DVD Title: DVD_TITLE
libdvdnav: DVD Serial Number: 3af90e09
libdvdnav: DVD Title (Alternative): WS_R0
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000048e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000ac1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0029abb6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0029abba
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002b4337
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002b433c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002c3780
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002c3785
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002dfb94
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002dfb99
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002fb55b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002fb560
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002ff510
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002ff515
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00309856
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0030985a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0030ba59
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0030ba5d
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 0
[00007faf580009b8] core input error: ES_OUT_RESET_PCR called
[00007faf580009b8] core input error: ES_OUT_RESET_PCR called
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
[00007faf60000958] vdpau_avcodec generic error: decoder profile not supported: 2
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
Segmentation fault (core dumped)

```

I used a store-bought DVD, not a writable one. Not only are the menus not interactive, but VLC crashes or hangs when I click the stop button.

---

### Post by Perfect Storm on 2017-04-20
Perhaps v2.2.4 fixes the problem: [http://ubuntuhandbook.org/index.php/2016/07/install-latest-vlc-2-2-4-ubuntu-16-04-via-ppa/](http://ubuntuhandbook.org/index.php/2016/07/install-latest-vlc-2-2-4-ubuntu-16-04-via-ppa/)

---

### Post by UbuntuWho on 2017-04-20
Here's the output of running an MP4 on my local hard drive:
```
$ vlc
VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)
[0000000000c19148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

** (vlc:3928): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-49GrnJxlW7: Connection refused
[0000000000d26d88] dbus interface error: poll() failed: Interrupted system call
[0000000000d26d88] dbus interface error: poll() failed: Interrupted system call
[0000000000d26d88] dbus interface error: poll() failed: Interrupted system call
[0000000000d26d88] dbus interface error: poll() failed: Interrupted system call
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
[00007fae4cc33b38] avcodec decoder: Using OpenGL/VAAPI/libswscale backend for VDPAU for hardware decoding.
Segmentation fault (core dumped)

```

I tried an FLV. The video properly resizes, but VLC still crashes. The output of that:
```
$ vlc
VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)
[0000000000f25148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

** (vlc:3994): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-49GrnJxlW7: Connection refused
[0000000001032d88] dbus interface error: poll() failed: Interrupted system call
[0000000001032d88] dbus interface error: poll() failed: Interrupted system call
[0000000001032d88] dbus interface error: poll() failed: Interrupted system call
[0000000001032d88] dbus interface error: poll() failed: Interrupted system call
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
[00007fad1d02c7f8] avcodec decoder: Using OpenGL/VAAPI/libswscale backend for VDPAU for hardware decoding.
Segmentation fault (core dumped)

```

I tried GNOME's Videos application. I can pause the video without crashing, but it still produces an error:
```
$ totem

** (totem:4059): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-49GrnJxlW7: Connection refused

(totem:4059): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(totem:4059): GVFS-WARNING **: can't init metadata tree HOMEDIR/.local/share/gvfs-metadata/home: open: Permission denied

```

What is going on here?!? :confused:

---

### Post by UbuntuWho on 2017-04-20
Just saw your message, AI. I'll try it.

EDIT: Didn't work. It says my VLC is already the newest version. I'll try VLC's website; perhaps an upgrade is all I need?

---

### Post by Perfect Storm on 2017-04-20
You could ttry vlc 3.0 nightly build: [http://www.omgubuntu.co.uk/2016/06/install-vlc-3-0-ubuntu](http://www.omgubuntu.co.uk/2016/06/install-vlc-3-0-ubuntu)

---

### Post by UbuntuWho on 2017-04-20
Found the PPA (ppa:videolan/stable-daily), installed extra packages required by the current VLC version (which is still 2.2.2). Now the MP4 videos resize properly, but VLC still crashes. Any more help?

EDIT: Apparently, I'm a bit slow in receiving responses. Just got the Master PPA; fingers crossed...

---

### Post by UbuntuWho on 2017-04-20
Nope. Same problem. Just tried an MP4, and it won't resize again, also. Output:
```
$ vlc
VLC media player 3.0.0-git Vetinari (revision 3.0.0~~git20160813+r65787+62~ubuntu16.04.1)
[000000000110b1a8] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

** (vlc:9507): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-49GrnJxlW7: Connection refused
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
Segmentation fault (core dumped)
```

---

### Post by Perfect Storm on 2017-04-20
try with:
```
 sudo apt-get install i965-va-driver libva-intel-vaapi-driver vainfo
```

EDIt: Try this: [https://askubuntu.com/questions/302759/vaapi-not-working-in-ubuntu-13-04](https://askubuntu.com/questions/302759/vaapi-not-working-in-ubuntu-13-04)
> Its in Tools > Preferences > Input & Codecs > Enable Use GPU Accelerated decoding

---

### Post by UbuntuWho on 2017-04-20
Not there. Output:
```
$  sudo apt-get install i965-va-driver libva-intel-vaapi-driver vainfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
E: Unable to locate package libva-intel-vaapi-driver

```

---

### Post by Perfect Storm on 2017-04-20
funny it's not in the list, but it's here: [https://launchpad.net/ubuntu/yakkety/+package/i965-va-driver](https://launchpad.net/ubuntu/yakkety/+package/i965-va-driver)

EDIT 64bit: [http://launchpadlibrarian.net/248519578/i965-va-driver_1.7.0-1_amd64.deb](http://launchpadlibrarian.net/248519578/i965-va-driver_1.7.0-1_amd64.deb)

---

### Post by UbuntuWho on 2017-04-20
Not working still. Result:
```
$ vlc
VLC media player 3.0.0-git Vetinari (revision 3.0.0~~git20160813+r65787+62~ubuntu16.04.1)
[00000000025721a8] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
Segmentation fault (core dumped)
```

---

### Post by Perfect Storm on 2017-04-20
Have you tried switching settings in VLC?
I don't have VLC, but I think there are GUI: Tools -> Messages to check for further debug.

---

### Post by Perfect Storm on 2017-04-20
Also try:

```
vlc -vvv
```

---

### Post by mc4man on 2017-04-20
By default vlc has hardware accelerated decoding & video output both set to automatic which doesn't always pick right.
Maybe to start turn off hardware accelerated decoding & see if that helps in general. It's in Tools > Preferences > Output/Codecs > 1st option's  dropdown.
You may also want to specify video output, it's under the Video tab. Either pick OpenGl or if on very old hardware pick Xvideo

---

### Post by UbuntuWho on 2017-04-20
Output of that: [https://paste.ubuntu.com/24419753/](https://paste.ubuntu.com/24419753/)

---

### Post by UbuntuWho on 2017-04-20
> **mc4man said:**
> By default vlc has hardware accelerated decoding & video output both set to automatic which doesn't always pick right.
Maybe to start turn off hardware accelerated decoding & see if that helps in general. It's in Tools > Preferences > Output/Codecs > 1st option's  dropdown.
You may also want to specify video output, it's under the Video tab. Either pick OpenGl or if on very old hardware pick Xvideo

I disabled hardware accelerated encoding and chose OpenGL GLX Video Output (XCB). MP4s now scale properly, and no more crashes! :D Other video formats work fine now, too. Thanks a heap, mc4man!

Thanks to Artificial Intelligence for helping, also. I hope the pastebin in my previous post can still be of benefit.

---

