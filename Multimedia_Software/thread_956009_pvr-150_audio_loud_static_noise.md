---
title: "pvr-150 audio loud static noise"
date: 2008-10-22
forum: Multimedia Software
---

### Post by ydumais on 2008-10-22
Hi, I am trying to complete my first MythTv setup on Ubuntu and at a dead end concerning an audio issue.

I am connected like so: [digital cable box] --coax--> [pvr-150]. 

I can control the cable box with LIRC and managed to record sceduled tv shows with MythTv. The video is fine but the audio I get is loud static noise. All the following methods produces the same output:
cat /dev/video0 > tst.mpeg and listening to recording with vlc
mplayer -vo vx -ao alsa -autosync 30 /dev/video0
Mythtv live video

I can listen to downloaded dvix fine with vlc (video and audio) and any mp3s.

Tried "/usr/bin/v4l2-ctl -d /dev/video0 --set-audio-input=0" with no effects.

Since this is Ubuntu 8.04.1, I did not install ivtv myself as it came with the distro.

Some output:

cat /proc/asound/pcm
00-01: Intel ICH - MIC ADC : SiS SI7012 - MIC ADC : capture 1
00-00: Intel ICH : SiS SI7012 : playback 1 : capture 1

lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80aa
	Flags: bus master, medium devsel, latency 32
	Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: f3e00000-f7efffff
	Prefetchable memory behind bridge: cbd00000-ebcfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
	Flags: bus master, medium devsel, latency 0
...

I believe it's a simple setting issues but this problem does not seem to show up much on my googling.

If anyone could help, that would be greatly appreciated. Thanks.

---

### Post by enricor77 on 2010-08-07
Same here. Have you found a solution for it?

---

### Post by ydumais on 2010-08-07
yes and no. I got tired of trying to make it work and installed Windows XP and tried GB-PVR. At first, sound did not work on this setup either (don't remember if same static noise or just no noise, I think it was no noise).

Anyway, I finally managed to make it work using the s-video out from my cable box and s-video in the pvr-150 instead of the analog cable. 

For sound, I used the rca from cable box to mini-stereo in the pvr-150. 

To connect the pc to the tv, I used the s-video out my GPU and the mini-stereo out my sound card to rca in the tv.

Long story short, I did not try this physical wiring with MythTv, but it might solve your issue (and I would like to know if it does :)).

GP-PVR was ok, I though the front end was a bit slugish (can't compare with MythTv has I never used it).

I have no setup ATM since I crapped that Windows XP install with wonky updates. Going back to Ubuntu soon.

Good luck

---

