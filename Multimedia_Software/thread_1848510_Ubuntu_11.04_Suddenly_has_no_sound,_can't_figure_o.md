---
title: "Ubuntu 11.04 Suddenly has no sound, can't figure out why...."
date: 2011-09-22
forum: Multimedia Software
---

### Post by Merlinnair on 2011-09-22
I'm running Ubuntu 11.04, sound has been working but for some reason it's not today. Not sure what I did...

sudo aplay -l:
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
helen@helen-Thinkpad-R60:~$ wget [http://www.alsa-project.porg/alsa-info.sh](http://www.alsa-project.porg/alsa-info.sh) -0 al





lspci -v | less:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio C
ontroller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at ee240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I'm using an IBM Thinkpad...Please help? Also, I'm a rookie Linux user, please explain things thoroughly if there are steps...And no, my computer is not muted.

---

### Post by DaimyoKirby on 2011-09-22
Yeah, my sound will just suddenly stop working as well. I made [a post]("http://ubuntuforums.org/showthread.php?t=1845700") a while ago about my problem, but nobody seems to have an answer.

I thought it might have been that my computer is just a terrible piece of trash, but since someone else is having the (seemingly) same problem, it might actually be Ubuntu 11.04.

I'm on a Pavilion dv6000 and am also running Ubuntu 11.04.

---

