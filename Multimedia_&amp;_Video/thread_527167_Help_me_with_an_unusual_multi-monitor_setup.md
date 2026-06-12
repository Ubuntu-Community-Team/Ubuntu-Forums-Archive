---
title: "Help me with an unusual multi-monitor setup?"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by porcorosso on 2007-08-16
I have a Dell Precision M70 notebook with an nVidia Quadro FX GO 1400 video card. When I'm out and about, naturally, I just use the built-in screen, a Seiko 1920x1200 14" LCD.

When I'm home I place the notebook in a port replicator, and I prefer to use a Dell 2005fpw external LCD as my primary or only monitor, with the lid on the notebook remaining closed.

I have installed the glx drivers using Envy, and I've got two X screens set up. But I have to leave the notebook lid open and let both screens run in order to use the external monitor with Ubuntu 7.04. (Well, if I turn off the power management setting to turn off the screen, I can close the lid and just use the external monitor. But the notebook screen stays lit, and this thing runs hot enough under Ubuntu without having that LCD running with the lid down.)

I have worked pretty hard at getting this far. The man pages on xorg.conf are understandable, but they don't seem to include enough information to help me cover this last bit of ground in getting this thing the way I want it to work.

I'm posting my xorg.conf file. Can someone please have a look and tell me if there's a way for me to just use the built-in LCD when undocked and the external screen only when docked? I don't want that built-in screen running with the lid closed.

This has something to do with the NULL parameter under metamodes, doesn't it?

Many thanks for any help you can give me!

PS: Oh, and BTW, does that Server Layout section look okay? What's with that screen statement in there? Is that okay? This xorg.conf has been manipulated by the Envy and then by nvidia-settings applet, and I'm a little concerned about some of the changes they made.

SOLUTION: Okay. In my supreme confidence as a 2 week user of Linux I decided to heck with it. I grossly rewrote the xorg.conf file manually in hopes that I could reach some sort of accommodation with this thing. The way it works now is that, when docked, I have to boot the system with the lid open. I hit Fn-F8 to switch to the external screen, and close the lid. Stupid, but better than it was. If someone knows how to let me just boot the system docked with the lid closed and have the external monitor "just work", I would GREATLY appreciate the benefit of your advice.

One thing you have to say for Linux, it's a learning experience! I've attached my new xorg.conf file for comparison.

---

