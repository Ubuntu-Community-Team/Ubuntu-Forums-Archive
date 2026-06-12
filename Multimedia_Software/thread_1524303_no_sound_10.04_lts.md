---
title: "no sound: 10.04 lts"
date: 2010-07-05
forum: Multimedia Software
---

### Post by methodtwo on 2010-07-05
Hi
I just installed fresh.I was using 9.04 before.The sound worked fine before.In sound preferences the soundcard is listed as ICE1712[envy 24] PCI i/o controller.It's an maudio soundcard.I know this is right as the drivers were listed as similar names before, in other distros.The output of lsmod suggests that all the right drivers are loaded.There are also  snd and soundcore drivers.So can i assume alsa installed correctly?.However the output of dmesg does not mention any of these drivers and shows no sign of recognising the soundcard, unless i'm very much mistaken!.
I've tried messing around in sound preferences.I've tried messing around in alsamixer.I've tried different cable-in-socket combinations.Still no sound on any of the apps i've tried since installing(firefox, totem etc).
I really don't know what to do.
Someone fixed their sound problem, on this forum, by doing:
```
$rm ~/.pulse
```
could this work for me?.I don't know if i have any pulse audio apps installed.So this probably won't work right?.Do you think it's worth a try?.What else should i do?
Any help would be great.Thank you for your time
regards

---

### Post by methodtwo on 2010-07-05
Just noticed that the out out of lspci lists the audio controller as:
```
Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
```
I'm sure that the soundcard is maudio.Now i don't know what model of maudio because Ubuntu has got it wrong!.I didn't think anything was wrong, with the name ice 1712, before because the ice1712 driver worked when i compiled alsa into the kernel, when i was using Gentoo.
i'm confused!

---

### Post by Yellow Pasque on 2010-07-06
For a little more info on your card, can we see output of:
```
aplay -l
lshw -C multimedia
```

---

### Post by methodtwo on 2010-07-06
here's the output of aplay -l:
```
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
And here's the output of lshw -C multimedia:
```
  *-multimedia            
       description: Multimedia audio controller
       product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ICE1712 latency=32
       resources: irq:17 ioport:c800(size=32) ioport:c400(size=16) ioport:c000(s

```

---

### Post by lidex on 2010-07-06
You may be hit by this bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442")

---

