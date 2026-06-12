---
title: "Audio issue on Samsung X11 laptop"
date: 2009-03-06
forum: Multimedia Software
---

### Post by ferreat on 2009-03-06
Hello,

I am new to Ubuntu. I just installed the last release, Ubuntu Intrepid 8.10, on my Samsung X11 laptop computer. I have an issue with the audio and I will describe it as follows:
[LIST]
[*]When the headphones are inserted in the headphone jack, audio doesn't stop playing from the in-built speakers, and audio is played in both, speakers and headphones. This issue is experienced using any audio software, internet radio on Mozilla or on-line videos.
[*]When using Skype, It shows a problem with the audio and voice calls cannot be placed.
[/LIST]
The details of the audio card are as follows:

ferreat:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Samsung Electronics Co Ltd Device c026
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d2300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

ferreat:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: AD198x Analog [AD198x Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: AD198x Digital [AD198x Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 6: Si3054 Modem [Si3054 Modem]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

When I browe in the audio configuration on my gnome I see the model is Analog Devices AD1986A.

I've tried to do many things but I still have the problem. I hope anyone can help me.

---

