---
title: "10 Bit h265 Video Playback on Low end systems on ubuntu"
date: 2016-09-05
forum: Multimedia Software
---

### Post by vinu4 on 2016-09-05
I was trying to watch some videos after installing Ubuntu 16.04 on my Acer 4736z. Video file was mkv format 10 bit h.265.I used VLC media player and totem player.Both of them are playing the video in a choppy manner.I understand it is because of poor hardware configuration but in windows 8 I was able to play these videos smoothly after installing K-lite codek and doing some tweaking ap per this


[http://colormesubbed.com/improving-h264-performance-on-slower-pcs](http://colormesubbed.com/improving-h264-performance-on-slower-pcs)


I have latest update of Restricted extras and VLC/TOTEM


I tried installing gstreamer plugin


sudo apt-get install gstreamer0.10-libde265


and vlc plugin


sudo apt-get install vlc-plugin-libde265


but both says unable to locate package
Is there any way to configure any player in ubuntu to play these files ?

---

### Post by andrew.46 on 2016-09-06
Do you have a link to one of the videos that you were playing?

---

### Post by vinu4 on 2016-09-06
I don't have a link and they are huge files.But I can say they are 10 bit H265 MKV files.I am sure they should play smooth on other Ubuntu systems.Problem is with my Old laptop.But I need any tweak similar to the one I shared for windows.

---

### Post by Yellow Pasque on 2016-09-06
The link you gave switches to an alternative decoder for h.264 in a specific Windows program. I don't see how it's related to your issue or Linux in general (I could be wrong).

I'm going to guess you have an Intel GPU (from googling model number). I would make sure va-api is installed/working, but I don't think it's going to help you much with h.265 video though:

```
sudo apt-get install vainfo gstreamer1.0-vaapi gstreamer1.0-libav i965-va-driver
vainfo   #give output of this command
```

You can activate VA-API in VLC under Tools -> Preferences -> Input/Codecs.  Totem/gstreamer should use it automatically.

---

### Post by mc4man on 2016-09-06
I would guess that most of that windows stuff was related to subtitle rendering. As a curiosity you could see if you can play back any of the low bitrate hevc files here (8 or 10bit). They've no audio or sub streams so if you can't play one with similar bitrate to your files then no way with the audio/subs.
[http://jell.yfish.us/](http://jell.yfish.us/)

Those plugins you mentioned are not used in 16.04 & just enable hevc support (which you have), not make it less cpu/gpu intensive
(no way that hardware would have hevc hardware support, as it stands I'm not sure what hardware decoding for h264 it would have being it's 8 years old & was weak at birth.

---

### Post by Yellow Pasque on 2016-09-06
> **mc4man said:**
> (no way that hardware would have hevc hardware support, as it stands I'm not sure what hardware decoding for h264 it would have being it's 8 years old & was weak at birth.

I was thinking VA-API could help a bit with rendering the image. I'm not sure exactly what GPU the OP has, but if it's GMA X4500HD, it does support h.264 accel. If it's the non-HD variant, it only supports MPEG2

---

### Post by vinu4 on 2016-09-07
@ [[COLOR=#000000]Temüjin[/COLOR]]("https://ubuntuforums.org/member.php?u=327594")[COLOR=#000000] [/COLOR]Thanks for your reply. I was losing hope at askubuntu

```
sudo apt-get install vainfo gstreamer1.0-vaapi gstreamer1.0-libav i965-va-driver
[sudo] password for vineeth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
i965-va-driver is already the newest version (1.7.0-1).
i965-va-driver set to manually installed.
gstreamer1.0-libav is already the newest version (1.8.2-1~ubuntu1).
gstreamer1.0-libav set to manually installed.
The following additional packages will be installed:
  libva-wayland1
Suggested packages:
  gstreamer1.0-vaapi-doc
The following NEW packages will be installed:
  gstreamer1.0-vaapi libva-wayland1 vainfo
0 upgraded, 3 newly installed, 0 to remove and 28 not upgraded.
Need to get 260 kB of archives.
After this operation, 804 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 libva-wayland1 amd64 1.7.0-1 [8,240 B]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 gstreamer1.0-vaapi amd64 1.8.2-1~ubuntu2 [242 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 vainfo amd64 1.7.0-1 [9,558 B]
Fetched 260 kB in 2s (93.6 kB/s)
Selecting previously unselected package libva-wayland1:amd64.
(Reading database ... 234226 files and directories currently installed.)
Preparing to unpack .../libva-wayland1_1.7.0-1_amd64.deb ...
Unpacking libva-wayland1:amd64 (1.7.0-1) ...
Selecting previously unselected package gstreamer1.0-vaapi:amd64.
Preparing to unpack .../gstreamer1.0-vaapi_1.8.2-1~ubuntu2_amd64.deb ...
Unpacking gstreamer1.0-vaapi:amd64 (1.8.2-1~ubuntu2) ...
Selecting previously unselected package vainfo.
Preparing to unpack .../vainfo_1.7.0-1_amd64.deb ...
Unpacking vainfo (1.7.0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libva-wayland1:amd64 (1.7.0-1) ...
Setting up gstreamer1.0-vaapi:amd64 (1.8.2-1~ubuntu2) ...
Setting up vainfo (1.7.0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
```

@[mc4man]("https://ubuntuforums.org/member.php?u=320715") h264  Jellyfish videos are playing smooth but not HEVC.They are too choppy on Ubuntu .I think my videos play better.But they are playing smooth in windows media player classic.

---

### Post by Yellow Pasque on 2016-09-07
At this point, my only suggestion would be to try different Video Output options in VLC.
If possible, attach a screenshot of the "Playback -> Output" screen from MPC-HC's Options.

I've never been clear on whether one needs libva1-glx package and how to use it if so. I guess that's because I always use VDPAU and haven't touched VA-API too much.

---

### Post by vinu4 on 2016-09-08
Thanks for trying to help guys.I'm back to windows again as most of the time I use laptop for watching videos.And almost everything new is h265 in my laptop.Hope i can come back to ubuntu when i buy a better laptop.

---

