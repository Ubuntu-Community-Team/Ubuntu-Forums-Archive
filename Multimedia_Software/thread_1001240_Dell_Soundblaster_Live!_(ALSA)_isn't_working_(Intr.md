---
title: "Dell Soundblaster Live! (ALSA) isn't working (Intrepid Ibex)"
date: 2008-12-03
forum: Multimedia Software
---

### Post by amckenny on 2008-12-03
When I was on Hardy my sound would work on about 1 out of every 4 reboots, so I would just reboot over and over again until I heard the Ubuntu bongos on the login page which meant that sound would work for that session. However, since I upgraded to Intrepid, I haven't been able to get it to work at all.

I went through the soundcard troubleshooting sticky and came up with the following results:

**<<<From "aplay -l>>>**
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**<<<From "lspci -v">>>**
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at cda0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1X
	Kernel modules: snd-emu10k1x

02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64
	I/O ports at cd98 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp


**<<<From "sudo modprobe snd-emu10k1x">>>**
[sudo] password for amckenny:
(I type my password, hit enter and am returned to the terminal prompt)


The volume is up, the mute is off, when I go into System>Preferences>Sound, and click test I hear nothing (Device is set to Dell Sound Blaster Live! (Alsa mixer))

Anyone have any ideas what may be going on?

---

### Post by psyke83 on 2008-12-03
You're approaching the issue from the wrong angle - Intrepid uses PulseAudio by default. The System/Preferences/Sound application only controls GStreamer applications (e.g. Totem, Rhythmbox), and since the release of Intrepid, ALSA output will transparently remap audio to PulseAudio (using the PulseAudio ALSA plugins).

Configure PulseAudio correctly. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by amckenny on 2008-12-04
> **psyke83 said:**
> You're approaching the issue from the wrong angle - Intrepid uses PulseAudio by default. The System/Preferences/Sound application only controls GStreamer applications (e.g. Totem, Rhythmbox), and since the release of Intrepid, ALSA output will transparently remap audio to PulseAudio (using the PulseAudio ALSA plugins).

Configure PulseAudio correctly. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
Hi psyke83

I went through the forum post you listed and think that probably got me 95% there, but totem is still having issues playing sound (in audio or video files).

After going through the post I now have sound in several applications (Amarok, MPlayer, etc). However, I do not have sound in Totem. I tried reinstalling Totem, but that didn't work. I also looked at the audio tab in preferences and didn't see anything there that worked.

Thanks for getting me this far! Any thoughts on the rest?

---

### Post by amckenny on 2008-12-06
Consequently, the sound doesn't work in Firefox either. Does anyone have any ideas? I'm pretty new to Linux so I don't know what to try.

Where sound works:
MPlayer
Amarok
Test buttons in System>Preferences>Sound

Where sound doesn't work:
Firefox (Youtube)
Totem
Bongos that normally sound when you boot up to the login screen

---

### Post by schmidtbag on 2008-12-06
This is weird, I think I have the same integrated sound and soundblaster as you.  I'm not sure how many soundblaster live!s dell made modifications to but i'm guessing theres only 1.  i'm running intrepid and my card works fine right now but i made it so it was the least hassle was turning off the integrated audio in bios.  when my integrated audio was on, i didn't hear the bongos either (or any system sounds) but my sound was still working perfectly fine.  when i turned off the integrated audio, some system sounds worked and basically anything with a high cpu usage would make the sound quality fairly poor.  so, i uninstalled pulseaudio and EVERYTHING sounds crisp clear and performance seems to have increased.  i really hate pulse, it makes things so difficult

---

### Post by amckenny on 2008-12-20
Hey I'm back from out of town... I tried what you said about turning off the other card in the bios and that seemed to work. Funny that was the problem in Ibex and not in Heron. Anyway, Thanks for your help!

---

