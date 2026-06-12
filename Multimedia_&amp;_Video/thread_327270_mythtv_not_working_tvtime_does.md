---
title: "mythtv not working tvtime does"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by dlehman on 2006-12-28
I cannot get my tv tuner card to work with mythtv but it works just fine with tvtime no configuration required at all, but I am looking for a DVR recording application and myth fails to open my card here is my lspic

```
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (dif
ferent version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Co
ntroller 0 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Co
ntroller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Co
ntroller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Co
ntroller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Co
ntroller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridg
e (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (r
ev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB C
ontroller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB C                     ontroller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB C                     ontroller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2                      Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External                      PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (r                     ev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev                      c1)
01:06.0 Multimedia audio controller: Ensoniq 5880 AudioP                     CI (rev 04)
01:0a.0 Multimedia controller: Philips Semiconductors SA                     A7133/SAA7135 Video Broadcast Decoder (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation NV                     34 [GeForce FX 5200] (rev a1)

```
I have searched the forums and google for my card it says the SAA7134 drivers will work they work fine for tvtime, I have come across post that say I need to unload and reload the kernel modules I have done this and it still does not wok 
mythtv-setup will auto detect my card under option 2 capture cards then analog v4l cards but when I goto option 5 channel editor and do a channel scan it says failed to open the card 

this makes no sense to me let me know if you need more info on my configuration 

Thanks in advance to your help

---

### Post by josesanders on 2006-12-28
If it works in TVTime, I think that the card is properly installed.  The problem is probably in the mythtv-setup.  I had the same problem in the past with a similar card, and I fixed it by adjusting some things in the card settings.  If you tell me what your settings are in the MythTV setup, maybe I could give you some more specific advice.

---

### Post by dlehman on 2006-12-28
well I'm not sure what settings you want but here goes

under option 2 capture cards

Card type:  analog v4l capture card
video device: /dev/video0
probed info: elitegroup  ECS TVP3XP FM 1236 Tu [saa7134]
VBI device: /dev/vbi
audio device: /dev/dsp
audio sampling rate limit: none   
do not adjust volume: unchecked 
default input: television 

let me know what other screens to get info from or is all this in a .conf file I can upload

thanks

---

### Post by majoridiot on 2006-12-29
you mention option two and option five in setup, but did you do steps three and four as well?

step two sets up the card, step three sets up the TUNERS on the card and then set four binds 
the channels to the tuners, if i recall.  you need to do at LEAST steps 1-4 to get the card 
working correctly.

for what it's worth, i sometimes get an error on initial set-up if ALL of the steps aren't completed
IN ORDER.  once it's up and working, tweak as you like.  i think it has something to do with 
the initial table configs in mysql or something.

good luck! :D

---

### Post by dlehman on 2006-12-30
Well I thank you for your help I did not realize those steps were required I thought that was for the lineup only but I got a zap2it account and video is working but I have not sound my sound device is set to /dev/dsp I don't know if this is right or not

if I use the play command with some mp3 it says "sox: Can't open output file '/dev/dsp': Device or resource busy
" but if I use the play -d /dev/adsp it will play 

I changed my device in mythtv-setup to /dev/adsp but still no sound 

I also need to figure out what buttons to use on the keyboard because you can't see the mouse I will work on the remote and lirc tomorrow


Thanks for your help

---

### Post by nigel502 on 2007-01-30
Were you able to resolve this? I'm experiencing the same issue

---

### Post by dlehman on 2007-01-30
I was able to get video but I have not got sound, I have not worked on it for a few weeks either. If you get something working let me know.

Thanks

---

