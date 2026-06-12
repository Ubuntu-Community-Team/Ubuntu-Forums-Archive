---
title: "Installing NVIDIA while using Integrated video?"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by eponymous on 2007-04-20
So I've been struggling with my 8800GTS since I switched to Ubuntu about a month ago.

My question is simple I hope:
Can I boot on my integrated video (asus p5 series mobo) and set up the nvidia drivers with the restricted drive manager?

When I tried it I got the same problem I got when trying to accomplish this in the terminal with the nvidia binary drivers: it doesn't see my nvidia card cause the bios is set for integrated video.

Can you force the driver install and then reboot on the nvidia card?

So far the best I've managed was, in Feisty beta, I had it so that I could boot to the recovery mode of my newest kernel, then run telinit 3 and get to the x server. if i let the boot go normally i'd just get black screen, not even an X server fail dialog.

If I try booting on the nvidia card I have no X server in which to run the restricted driver manager, so the only way to install the drivers is to go to recovery mode and do telinit 3 then set them up, which has resulted in a system that can only be booted in the same fashion.

Would it help to boot non-recovery kernel with no X server? a grub option maybe? The 8800 works fine until it tries to boot X server so that might work by using terminal commands to install restricted drivers. I'm totally green at this so any tips would be appreciated.

Oh this is all in Feisty release, by the way, which has been working great except for this.
Thanks in advance and lemme know if I need to explain what i'm doing further.

---

