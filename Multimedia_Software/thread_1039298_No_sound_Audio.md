---
title: "No sound Audio"
date: 2009-01-14
forum: Multimedia Software
---

### Post by simon72post on 2009-01-14
Please help 



The problem I'm having is. I Get no sound when playing music in vlc or any other player like Mplayer.

the motherboard is a jetway j7f4 board.

The OS is Ubuntu Linux mythbuntu 8.10 debian version - lenny/sid.

I tested the machine on a live puppy linux cd it all works fine.

So It's definetly a problem in ubuntu.

this is what I have done so far.

I had a look at this web site.
[http://www.seopher.com/articles/how_to_fix_the_no_sound_in_ubuntu_7_10_on_a_laptop_or_notebook](http://www.seopher.com/articles/how_to_fix_the_no_sound_in_ubuntu_7_10_on_a_laptop_or_notebook)

And they said to disable the external amplifier tick box, and it should solve the problem.
But it didn't.

So then I had a look at this web site.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)

And I was able to get these details on my sound card.

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Lspci -v

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 A                      C97 Audio Controller (rev 60)
        Subsystem: Jetway Information Co., Ltd. Device 4765
        Flags: medium devsel, IRQ 22
        I/O ports at ee00 [size=256]
        Capabilities: [c0] Power Management version 2
        Kernel driver in use: VIA 82xx Audio
        Kernel modules: snd-via82xx

But Now I don't know what to do to solve the problem.

Please can someone help.

---

### Post by blaine1984 on 2009-01-14
-edit-
sorry

---

