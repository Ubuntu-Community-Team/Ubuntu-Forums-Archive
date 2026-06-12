---
title: "NVIDIA GeForce GTX 770M Compatability"
date: 2013-09-26
forum: Multimedia Software
---

### Post by JYzeeeJ on 2013-09-26
Hi,

I am looking at buying my first [Linux based Laptop]("http://www.pcspecialist.co.uk/notebooks/VortexIV-15/"). The GFX card that comes with the Laptop is:

**NVIDIA GeForce® GTX 770M - 3.0GB DDR5 Video RAM - DirectX® 11**

I've looked for Linux drivers and they appear to exist [http://www.geforce.co.uk/drivers/results/63660](http://www.geforce.co.uk/drivers/results/63660)

Has anyone had any experience with this and Ubuntu 13.x?

Looking at this post from Temüjin, [http://ubuntuforums.org/showthread.php?t=2176549](http://ubuntuforums.org/showthread.php?t=2176549), it seems I should:

[COLOR=#000000]1. Remove any nvidia drivers you installed[/COLOR]
[COLOR=#000000]2. Make sure your BIOS is set to Optimus mode if it has a switch to select what graphics modes are active[/COLOR]
[COLOR=#000000]3. Make sure that the lspci command shows both cards[/COLOR]
[COLOR=#000000]4. [/COLOR][https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Would like to hear feedback before I buy the laptop.

Thanks

---

### Post by Yellow Pasque on 2013-09-26
Like I said in the other post, here's the driver you'll want to use (nvidia-319) if you're installing Ubuntu 13.04: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by JYzeeeJ on 2013-09-26
Thanks and you mention that it comes pre-packaged with 13.10. Might just go with that from the off.

---

