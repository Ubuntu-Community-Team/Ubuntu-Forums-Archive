---
title: "[SOLVED] HDMI sound via nvidia geforce 8800 gt"
date: 2008-11-01
forum: Multimedia Software
---

### Post by EvilTchnlgy on 2008-11-01
I was about to give up after trying a million things to get sound to work over hdmi with my video card.
In ubuntu 8.10
NOTE: READ THE ****** AT THE END (AFTER STEP 10) AS IT MAY SAVE YOU A HEADACHE
1) Open the Volume Control Panel
2) Click Switches
3) Click Preferences
4) Check off IEC958 and IEC985 DEFAULT PCM
5) Close the preferences panel
6) Check off the newly found checkboxes on the switches panel
7) Close the Volume Control Panel
8) Go to System>Preferences>Sound
9) Go to the devices tab and change the following to 
"HDA ATI SB ALC662 DIGITAL (ALSA)" :
"Sound Events"
"Music and Movies"
"Audio Conferencing" 
10) Set "Default Mixer Track" to "HDA ATI SB (ALSA)" and then chose "Digital" at the bottom of the list below it.
11) Enjoy sound over HDMI =)
******) "HDA ATI SB ALC662 DIGITAL (ALSA)" and "HDA ATI SB (ALSA)" are both part of my onboard video card. Therefore it is very likely your value here will be different, just look for something similar. Try tunning aplay -l and comparing to my results to find your appropriate value. Remember, if your sound is already working via the audio ports but not HDMI then you shouldn't have to change it anything too dissimilar.

This may seem rather simple but I tried every solution I could find on this forum and went to extraordinary lengths and it turned out being something quite simple.

Just in case: here is the result of my aplay -l

root@phenomx4:/home/brendan# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@phenomx4:/home/brendan# 



Running the latest closed-source nvidia drivers

---

### Post by jkeyes0 on 2008-11-02
this worked beautifully on my XPS m1530 laptop. Thanks so much for this solution!

---

### Post by EvilTchnlgy on 2008-11-03
No problem. I really did feel like I tried every possible solution and finally finding the solution was such a relief to me.
I forgot to add that I had to go to System>Preferences>Sound and then go to my devices tab and change sound, music and movies, audio conferencing to "HDA ATI SB ALC662 DIGITAL (ALSA)" which I believe is the SPDIF output of my onboard video card that I run into my video card.
As for "Default Mixer Track", I set that to "HDA ATI SB (ALSA)" and then chose "Digital" at the bottom of the list below it. I left Sound Capture as it was originally for obvious reasons..
It worked before I did this but say I was listening to music, if pidgin made a sound it would switch audio devices on me and was a pain...
I'll add this to the original post in the meantime

---

### Post by Comsci on 2009-06-12
I would like to confirm the above approach for the following system:

- Zotac IONITX-B mainboard   with on-board
- NVidia GeForce 9400M / ALC662 Graphics/HD audio   connected to
- Sony TV KDL-32W4000 via DVI to HDMI cable 
- Ubuntu 9.04 with NVidia driver 185.18.14

Analog sound via TV was working prior to the NVidia driver installation.  But afterwards, there was no more sound on the TV (this was caused by the TV, since the analog connection was still working). Playing around with the volume control finally also corrupted the analog output. :-(

Basically following the proposal above, HDMI sound could be enabled. In particular, the activation of the IEC 958 switches in the volume control panel (HDA NVidia (Alsa mixer)) apparently introduced the NVIDIA HDMI options in the system audio preferences. Actually, "aplay -l" did not list the  third HDMI device before.

Current drawbacks:
- mainboard analog audio output (e.g. for head-phones) is not working (noise)
- HDMI output volume cannot be controlled by the volume control

However, thanks for the tip!

---

### Post by cumulonix on 2010-12-20
I am trying to get HDMI to play with my panasonic TV, with ubuntu 10.10 on my HP laptop. Just connecting the laptop to the TV with a HDMI cable does the following:
-audio - OK
-video - a pink tinge to the video. colors are distorted. Doing this with windows running on the same system works fine for audio and video.

Here are some details with "aplay -l"
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I think my graphics card is ATI Radeon for 64bit AMD (ubuntu 10.10 for 64bit AMD).What should I be tweaking?

---

### Post by gordintoronto on 2010-12-20
Since you don't have a sound problem, I suggest you should start a new thread. Go to Accessories/Terminal and run the command:
lspci
then copy/paste the line which includes the word "vga". Also, have you installed a proprietary video driver? Do you use compiz? (With any video problem, the first thing to try is disabling compiz.)

---

