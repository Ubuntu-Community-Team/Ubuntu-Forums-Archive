---
title: "Using VDPAU with MPlayer and VLC"
date: 2010-01-23
forum: Multimedia Software
---

### Post by perevera on 2010-01-23
I am trying to take advantage of VDPAU for playing video files with my ASRock ION 330.

As far as I know, MPlayer and VLC both include VDPAU support.

Ok then, I managed to make MPlayer work from the command line:

mplayer -vo vdpau -vc ffh264vdpau ./filename.mkv

In this way it plays a 720p content smoothly, with under 10% CPU use. Great!

The problem is when I try to make this permanent, i.e., configuring the files ~/.mplayer/config and ~/.mplayer/gui.conf.

This is what I have in there:

config
======
vo=vdpau,xv,
vc=ffh264vdpau,ffmpeg12vdpau, 

gui.conf
========
...
vo_driver = "vdpau"
...

But still, when I open MPlayer from the menu, no matter what file I try to open it gives this ugly message:

Error opening/initializing the selected video_out (-vo) device.

With regard to VLC, I had no luck, although I am using the latest "1.0.3 Goldeneye" version, I don't know how to make use of VDPAU.

So, please, if anybody has any hint, could he/she share it here with us?

---

### Post by Yellow Pasque on 2010-01-23
For VLC (doesn't look easy though): [http://forum.videolan.org/viewtopic.php?f=13&t=53928](http://forum.videolan.org/viewtopic.php?f=13&t=53928) Maybe there's a PPA somewhere that has it for you

For Mplayer, double-check your syntax. It looks like you have extra commas on the end of the vo and vc lines.

---

### Post by andrew.46 on 2010-01-23
Hi perevera,

> **perevera said:**
> With regard to VLC, I had no luck, although I am using the latest "1.0.3 Goldeneye" version, I don't know how to make use of VDPAU.

It is a small point but the latest version is actually:

```

andrew@skamandros~$ cvlc --version | head -n 1
VLC media player 1.1.0-git The Luggage
VLC version 1.1.0-git The Luggage (65113f5)

```

while the latest *release* version is actually 1.0.4, neither support vdpau. For MPlayer I would suggest you abandon the default gui of GMPlayer, as the MPlayer developers have, and install SMPlayer which should give you no trouble with vdpau.

All the best,

Andrew

---

### Post by perevera on 2010-02-08
Temüjin: No, the commas at the end of the line are alright, I found it somewhere.

Anyway, Andrew, you were right: SMPlayer is the good approach. I had to install it from SVN though, but it does not fit with the latest MPlayer, giving the following error:

/usr/bin/mplayer: symbol lookup error: /usr/bin/mplayer: undefined symbol: codec_wav_tags

All this is a mess, but alright, I managed to make it work as I mentioned: SMPlayer from SVN and MPlayer from packages. Of course, as the output driver you need to indicate "vdpau".

Thank you both.

---

