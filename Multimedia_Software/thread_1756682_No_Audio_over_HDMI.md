---
title: "No Audio over HDMI"
date: 2011-05-12
forum: Multimedia Software
---

### Post by Sctmon on 2011-05-12
I have been trying for a while now to get the audio over HDMI working from my PNY G210 graphics card and mythtv but with no luck.

I have followed this guide [http://wiki.xbmc.org/?title=HOW-TO_s..._Begin.2FNotes](http://wiki.xbmc.org/?title=HOW-TO_s..._Begin.2FNotes)

prior to following this I only had my motherboards on board audio showing up but I am now at the stage that I can see the HDMI audio and select it and un mute it but still cannot get any sound out of it.

As a side effect after following the steps from the link above, now every time I boot the computer up my on board audio is muted so I need to un mute it from sound preferences. Any ideas on how I can fix this?


This is my audio config as it stands:
scott@MythtvFrontend:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 7: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 8: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 9: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0

and this is the options I added into /etc/modprobe.d/sound.conf
enable_msi=0 probe_mask=0xffff,0xfff2

The mother board is a an ASUS MN32-SLI deluxe and I have 2 graphics cards in it, a 9600GT to run the 2 monitors connected and a G210 which I would like to use to connect to my TV using the HDMI output. At the moment I am using the VGA output from the G210 to the TV and a separate audio out from the computer which was working fine but the audio is now always muted on startup.

I don't think it is an issue with my mythtv settings as I cannot get any audio over the HDMI using speaker-test (on board analogue audio works ok).

Any suggestions?

---

### Post by Sctmon on 2011-05-14
I have made a bit of progress on this. I have solved the problem with the audio being muted at startup but still cannot get mythtv audio to work over HDMI.

I have been able make audio work over HDMI using
aplay -Dplughw:1,8 test.wav

but that is as far as I have gotten. I have tried scanning for audio devices in mythTV and selecting the HDMI device (as well as all the other options) but nothing.

---

### Post by lidex on 2011-05-14
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

---

### Post by Sctmon on 2011-05-15
Thank, got it working but lost my analogue audio out from the on board card in the process.

---

### Post by lidex on 2011-05-15
> **Sctmon said:**
> Thank, got it working but lost my analogue audio out from the on board card in the process.

Try using pulse audio preferences to enable simultaneous output.

---

### Post by Sctmon on 2011-05-16
Hi,
After following the steps in the link the only playback device listed is as follows


scott@MythtvFrontend:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

I would like to be able to get my on board analogue audio back but it is not the end of the world.
I am building a small dedicated myth fronted with an micro itx Intel atom / nvidia ion board that I will bolt to the back of the tv and then reclaim my other pc.
Any suggestions welcome though. I am fairly new to this and struggling to understand how Linux handles audio hardware.

---

### Post by lidex on 2011-05-16
This thread I think discusses that issue. Try to muck your way through it:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

