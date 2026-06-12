---
title: "Cannot get NVIDIA drivers to work."
date: 2013-02-08
forum: Multimedia Software
---

### Post by jmoney47 on 2013-02-08
Hi,

I recently had to do a clean install of Ubuntu 12.04 LTS onto my laptop.  After doing so, I tried to install gnome-shell like I had done before, but when I went to it, it showed me gnome-classic.  I found out this is because my video drivers are not installed and working correctly.  However, when I try to install them it doesn't work.  EVER.  I have spent the last five hours trying every single workaround and different approach possible.  NOTHING WORKS.  To make matters worse, if I update everything after a clean install, jockey thinks that I do not have an NVIDIA video card anymore as the drivers that did appear there no longer do so.  I've tried using the file from nvidia.com, but that didn't work because whenever I type "sudo service lightdm stop," it takes me to some black screen where I can do nothing (ctrl + alt + F1 to get to a terminal does nothing).  I am out of ideas.

Can someone please give me a suggestion on something to try next?  I just want to run gnome-shell and eclipse.  That's all I did with it before.  I have no idea why it won't work again.  I believe a laptop that I paid $2100 for should be able to do that.  Any suggestions will be very welcome.

Thank you.

---

### Post by Bucky Ball on 2013-02-08
*Thread moved to **Multimedia & Video**.*

---

### Post by Yellow Pasque on 2013-02-08
What is output of:
```
lspci | grep VGA
```

---

### Post by jmoney47 on 2013-02-08
I get:

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1212 (rev a1)

---

### Post by Yellow Pasque on 2013-02-08
Remove the nvidia driver and then follow these instructions:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by papibe on 2013-02-08
Hi jmoney47.

Your laptop has [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux.

There are laptops that have the ability to select the graphics from the BIOS. Some only allow you to disable the discrete card, but others even let you select either integrated (Intel), discrete (just the Nvidia card, which would be better ), or NVIDIA Optimus.

If there's no option on the BIOS, take a look at this tutorial: [Bumblebee]("https://wiki.ubuntu.com/Bumblebee"). [Here]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work") is additional information.

I hope it helps. Let us know how it goes.
Regards.

---

### Post by jmoney47 on 2013-02-11
> **papibe said:**
> Hi jmoney47.

Your laptop has [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux.

There are laptops that have the ability to select the graphics from the BIOS. Some only allow you to disable the discrete card, but others even let you select either integrated (Intel), discrete (just the Nvidia card, which would be better ), or NVIDIA Optimus.

If there's no option on the BIOS, take a look at this tutorial: [Bumblebee]("https://wiki.ubuntu.com/Bumblebee"). [Here]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work") is additional information.

I hope it helps. Let us know how it goes.
Regards.

Thank you very much.  It worked without any issues!  I wish I knew about this before!

---

