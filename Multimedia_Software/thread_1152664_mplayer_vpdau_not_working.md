---
title: "mplayer vpdau not working"
date: 2009-05-08
forum: Multimedia Software
---

### Post by Blackkitten on 2009-05-08
Hello everyone!
I'm running Ubuntu 9.04 on Acer Aspire 5920g ( CPU: T7500 GPU: GeForce 8600m GT with 185.19 beta drivers  )

My problem is rhat vpdau is not working.

I installed mplayer using this "How to" [http://ubuntuforums.org/showthread.php?t=558538]("http://ubuntuforums.org/showthread.php?t=558538")
And it seems running fine but when I try to play movie file

( > mplayer -vo vpdau /home/sam/&#1042;&#1080;&#1076;&#1077;&#1086;/Wrestler.2008.BD.Remux.1080p.H264.rus.eng.mkv )

I get something like this

> MPlayer SVN-r29274-4.3.3 (C) 2000-2009 MPlayer Team

Playing /home/sam/&#1042;&#1080;&#1076;&#1077;&#1086;/Wrestler.2008.BD.Remux.1080p.H264.rus.eng.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
....
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


And only auidio is playing:(.

Can somebody help me, please?

---

### Post by Blackkitten on 2009-05-08
It's VDPAU not VPDAU!
My mistake:P

---

### Post by xc3RnbFO8P on 2009-05-08
mplayer -vo **xv** vpdau /home/sam/&#1042;&#1080;&#1076;&#1077;&#1086;/Wrestler.2008.BD.Remux.1080p.H264.rus.eng.mkv

---

### Post by Blackkitten on 2009-05-08
Thank you for replying!
But i found that option -vo vdpau works fine.
I was misprinting all the time...

---

### Post by xc3RnbFO8P on 2009-05-08
I don't get video output if I use **mplayer -vo vpdau**

---

### Post by Blackkitten on 2009-05-08
> mplayer -vo vdpau -vc ffh264vdpau -ao sdl /home/sam/&#1042;&#1080;&#1076;&#1077;&#1086;/Wrestler.2008.BD.Remux.1080p.H264.rus.eng.mkv

This works for me well for sure.
But in order to use vdpau I need to specify codec with "-vc" command.

By the way Smplayer doesn't work with vdpau. It just stops when I open file.
Moreover I can't launch vdpau support from GUI in both players(Smplpayer and Gmplayer) only command line works.

Simplicity is good, but what is the problem may be?

---

### Post by rvm4000 on 2009-05-08
> **Blackkitten said:**
> By the way Smplayer doesn't work with vdpau. It just stops when I open file.

And what does the mplayer log say? 

I think it's necessary to disable some things (like the screenshots), or vdpau fails...

BTW, I added some support for vdpau in smplayer. From svn r2939 it automatically enables the vdpau codecs when the vdpau vo is used.

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by andrew.46 on 2009-05-08
Hi rvm,

> **rvm4000 said:**
> BTW, I added some support for vdpau in smplayer. From svn r2939 it automatically enables the vdpau codecs when the vdpau vo is used.

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

Thanks again for making all of this available! You have several PPAs available at the moment, can I ask if this one is the one you recommend people use?

All the best,

Andrew

---

### Post by rvm4000 on 2009-05-08
> **andrew.46 said:**
> Thanks again for making all of this available! You have several PPAs available at the moment, can I ask if this one is the one you recommend people use?

Well, as the name says, it's for testing. I will upload the packages there first, and people is welcome to test them but there's also the possibility that the packages could have problems.

---

### Post by Blackkitten on 2009-05-09
I downloaded .deb package from the launchpad. And now vdpau seems working.
The problem was in options. With vdpau post processing etc don't work. And the video doesn't play.

So it's great, now I don't have to manually choose -vo and -vc. 
But will be there an option for auto-disabling all the features that don't work with vpdau? It would be very useful.

Anyway, thanks for help!

---

### Post by _nico on 2009-10-13
**I installed so:**

```
sudo vi /etc/apt/sources.list

deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
``````
gpg --keyserver keyserver.ubuntu.com --recv 1DABDBB4CEC06767 && gpg --export --armor 1DABDBB4CEC06767 | sudo apt-key add - && sudo aptitude update

sudo aptitude install linux-headers-`uname -r` nvidia-185-kernel-source nvidia-185-libvdpau nvidia-settings smplayer mplayer-nogui

sudo nvidia-xconfig
```...restart KDE/GNOME Session (Ctrl+Alt+Backspace)

```
sudo nvidia-settings
```...set your resolution

```
sudo aptitude install libavcodec-unstripped-52 libavutil-unstripped-49
```Now, SMplayer -> Optionen > Allgemein -> Video &#8220;vdpau&#8221;. 
SMplayer restart!

It works fine.


**VDPAU without tearing**

...to the End

```
sudo vi /etc/X11/xorg.conf

Section "Extensions"
Option "Composite" "Disable"
EndSection
```or

```
nvidia-xconfig -no-composite
```[COLOR=Red][]("http://ubuntuforums.org/click%20here")[/COLOR]

---

### Post by abdusamed on 2010-06-12
I enable vdpau using smplayer video tab perferences.. i can only hear not see anything..! i did the terminal command like myplayer -vo or -vc vdpau.....some prob...

---

### Post by Linuxforall on 2010-06-12
For vdpau to work, apart from compiling your own following andrew46's instructions and compiling your own x264 and ffmpeg with Fake Outdoorsman's method, using RVM's ppa is the best way out, make sure to use both the ppa, for mplayer and smplayer.

---

### Post by abdusamed on 2010-06-12
where is that method??

---

### Post by Linuxforall on 2010-06-12
> **abdusamed said:**
> where is that method??

Which one?

ffmpeg and x264 compile here at [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

mplayer here at [http://ubuntuforums.org/showthread.php?t=1305181&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=1305181&highlight=mplayer)

---

