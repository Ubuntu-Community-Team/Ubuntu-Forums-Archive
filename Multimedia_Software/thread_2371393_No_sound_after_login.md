---
title: "No sound after login"
date: 2017-09-14
forum: Multimedia Software
---

### Post by Loki*PI on 2017-09-14
Hi:  I'm running 16.04 have had no problems with sound.  Now no sound.  When the login screen comes up I get the drums, then after I login no sound.  I worked through the SoundTroubleshootingProcedure, everything appears to be ok.

What's changed - I bought a webcam.  Ubuntu recognized it and it works.  AlSA lists the webcam as a sound driver, it has a mic.  Even with this disconnect and a reboot, there is no sound.  On reboot ALSA does not list the webcam.  

Other thing, I added a hard drive and installed windows 7.  This is not dual boot.  When I need windows I disconnect the Ubuntu drive and connect the windows and visa versa.  (I know, but I've never been able to get dual boot to work on this system, BIOS is too old I think.)

I have updated and reinstalled the drivers.  Uninstalled and reinstalled restricted extras.  

Sound does not work with Windows either, nothing.  

Configuration in OSs appears to be ok.  If you play a CD you can see sound bars moving, but no sound. 

I've checked the hardware repeatedly and found nothing wrong.  Again, I hear the Ubuntu drums at login.

Anyone got any ideas???????   I've been at this for hours. . .

---

### Post by Loki*PI on 2017-09-14
In AlsaMixer - the option Headphone -   I can only set it at 00 or MM.  There is no scale bar as with the other options.   Is that normal?

---

### Post by Loki*PI on 2017-09-15
I worked this out; for those that follow . . .     Installed pavucontrol and under the configuration tab selected  'Analog Stereo Duplex (unplugged)' and sounds came back.  No idea what the unplugged is suppose to indicate, I assumed it would do nothing, put when I selected it the sound came up.  This was 'click and hope it works' problem solving, not what I like.  I still don't understand what the problem was, but I have sound again.

On the Windows side, from what I've been able to find, there is a glitch in the motherboard, known problem, with no fix.  The MB is 10 yrs old.

---

