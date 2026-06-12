---
title: "Hauppauge WinTV-HVR-950"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by starfleetcaptainrob on 2007-07-23
Okay, I'm totally stumped I bought the Hauppauge WinTV-HVR-950 over the weekend and followed the installation instructions to a T from this site:
[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html")

I still can't get it to work.  I've been trying to get it to work via TVtime, but all I get is a blue screen.  When I input lsusb it shows that it's seeing the card there:

```
Bus 006 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 2040:6513 Hauppauge 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

However I can't seem to get TVtime to use the card.  I've tried MythTv but that doesn't seem to work and I'm more interested in being able to watch TV and work on my computer at the same time (I have a dual monitor set up).  Are there any other TV programs out there that might work better that anyone knows of?  Does anyone have any ideas on what I'm doing wrong?  I can post whatever info that might help, just tell me where to get it from.  (Still a bit of a Linux noob)

Thanks!

---

### Post by dabl on 2007-07-24
I don't know how similar or different your card is from the PVR-150, but here's the basics to get a 150 working:

[http://kubuntuforums.net/forums/index.php?topic=3085164.0](http://kubuntuforums.net/forums/index.php?topic=3085164.0)

Note the fact that, if your 950 uses mpeg2, tvtime will never work with it.


HTH  :)

---

### Post by buntunub on 2007-07-27
I can get tvtime video no problem. Looks nice, actually, but no audio. This seems to be the common issue for most - video but no audio - no matter what is tried. Some claim that sox works but audio is delayed a second or two from the video. My issue with that is that i have only /dev/dsp and dont know how to get anything more than that (/dev/dsp0, 1, 2) so sox wont work here. The driver is em28xx, and some claim that modprobing em2880-dvb causes even more issues (which is what that lunapark6 article recommends to do). This and getting audio to work with luvcview with my webcam (also usb integrated) seems to be a big hurdle for linux right now as support for usb seems to be positivly abysmal. Kudo's to the one or two italien guys that actually do work on reverse engineering drivers for that usb stuff though. :popcorn:

---

### Post by bliffle on 2007-08-01
Best luck I've had was with 'vlc', but only analog, not HDTV.

---

### Post by Zyrshnikashnu on 2007-08-01
> **buntunub said:**
> I can get tvtime video no problem. Looks nice, actually, but no audio. This seems to be the common issue for most - video but no audio - no matter what is tried. Some claim that sox works but audio is delayed a second or two from the video. My issue with that is that i have only /dev/dsp and dont know how to get anything more than that (/dev/dsp0, 1, 2) so sox wont work here.

I face precisely the same issue. Also, I've tried both em28xx and em2880-dvb, but both seem to work precisely the same with tvtime.

---

### Post by CptCrncher87 on 2007-09-06
I've got a similar problem but I've gotten phases where I could get picture, no sound, and the color is all off (people have green skin) this was for both mythtv and tvtime.  I tried messing with it and then got low sound, had to use max volume to get any sound at all, but still didn't have a good picture, now i'm at the point where I have no sound and just static.  The really odd thing is that most of the tv programs i've tried say the composite extension is not available and that is it.  Another oddity is that my comp is picking it up as a 980 but it says on the device it is a 950.  This is one of the ties that still has me using windows mainly, because windows didn't have a problem picking it up, but i would really like to cut that tie and use mainly Ubuntu so anyone have any idea what can be going wrong with this?

---

### Post by winterequinox on 2007-10-11
I tried my HVR-950 on two different computers.  On one it worked fine, on the other
it didn't.  I think I finally figured out why.  One had USB 2.0 ports and the other
USB 1.0.  (Also, one is a 64 bit computer, maybe that helps too.)

Also, I have a pchdtv card, and I'd already gone through a certain amount of
pain with that.  You have to be pretty careful about antennae and their
placement to get things to work.

---

### Post by ZychoFlow on 2007-11-16
Was anyone able to resolve the _**no audio issue**_ I've been having the same problem with it.

Also I have several sound cards 3 to be precise maybe my _/dev/dsp_ setting is wrong.
With _/dev/dsp1_ all I get is static and with _/dev/dsp_ and _/dev/dsp0_ I get nothing.

Also I have usb speakers which also count as a separate sound card.

Is there a way to use something like _alsa:device=hw=3.0_ instead of _/dev/dsp_ here like I do in mplayer?
(Actually I already set it as my default card so I would just have to use _alsa:default_)

---

### Post by cow_racer on 2007-11-18
I have the same problem.  I want to watch HDTV, but tvtime doesn't support atsc signals.  Mythtv doesn't seem to work or too difficult for me to get it right.

---

### Post by Acuos on 2007-12-07
I found this website trying to find a solution.  He offers a link to how to get it to work and a command for getting sound to work.  However, the sound is delayed.  A comment suggest delaying the video to sync with the audio.

[http://www.fsckin.com/2007/11/26/hauppauge-wintv-hvr-950/](http://www.fsckin.com/2007/11/26/hauppauge-wintv-hvr-950/)

---

