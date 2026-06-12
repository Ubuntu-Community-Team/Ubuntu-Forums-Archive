---
title: "Please help a poor soul with my SPDIF mythvideo problems"
date: 2008-10-08
forum: Mythbuntu
---

### Post by spartanmythfan on 2008-10-08
I have nforce motherboard with spdif out.  I can play a dvd from the dvd drive and the spdif sends 5.1 to my AV receiver.  I have checked and my aplay -l shows card 0, device 2 as my IEC958.  I rip .iso dvd without ac3 checked in rip options, and video works perfect but no sound.  I rip .iso with ac3 checked and I get messed up video and questionable sound.

I want to use INTERNAL myth dvd player, but only video works at 720p to my tv.  I have tried different audio settings with no luck, alsamixer has unmuted IEC958.  I have tried audio settings like ALSA:spdif, ALSA:default, checked the passthrough settings, yet absolutely no sound when playing dvd in mythvideo.

Is it likely a ripping problem or a audio setting problem, anybody help me as I have read many forums, tried many things, but still no sound.  I really love mythtv and can't wait til this works, just running out of ideas now.

[email]jason.m.brewster@gmail.com[/email]

Please help if you know, I can post information if desired.

JB

---

### Post by jaakan on 2008-10-09
here is what I did

[http://www.mythtv.org/wiki/index.php/ASUS_P5N-D](http://www.mythtv.org/wiki/index.php/ASUS_P5N-D)



Turning on SPDIF

    * at the command line
    * # alsamixer
    * go to the right and hit "M" when your over "iec958" and Hit "esc" 


Fixing SPDIF only plays 2ch issue - Mythbuntu 8.04 x64

    * Here are my settings for mythfrontend General Setup.
          o AUDIO OUTPUT DEVICE = ALSA:default
          o PASSTHROUGH OUTPUT DEVICE = ALSA:iec958:{ AES0 0x02 }
          o MAX AUDIO CHANNELS = stereo
          o UPMIX = passive
          o X=Enable AC3 to SPDIF Passthrough
          o X=Enable DTS to SPDIF Passthrough
          o _=Aggressive Sound Card Buffering
          o _=Use internal Volume Controls 

Fix for bad sound output if outputting at 44.1Khz
there is a setting to change the sample rate to 48Khz from 44.1Khz I forget where that option is.

---

### Post by skaggapa on 2008-10-18
Do you remember where that fix is? I think i have the same problem. Bad sound over spdif.

---

### Post by jk-menifee on 2009-03-09
Successful SPDIF'ing is very sensitive to alsamixer settings. FYI my setup only worked if the iec958-related items in the mixer were set exactly as follows:

- IEC958 set to "00" (not "MM"--use "M" to toggle; the above post and link don't say what state this is supposed to end up in)
- IEC958 Playback AC97-SPSA set to "0"
- IEC958 Playback Source set to PCM

Then I put the mythtv settings exactly as reported above and voila, live tv, recorded tv, DVD's, and ripped DVD's all work.

---

### Post by isalisb on 2009-03-10
> **skaggapa said:**
> Do you remember where that fix is? I think i have the same problem. Bad sound over spdif.

It is in the alsamixer

---

