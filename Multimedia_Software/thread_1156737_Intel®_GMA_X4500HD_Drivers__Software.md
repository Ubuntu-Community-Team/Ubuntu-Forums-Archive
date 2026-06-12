---
title: "Intel® GMA X4500HD Drivers / Software?"
date: 2009-05-12
forum: Multimedia Software
---

### Post by 4dplane on 2009-05-12
Hi,

I have been using nvidia cards for awhile now on Linux. First I would set the drive active and then there would be the "NVIDIA X Server Settings" - ok.

So where is all this for the intel video cards? How do I know i running the correct driver and how do Interface with the cards settings? 

For one, I do not have output via the DVI port, I only have output via the HDMI port.

Thanks,
4dplane

---

### Post by psyke83 on 2009-05-12
> **4dplane said:**
> Hi,

I have been using nvidia cards for awhile now on Linux. First I would set the drive active and then there would be the "NVIDIA X Server Settings" - ok.

So where is all this for the intel video cards? How do I know i running the corrert driver and how do Interface with the cards settings? 

For one, I do not have output via the DVI port, I only have output via the HDMI port.

Thanks,
4dplane

There are no specialized GUI configuration utilities for the Intel drivers similar to nvidia-settings - the Intel drivers are open source and included in the Xorg framework, so you don't need to do anything special to install them.

For details on how the driver functions, refer to "man intel". It explains how to get different outputs working, etc.

Also check System -> Preferences -> Display.

---

### Post by 4dplane on 2009-05-12
Thanks psyke83, that helps alot!

---

### Post by eyeshield30 on 2010-04-24
hello, is anybody know where to download this driver?
i'm just finishing installed ubuntu on my laptop thanks ^^

---

### Post by BELLION on 2011-04-25
Actually you dont need to find this driver because it is enough for you to load X.org driver from synaptic packet manager. But you will have a problem about the brightness of the screen so my solution is to set the brightness during the selection of GRUB screen by using the FN + brightness controll buttons so Ubuntu 10.10 wont change the brightness you set during the GRUB after you log in.

---

