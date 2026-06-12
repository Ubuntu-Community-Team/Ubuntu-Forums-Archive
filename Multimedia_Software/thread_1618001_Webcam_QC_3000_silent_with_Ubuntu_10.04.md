---
title: "Webcam QC 3000 silent with Ubuntu 10.04"
date: 2010-11-10
forum: Multimedia Software
---

### Post by yetilab on 2010-11-10
Hi there,

my Logitech "QC 3000 for business" (046d:09a5) is working fine on Debian (Lenny) and OpenSuse 11.1 and  11.3. With Ubuntu 10.04 it delivers video - no problem - but no audio signals. Here are my first steps to identify the problem:

[LIST]
[*](uninstall Pulseaudio,) ALSA recognizes the device. [FONT=Fixedsys]arecord -l [/FONT]shows:
[/LIST]
[INDENT]```

card 1: U0x46d0x9a5 [USB Device 0x46d:0x9a5], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```[/INDENT]
[LIST]
[*]Select the correct input with [FONT=Fixedsys]amixer[/FONT] / [FONT=Fixedsys]alsamixer[/FONT],  unmute and set recording level to 100%
[*]Test recording with [FONT=Fixedsys]audacity[/FONT] and [FONT=Fixedsys]ameter[/FONT]: No signal.
[*]Test the same system with a (borrowed) Logitech "C 300" (046d:0805) : everything works fine out of the box.
[/LIST]
I would appreciate any help to identify the cause of the problem and to solve it.

Thanks
Ulf

---

### Post by yetilab on 2010-12-03
It was a matter of v4l. after downloading and installing the current driver, everything runs fine.

---

