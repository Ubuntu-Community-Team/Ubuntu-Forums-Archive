---
title: "SPDIF please help!"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by sDoky on 2008-02-23
I have a very similar problem as in many cases above. Though I wasn't able to achieve my victory. After few months of looking through several forums I'm really irritated. I have Audigy2 Value connected by composite cable to my amplifier. The sound goes out in PCM ordinarily, although when I try to play a DVD with all advantages of DTS or DolbyDigital there's just nothing. I've tried VLC configuring to SPDIF out, it is mute. Totem gstreamer version makes the same damn thing... please help. I desperate. That's the only thing I really miss from windows... On the other hand ubuntu gutsy is so much cooler and stable and so on... But no SPDIF sound :( Please give any advice, any help will do. Thx a lot.

---

### Post by wikityler on 2008-02-24
First download [this 26Mb AC3 file]("http://www.diatonis.com/downloads/diatonis_ac3_48k_soal.zip") from [diatonis]("http://www.diatonis.com/downloads_dts_ac3.html"). It's just a free AC3 sample that can be used to test stuff.

Unzip the file to a location like /tmp,

Go to the terminal and enter: *mplayer /tmp/diatonis_soal_48k.ac3 -ao alsa:device=spdif -ac hwac3*
This command tells mplayer to use the SPDIF output, but to let AC3 be decoded by external hardware.

What are the results?

---

### Post by sDoky on 2008-02-24
Pure silence... It does not have 5 minutes, does it? It seems such a small file for so long record.

```
sdoky@sdoky-desktop:~$ mplayer /tmp/diatonis_soal_48k.ac3 -ao alsa:device=spdif -ac hwac3
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /tmp/diatonis_soal_48k.ac3.
libavformat file format detected.
==========================================================================
Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
Video: no video
Starting playback...
A: 347.5 (05:47.4) of 347.8 (05:47.7)  0.2% 

Exiting... (End of file)
sdoky@sdoky-desktop:~$ 
```

> **wikityler said:**
> First download [this 26Mb AC3 file]("http://www.diatonis.com/downloads/diatonis_ac3_48k_soal.zip") from [diatonis]("http://www.diatonis.com/downloads_dts_ac3.html"). It's just a free AC3 sample that can be used to test stuff.

Unzip the file to a location like /tmp,

Go to the terminal and enter: *mplayer /tmp/diatonis_soal_48k.ac3 -ao alsa:device=spdif -ac hwac3*
This command tells mplayer to use the SPDIF output, but to let AC3 be decoded by external hardware.

What are the results?

---

### Post by wikityler on 2008-02-24
Sorry. It appears the file size is actualy 18.6Mb. Must be a typo on the diatonis site. Yes it is 5m47.7s of audio.

When you are able to output PCM, what software are you using?

Does your external decoder give any indication that it is recieving any signal? My reciever has LEDs to display what channel configuration it is recieving (2/4/5.1). Does yours have something simmilar?

Although it shouldn't be, lets confirm your IEC958 isn't muted. At the terminal enter
```
alsamixer
```
Now use your left and right arrow keys to highlight the IEC958 column. Confirm that it is set to 00 and not MM. If it is set to MM, then press the *m* key to un mute it. Use Esc to exit, and try to play some ac3.

---

### Post by sDoky on 2008-02-25
Any software does it. KNotify, all music and video players. My receiver writes type of input. Actually it is a Panasonic A/V receiver. It says PCM 41000Hz 16bit. In windows it switches to DTS or Dolby digital (2.0 or 5.1) if an AC3 output is detected and any normal output (ordinary win sounds, winamp - simply all sounds) are disabled - no mixer, which is good and logical. I'd like to do that here on my gutsy gibbon. thanks

EDIT: I have failed to increase the level of IEC958 because it has already been 100% and also NOT muted :(
> **wikityler said:**
> Sorry. It appears the file size is actualy 18.6Mb. Must be a typo on the diatonis site. Yes it is 5m47.7s of audio.

When you are able to output PCM, what software are you using?

Does your external decoder give any indication that it is recieving any signal? My reciever has LEDs to display what channel configuration it is recieving (2/4/5.1). Does yours have something simmilar?

Although it shouldn't be, lets confirm your IEC958 isn't muted. At the terminal enter
```
alsamixer
```
Now use your left and right arrow keys to highlight the IEC958 column. Confirm that it is set to 00 and not MM. If it is set to MM, then press the *m* key to un mute it. Use Esc to exit, and try to play some ac3.

---

### Post by wikityler on 2008-02-25
Well I'm baffeled. I wish someone with more knowledge than me would step in.

---

### Post by sDoky on 2008-02-25
BTW: thanks a lot for your help, even though you weren't able to help me... I'd bet you did your best. Really thanks.

Please, people, help...
> **wikityler said:**
> Well I'm baffeled. I wish someone with more knowledge than me would step in.

---

