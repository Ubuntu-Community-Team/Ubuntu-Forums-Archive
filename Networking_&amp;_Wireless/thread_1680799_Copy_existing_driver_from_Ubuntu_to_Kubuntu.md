---
title: "Copy existing driver from Ubuntu to Kubuntu"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by tmcox on 2011-02-03
Hi All,
I have ubuntu installed on my laptop which works fine. It has a pcmcia wifi card. When I tried to run the kubuntu live cd it couldn't find the card. As the drivers will be the same how do I find the drivers to allow me to use kubuntu?
I plan to make a live usb which I'll add the drivers to so that it'll work each time I plug in. Alternatively if I can find the drivers then I'll just enable them each time via the cd.
Thanks
Tom

---

### Post by ronnielsen1 on 2011-02-03
Knowing what your pcmia card is would help

---

### Post by tmcox on 2011-02-03
Yeah, unfortunately I'm at work at the moment and the laptop is at home. I was hoping the drivers would be in a certain location or found by a certain method irrespective of what the actual driver was.

---

### Post by ronnielsen1 on 2011-02-03
This is from an old post but still kind of relevant. It's a lot better just to list what pcmcia card you have and search from there.
> All the drivers are built into the kernel, With dapper came a upgraded  kerenel which probbaly includes your drivers when the old beezy kernel  didnt.

Run this command and find out what driver your wifi is using, If it is a usb card look at the "usbcore" line

lsmod

That is the name of the dirver, then run 

locate *name*

and you will see where the file is. It is usually something like /src/kernelxx/drivers/net/wireless

You can try and save the driver files, but they wont work with any other  kernel versions so say you have kernel 2.6.15-26-k7 on dapper now and  you install say fedora at kernel 2.6.15-25-k7 then then dapper files  wont work, But if you find a distro with the same kernel you have now  they should already be included,

---

### Post by tmcox on 2011-02-07
Hi,
My card is a USRobotics USR5412 pcmcia card. As far as I can tell this doesn't work straight out of the box - the laptop was given to me working so I don't know what was done to get it to work.
My kernel is 2.6.35-25-generic.
According to 'additional drivers' my laptop has the 'broadcom sta proprietary wireless driver' installed and in use. When I tried to install that on the Live USB Kubuntu it got right to the end and then failed.

---

### Post by tmcox on 2011-02-07
I found the chipset inside the card is a Broadcom 4321 type so I tried installing the additional drivers following the method [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") for the STA no internet usb version. I installed the first 3 packages manually but the fourth (/pool/restricted/b/bcmwl) errored. I tried it from the terminal window and it errored again. As such it wouldn't let me activate the driver.
Any ideas?

---

