---
title: "Gutsy - Video random stall for several sec, sound is ok"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by fseto on 2007-11-14
The problem:  On video playback of .avi / .mkv (probably others too), randomly in the middle of the video, the frame will just freeze and pause for about 3-5 sec.  During this time, the audio is ok.

I've tried using totem, mplayer, & smplayer.  And it happens on all 3, although more frequently in totem.  I know that the video file is fine, as it plays ok in other OS.  And if I rewind and play it again, it would play fine.  

Any suggestions?  Is this happening for others too?  Thanks.

My PC:
Ubuntu 7.10 - AMD64
Dell C521- 4GB RAM
NV 6150 - nvidia-glx-new driver

---

### Post by waldrepdebater on 2007-11-14
I used to get the same problem all the time in Vista and OSX.  It might not be ubuntu at all.

---

### Post by fseto on 2007-11-14
This is not a problem on my system in WinXP or Vista.  I only see it when running Ubuntu.  Granted, I'm not running other distros, so I can't say whether it's specific to Ubuntu or not.  Or even whether it's just 64bit vs 32.

---

### Post by vivichrist on 2007-12-04
I have this exact same problem but does your system video stall intermittently in general mine does. do you get:

(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000b960, 0x0000b970)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000b970, 0x0000b970)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00006e38, 0x00006e48)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00006e48, 0x00006e48)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x000067c4, 0x000067d4)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x000067d4, 0x000067d4)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000aa74, 0x0000aa84)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000aa84, 0x0000aa84)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000935c, 0x0000936c)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000936c, 0x0000936c)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000a340, 0x0000a350)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000a350, 0x0000a350)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000ece0, 0x0000ecf0)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000ecf0, 0x0000ecf0)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000508c, 0x0000509c)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000509c, 0x0000509c)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x000017b4, 0x000017c4)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x000017c4, 0x000017c4)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00004ab0, 0x00004ac0)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00004ac0, 0x00004ac0)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000c08, 0x00000c18)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00000c18, 0x00000c18)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00004820, 0x00004830)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00004830, 0x00004830)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00004f70, 0x00004f80)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00004f80, 0x00004f80)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00002abc, 0x00002acc)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00002acc, 0x00002acc)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00006e08, 0x00006e18)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00006e18, 0x00006e18)

kind of stuff in your /var/log/xorg.0.log?

this is extremely annoying when watching movies

---

### Post by fseto on 2007-12-04
Yup!  I haven't check the log before.  What does it means??

SetGrabKeysState - disabled
SetGrabKeysState - enabled
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x00008a18, 0x00008a3c)
(WW) NVIDIA(0): WAIT (0, 7, 0x8000, 0x00008a3c, 0x00008a3c)
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x00008488, 0x000084ac)
(WW) NVIDIA(0): WAIT (0, 7, 0x8000, 0x000084ac, 0x000084ac)
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x0000f970, 0x0000f994)
(WW) NVIDIA(0): WAIT (0, 7, 0x8000, 0x0000f994, 0x0000f994)
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x0000c518, 0x0000c53c)
(WW) NVIDIA(0): WAIT (0, 7, 0x8000, 0x0000c53c, 0x0000c53c)
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x00001914, 0x00001938)
(WW) NVIDIA(0): WAIT (0, 7, 0x8000, 0x00001938, 0x00001938)
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x00006ccc, 0x00006cf0)
(WW) NVIDIA(0): WAIT (0, 7, 0x8000, 0x00006cf0, 0x00006cf0)
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x0000c4ac, 0x0000c4d0)

---

### Post by vivichrist on 2007-12-11
just try installing xserver-xgl and see if that fixes it

---

### Post by fseto on 2007-12-13
> **vivichrist said:**
> just try installing xserver-xgl and see if that fixes it

Did that work for you?  Looks like there's an outstanding bug that halves the frame rate?  [Link]("https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/136650")

Mine is a 6150, so there's not much oophm to start with.

---

### Post by vivichrist on 2008-01-01
ah but have you tried using totem-xine?
remove xserver-xgl and install totem-xine and see how that go's.

---

### Post by fseto on 2008-01-09
Thanks for the suggestions.  But no luck.  The video still stops right in the middle oftentimes.  I have a strong suspicion that it's the nvidia driver or maybe some weird interaction between that and Xorg.  But don't really have much to go on. =/


> **vivichrist said:**
> ah but have you tried using totem-xine?
remove xserver-xgl and install totem-xine and see how that go's.

---

### Post by reets on 2008-01-10
I have this same problem in VLC, video freezes for a few seconds and sound continues. Does it a lot though during a movie :( No other video formats cause this problem for me.

---

### Post by fseto on 2008-01-10
I ran into this thread just yesterday, where they seems to have similar problem and was able to fix it by setting "UseEvents" Options to true in the device section of the xorg.conf.  Seems somewhat promising so far, will know more after watching some movies. =)

[http://www.nvnews.net/vbulletin/showthread.php?t=86253](http://www.nvnews.net/vbulletin/showthread.php?t=86253)

---

### Post by vivichrist on 2008-01-14
I tried this suggestion to no avail. the only thing that had success for me was xserver-xgl but that has other (less annoying) problems.

---

### Post by reets on 2008-01-14
That post didn't fix anything for me either. I did try Mplayer like someone suggested and it was a little better. After playing with some settings I was actually able to get Mplayer to play the movies perfectly. Watched 2 of them so far an both ran very well. Enabling the drop frames option did work but it was jaggy a bit. If I turn that off, enabled double buffering, direct render, turning off Post-Process and maxing out the cache it ran awesome!

Thanks a LOT for all the help :D

---

### Post by fseto on 2008-02-28
the mplayer didn't work for me.... 
But switching over to AIGLX seems to do the trick.  I followed the directions below; it seems to be meant for Edgy, but seems ok with Gusty also.

[https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy)

---

