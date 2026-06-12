---
title: "Audio in browser but not music player"
date: 2019-08-07
forum: Multimedia Software
---

### Post by mfox on 2019-08-07
This is actually a carryover from a problem I had two years ago, but was never solved. I am running Ubuntu 19.04. My internal speaker audio works in some applications, but not others. It always works in Firefox (playing youtube videos), but not in Chromium. And it doesn't work in any music player I've tried (tested extensively in rhythmbox. I have external usb speakers, and when plugged into a Sabrent usb audio dongle, I get sound through all these applications. But my internal speakers are better and I would prefer using them. My audio output from inxi (without the external speakers) is as follows:
```
xxx:~$ inxi -AG
Graphics:
  Device-1: AMD driver: amdgpu v: kernel 
  Display: x11 server: X.Org 1.20.4 driver: amdgpu 
  resolution: 3840x2160~60Hz 
  OpenGL: renderer: AMD RADEON R9 M390X (TONGA DRM 3.27.0 5.0.0-23-generic 
  LLVM 8.0.0) 
  v: 4.5 Mesa 19.0.2 
Audio:
  Device-1: Intel 100 Series/C230 Series Family HD Audio 
  driver: snd_hda_intel 
  Device-2: AMD Tonga HDMI Audio [Radeon R9 285/380] driver: snd_hda_intel 
  Sound Server: ALSA v: k5.0.0-23-generic 
```

Interestingly enough, if my external speakers are plugged in, I can sometimes switch to the internal speakers with sound preferences, and rhythmbox will temporarily work (until I turn it off an on), but even then, the external sound dongle has to be plugged in. Note that I have also tried changing settings in gnome alsamixer, to no avail. I have attached the output from the alsamixer command in a terminal, in case it gives someone a clue as to what's wrong.

---

