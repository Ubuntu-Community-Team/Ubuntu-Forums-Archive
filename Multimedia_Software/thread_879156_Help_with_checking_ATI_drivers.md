---
title: "Help with checking ATI drivers"
date: 2008-08-03
forum: Multimedia Software
---

### Post by shufflemoomin on 2008-08-03
Hi,

I'm a Linux Newbie. I have ubuntu installed on a system with a Radeon 8500. I am having graphics issues in that windows are incredibly slow to draw and drag around and some graphics artifacts. I assume I have an incorrect video driver or wrong settings somewhere.

Can someone be so kind as to step a newbie though checking which driver is installed and how to get the correct driver for my 8500 working?

Many thanks in advance

---

### Post by jinksys on 2008-08-03
Go to System->Administration->Hardware Drivers

There you'll be able to install any non-free drivers, such as an ATI driver.

---

### Post by shufflemoomin on 2008-08-03
THanks, I've tried that, it says no proprietary drivers are in use on this system, but doesn't give me an option to add them.

---

### Post by Vorian Grey on 2008-08-03
Try envy, found in Synaptic. It will download and install the correct driver for you.

---

### Post by shufflemoomin on 2008-08-03
Thanks for that. I managed to get (I think) the open source driver which I think won't get me 3D acceleration but at least the system is usable. I'll give envy a try when my patience is renewed if I have to start troubleshooting if it doesn't work again.

Thanks for the suggestion. Wouldn't have known about envy without it.

---

### Post by Melcar on 2008-08-03
The proprietary drivers won't work for that card.  If you still want to mess around with fglrx, use the [older versions]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html"), but beware that they are not as good (or stable) as the newer release.  Your best bet is to just use the open source drivers; they should be loaded automatically and will give you full 2d/3d acceleration.

---

### Post by shufflemoomin on 2008-08-04
I seem to keep coming across advice that the closed drivers won't work on a Radeon 8500, but the ATI support site says that it will. What are the reasons people are against using the drivers with cards ATI say will work? Are there issues it causes with this card?

---

