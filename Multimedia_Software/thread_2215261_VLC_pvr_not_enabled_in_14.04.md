---
title: "VLC pvr not enabled in 14.04"
date: 2014-04-05
forum: Multimedia Software
---

### Post by HNmYk3h on 2014-04-05
It seems that the PVR feature is not enabled in VLC 2.2.0.  Was this functionality replaced with something else?  Perhaps TV analog using v4l2?  I used to display mpg from my Hauppauge PVR-150 with a "vlc pvr:// :pvr-device="/dev/video0"" command but this no longer works.

---

### Post by cariboo on 2014-04-05
Does View->Advanced Controls Work for you?

---

### Post by HNmYk3h on 2014-04-07
> **cariboo907 said:**
> Does View->Advanced Controls Work for you?

Yes, but it only adds four icons for record, snapshot, loop, and frame by frame.

---

### Post by cariboo on 2014-04-07
Can you set the device in Media->Open Capture Device?

---

### Post by HNmYk3h on 2014-04-08
Yes, but there is no PVR tab here.  Under Capture Device tab I can choose Video camera or TV - analog, and then /dev/video0 in the device selection drop down, but no video is displayed.  Everything else is working because I can get mplayer to display PVR-150 video using the command  "mplayer pvr:// -profile ivtv".  Mplayer may allow me to get by but VLC used to work and I prefer VLC.  My assumption is that VLC is not currently compiled with enable-pvr.

---

### Post by cariboo on 2014-04-08
Andrew.46 created a thread a couple of hours ago on compiling VLC yourself, have a look [here]("http://ubuntuforums.org/showthread.php?t=2215743").

---

### Post by HNmYk3h on 2014-04-08
Thanks, timely post!

---

### Post by andrew.46 on 2014-04-08
> **HNmYk3h said:**
>  My assumption is that VLC is not currently compiled with enable-pvr.

The guide that I run only deals with vlc-git rather than the release version but I note that in the development version at least the option *--enable-pvr* is not present (and was probably[ removed in 2012]("http://git.videolan.org/?p=vlc.git;a=commitdiff;h=fb1dcab36e7c3a49d49562334045e4f87980ac03")) and certainly the version that I build does not have a PVR tab either. Very curious...

---

### Post by HNmYk3h on 2014-04-10
From snooping around in the changelogs and open_panels.cpp, it looks like they may have replaced the PVR feature with the "TV- analog" feature.  But I cannot get my PVR-150 to display using TV - analog in the Capture device menu. I'm looking into avconv as a replacement for VLC in my attempt to use the PVR-150 as input and stream the output.

---

### Post by andrew.46 on 2014-04-10
Difficult to test as I do not have access to such a device. Perhaps try on the videolan forums:

VLC media player for Linux and friends Troubleshooting
[https://forum.videolan.org/viewforum.php?f=13&sid=fe4be6bfd3a0d572d915a28dbac7ca2a](https://forum.videolan.org/viewforum.php?f=13&sid=fe4be6bfd3a0d572d915a28dbac7ca2a)

but be aware the developers can be a little brusque at times....

---

### Post by HNmYk3h on 2014-04-10
I think I found a solution with  avconv:

```
avconv -i /dev/video0 -c copy -c:v h264 -f mpegts udp://<destination-ip-address>:5004
```

At the destination I use VLC and open udp://@:5004

I need to check video quality and a/v sync more closely but it seems to work.

---

### Post by jiskefet2 on 2014-04-30
Found this in the wiki: [https://wiki.videolan.org/Documentation:Modules/v4l2](https://wiki.videolan.org/Documentation:Modules/v4l2)

You need to use the 'compressed' alias (v4l2 with c):
```
vlc 'v4l2c://'
```

The frequency setting doesn't work though, it has a strange factor on it. If you enter for example 50, then you get 195.3125 MHz, so you never can set an integer value.

```
vlc 'v4l2c://:tuner-frequency=50'
```

As a workarround you can use this (for 216MHz):

```
ivtv-tune -f 216 && vlc 'v4l2c://'
```

Opening the TV from the VLC GUI doesn't seem to be possible. The only way I got it to work was through the "Network" tab and entering "v4l2c://" as URL. This does not allow for setting a frequency though, that would still have to be done from a commandline (ivtv-tune -f 216).

---

### Post by cariboo on 2014-04-30
Moved to Multimedia & Video, as 14.04 has been released, and is no longer in development.

---

