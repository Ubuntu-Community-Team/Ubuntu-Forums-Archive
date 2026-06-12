---
title: "No Sound from Sound Blaster Live! 24-bit"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by Breaddy3 on 2006-12-10
I did a fresh install of Xubuntu 6.10 (Edgy Eft) about a week ago over Ubuntu 5.10, and everything's been working fine except the sound. When I first installed 6.10, I got the boot-up sound, but haven't had a single sound since, including the boot-ups after that. ](*,)  I know Xubuntu detects my sound card (Sound Blaster Live! 24-bit (CA0106)) because the sound card is listed both in aplay -l and the alsamixer command works. I've tried going through the comprehensive sound guide, the ALSA project, and the forums, but haven't found anything that would help my specific problem. Any ideas?

---

### Post by Breaddy3 on 2006-12-16
If it helps.....the sound was working when I had Ubuntu 5.10, so at the very least, is there anyway to revert the older driver that was used in 5.10?

---

### Post by Alpha1125 on 2006-12-29
I had the same problem.

I reinstalled the alsa, as per the guide, and it works fine.  Sometimes, when I boot up, it causes zero sound to occur again, and another reinstall of alsa does the job.  


I've got a theory that it's flash beta 9, that's causing the sound driver to die, but it's only a theory, that I can't prove.

---

### Post by lhtown on 2007-02-27
Same problem here. I don't know if the boot-up sound worked once or not.

Also, it didn't work in Fiesty herd 4.

I have the Sound Blaster Live on Xubuntu 6.10 fresh install.

---

### Post by RomeReactor on 2007-02-27
Hi. Just a thought, but do you guys have **ld10k1** installed? i had to install it to make my Audigy SE to work. Look for it in Synaptic; you need to enable Universe repositories first. I also had to change the track to control to **Analog Front** in the volume applet on the top panel (in Gnome). Right click on it, select Preferences, make sure the device is **CA0106**, and choose Analog Front as the track to control. I also had to do this for Mplayer to work with the card:

> If you have a SB Live 24-bit and mplayer gives the "Unable to find..." error, do this:

* Go to Preferences -> Audio tab
* Select Alsa and click "Configure Driver"
* Set "Device" and "Mixer" to default
* Write "Analog Front,0" into Mixer Channel.
* Press OK on both windows.

Maybe that could help, but since two of you are using Xubuntu, i wouldn't know where to make the changes.

---

### Post by lhtown on 2007-02-27
I tried installing it, but I'm not sure what it is supposed to do and couldn't figure out what to do with it. After a reboot, still no go.

---

### Post by lhtown on 2007-02-27
OK, I tried the 6.10 Ubuntu live CD (not Xubuntu). Sound works like a charm from the example ogg vorbis file.

I then proceeded to copy all of the alsamixer settings from the live CD setup and then applied the exact same ones to my installed Xubuntu. At first, the sound didn't work on a streaming Winamp feed that was "playing." Then I tried the same Ogg Vorbis file that I used on the live CD. It is a bit choppy, but it works.

At this point, I would REALLY appreciate any ideas or help that anyone might have. 


Just for the record, here are the settings I copied from the live CD Ubuntu setup and used for alsamixer on my Xubuntu install:

```
Master 81 00
Headphone LFE 1 MM
Headphone 1 0
Headphone Center 1 MM
Tone MM
Bass 50
Ttreble 50
3D control MM
3D control Sigmatel - Depth 0
3D control Sigmatel - Rear Depth 0
PCM 81 00
Surround 100
Center 100
LFE 100
Synth 80
Wave 80
Wave Center 0
Wave LFE 0
Wave surround 0
Line MM
Line LiveDrive 0
Line2 LiveDrive 1 0
CD 81 00
Mic MM
Mic Boost MM
Mic Select Mic1
Video MM
Phone MM
IEC958 Coaxial 0
IEC958 LiveDrive 0
IEC958 Optical Raw MM
IEC958 TTL 0
PC Speaker MM
Aux MM
AC97 80
External Amplifier 00
SB Live Analog/Digital Output Jack MM
Sigmatel 4-Speaker Stereo MM
Sigmatel Output Bias MM
Sigmatel Surround MM
Sigmatel Surround Phase Inversion Playback MM
```

---

### Post by lhtown on 2007-02-28
OK, I have it mostly working now. The sound still isn't too good, but it is at least usable.

I should note that I have about a PII 450 processor with about 192 MB of ram.

For one, I turned off the visualizations in gxine. All of that crazy movement does use processor power. That helped significantly which leads me to believe that part of my problem is my slow processor.

Also, I installed libxine1 which made the files I was trying to play actually produce sound.

---

