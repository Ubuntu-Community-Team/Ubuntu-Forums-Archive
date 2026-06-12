---
title: "Sound on Asus P5RD1-VM / ADI1986A"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by ginkhao on 2006-10-24
Hi all,

I've tried numerous methods to get sound working on my machine and nothing seems to work.  The motherboard is an Asus P5RD1-VM with ADI1986A sound on-board.  

I have been through the 'comprehensive solution guide', sound appears to be detected and loaded OK, the mixers are not muted but no sound comes out.

aplay -l yields:
**** List of PLAYBACK Hardware Devices ****
card 0: M5461 [HDA ULI M5461], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: M5461 [HDA ULI M5461], device 1: AD198x Digital [AD198x Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

The closest driver match is intel8x0, and when I type:
sudo modprobe snd-intel8x0
nothing happens, no errors or any other messages, I can't tell from the (otherwise very well written) guide what if any response there should be, but there is no sound.

Sound is not muted in alsamixer, or the gui mixer on the top taskbar

This particular chip isn't listed at alsa-project so I may be out of luck, but any help is appreciated.

---

### Post by ginkhao on 2006-10-25
edited

---

### Post by ginkhao on 2006-10-25
After numerous hours fiddling I decided to reinstall Ubuntu and try anew.  This time:

1) aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M5461 [HDA ULI M5461], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: M5461 [HDA ULI M5461], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1

Good so far

2)lspci -v
0000:00:1d.0 0403: ALi Corporation High Definition Audio/AC'97 Host Controller
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818f
        Flags: bus master, medium devsel, latency 64, IRQ 233
        Memory at dfff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

Good again

3) The correct driver I believe is snd-hda-intel

4) sudo modprobe snd-hda-intel
nothing returned by the system, but no errors, and no sound.

Next was ALSA Driver Configuration
This failed with a package not found error at:
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

Next I went to the Synaptic Package Manager, added repositories, and then added anything with any relevance to ALSA I could find, which I found meant automatically installing linux-headers which didn't work in the previous step.  Still no sound, but:

Went back to ALSA Driver Congfiguration, and followed all steps without errors, rebooted and was welcomed with the login sound - and - mp3 playback with XMMS!!!

However...my problem is now that any time the volume control is touched - and I mean touched - sound dies completely, when I reboot it comes back (I imagine there's a way to get it restarted without a reboot but I don't know it (Windows background))

Any ideas?

---

### Post by ginkhao on 2006-10-28
I've bought a new soundcard, autodetected fine, so this issue is closed (for me)

---

