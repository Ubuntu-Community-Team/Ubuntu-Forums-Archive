---
title: "Diamond Xtreme 5.1 Problems"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by raashell on 2008-03-01
Anybody that can help, I'd really appreciate it.  I'm on my second sound card now, a Diamond Xtreme 5.1, trying to get surround sound out of it (first was Creative Labs Audigy SE, and I couldn't get it to support sound from multiple apps).  I know that the surround sound can work, because when I run:

aplay -Dsurround51 foo.wav

I clearly hear each of my speakers playing the test.  My problem is getting audio for my center and bass speakers anywhere else.  I'm running Fiesty Fawn under both Gnome and Xfce.   I tried uninstalling and re-installing alsa and I think (I've been working on this for awhile) that, that got the sound working out of my front and rear speakers.

The other thing worth noting is that, I haven't found any sound settings in my Bios to turn off.  The only thing that might have something to do with it, that I can see, is a plug and play setting that is enabled.

Here is lscpi -v

00:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at b000 [size=256]
        Capabilities: [c0] Power Management version 2

here is aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Here are some screenshots of Alsamixer:

[IMG]http://www.oneuglyduck.com/alsa1.gif[/IMG]

[IMG]http://www.oneuglyduck.com/alsa2.gif[/IMG]


Once again,  I would be very grateful for any help.

Thanks,

John

---

### Post by raashell on 2008-03-02
Bump.

---

