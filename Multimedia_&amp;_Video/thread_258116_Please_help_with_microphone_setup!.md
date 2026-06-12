---
title: "Please help with microphone setup!"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by Menyus on 2006-09-15
Problem: 
1.) when speaking into mic., I get direct feed back through speakers.
2.) When playing back recorded sound in Sound Recorder, no sound comes through speakers. (I am fairly confident that my sound gets recorded.)

I have tried suggestions for sound problems found in this forum and I also reinstalled alsa but I still have the same problems.

My setup:
- ASUS P5B mobo with built-in SoundMAX ADI AD1988A 8-channel CODEC
- Intel Core2 Duo E6400
- kernel module 2.6.15-26-amd64-generic
- alsa-base driver module 1.0.10-4ubuntu4

I also checked the alsa website for the list of supported devices. The latest AnalogDevices sound devices listed was the AD1985. Does that mean the AD1988A is not supported yet? If that's the case, why would ASUS include the alsa driver (1.0.9) in the Linux driver folder on the CD that came with the mobo?

Any suggestion, advice and/or comments is appreciated.

---

### Post by galileux on 2007-05-19
Hi
I have a similar setup (same Mobo) and a similar problem: but my mic is not working at all.
Could you tell me how to check if the latest ALSA drivers are installed and loaded?
I would appreciate.
Thanks

---

### Post by Lanky Juggler on 2007-05-20
Theres a simple fix for the feedback through your speakers, at least.  Go into your volume control panel (for me its in my gnome panel) and in the Playback tab there should be one or two volume settings for "Mic" or "Internal Mic", just set those at minimum/hit mute.  While you're there, you might want to check out the volume settings for recording and such, just in case.

---

### Post by diverse_izzue on 2007-07-12
That's not really a solution, is it? As I understand it, what comes in through the microphone is not supposed to be routed out again through the speakers. I want it to be fed to the sound chip in case an application wants to record something.

Like this, I have to have my microphone muted all the time in order not to be bothered (i can actually hear myself typing because the microphone is right next to the keyboard), and everytime i want to make a VoIP call i have to manually unmute the microphone. Anyone?

---

### Post by w1ldc412d on 2007-11-24
To mute feedback through speakers when speaking into the mic
  - double/right-click the Volume Applet to open Volume-Ctrl
  - click on Recording Tab
  - Mute the speaker-icon on your sound capture device 

If you're not seeing the Recording tab
  - double/right-click the Volume Applet to open Volume-Ctrl
  - Edit => Preferences
  - select Microphone-Capture (or whatever your device; is Line-2 Capture for me)
  - (you may have to close and re-open Vo-Ctrl Props)

Hope this helps :)

---

