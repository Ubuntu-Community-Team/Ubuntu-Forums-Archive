---
title: "Twinview mix up"
date: 2006-01-13
forum: Multimedia &amp; Video
---

### Post by vanhonk on 2006-01-13
I'm not completely sure this is the right place for this post, but here it goes.

I have succesfully set up Kubuntu with twin view. My basic setup is as follows:
[LIST]
[*]I have an NVIDIA 6200A from Chaintech 256M One VGA and One DVI port.
[*]I have two 19" flat panel monitors. One only has a VGA connection and the other has both VGA and DVI[/LIST]The problem is as follows:

When I first set it all up, the vga panel ended up being the default monitor. I wanted the DVI panel to be the default monitor. The solution seemed simple. I removed the VGA panel and re-ran xserver reconfig. I then set up twinview again with the VGA panel as the second monitor. When KDE is running, it still shows the VGA panel as monitor 1. I'm sure that X has it right because When I set the TwinViewOrientation perameter in my xorg.conf file, I have to set it backwards to orient my monitors correctly.

I guess the question would be; how do tell KDE to switch panel1 and panel2?
Thanks

---

### Post by andrewsawyer on 2006-01-14
In xorg.conf (sudo nano /etc/X11/xorg.conf), have you tried changing the Monitor settings:

```
Option          "TwinViewOrientation" "RightOf"
``` to LeftOf and changing the Device section from:

```
Option          "ConnectedMonitor" "CRT, DFP"
``` to DFP,CRT?

This might be worth trying.

---

### Post by mo_x on 2006-01-14
Currently the nvidia driver will always use CRT as the primary display.

---

### Post by el3ktro on 2006-01-28
Is it possible that you're just not knowing that you don't have display-1 and display-2, but display-0 and display-1? According to your description, when the VGA monitor is referenced as display-1, it would be correct!

Remember: Computers always start counting with 0!

Tom

---

### Post by vampyrebytes on 2006-11-12
> **mo_x said:**
> Currently the nvidia driver will always use CRT as the primary display.

This stinks... I use a laptop and I want my built-in flat panel to be my primary display.

I'm testing putting the panels to be on the secondary monitor... I haven't tested this out compleyely yet... What I'm hoping is that this setting will persist between sessions, but intelligently... so that if no CRT is plugged in, it exists on the primary (only) and when I have the CRT plugged in, it will go to the secondary... ie always staying on the flat panel.

((Xubuntu 6.10 on an HP Pavilion zv5000 custom job... everything else running smooth as silk, I think. I choose Xubuntu as an aesthetic preference, not a performance one.))

---

### Post by vampyrebytes on 2006-11-13
no such luck.

If I do not choose the NULL,1280x800 setting before logging out, I cannot see the log in screen at all when the CRT is unplugged. 

Panels stay on "monitor 2" unless explicitly moved. When the laptop's LCD is teh only monitor connected (and the NULL,1280x800 resolution is selected), it becomes "monitor 1", which leaves me with no panels, until I switch them in "Panel Settings"

using Twinview to support two monitors in a laptop, "sometimes-you-have-two,-sometimes-you-have-one" setting is just not worth the hassle.

Windows handles 2 monitors beautifully, it very gracefully switches between modes (LeftOf, RightOf, Clone, etc) for any two of the three monitors I have connected. ((I have the VGA out, the s-video out and the built in LCD)). I can do any of this live, on-the-fly. I have to manually edit my xorg.conf and restart xwindows to do this in Linux.

I love my Xubuntu, but there are just something things taht Windows handles better. and Dual Monitor support is one.

---

### Post by mo_x on 2006-11-16
Recent nvidia drivers have new options for setting the primary display device. Check the readme that comes with the driver. Also the nvidia-setting program has some new options for dual displays.

---

