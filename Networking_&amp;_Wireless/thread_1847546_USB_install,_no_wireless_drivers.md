---
title: "USB install, no wireless drivers"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by macruadhi on 2011-09-21
I have a laptop that currently lacks a hard drive and I am trying to use it with a flash drive only. I try to enable the restricted drivers, it says it's installing then, then it fails.

Are the drivers on the usb install I did, or do I need the .iso to install them?

---

### Post by mikewhatever on 2011-09-21
What you call a USB install is just an ISO image copied to the USB and made bootable. It's not a proper installation, and therefore, installing drivers won't work.

---

### Post by staticd on 2011-09-21
Did you create a start up disk with the start up disk creator tool? If you did, you will get the install ubuntu icon on your desktop. In this case Ubuntu comes bundled with a few restricted drivers (eg broadcom STA etc.) those work out of the box.

To save stuff you will have to make the startup disk persistent with a persistence file

However If you "installed" it to the usb drive on another computer, It may not have the required drivers available to install. try adding the iso file as a repository/ connecting to the net through a wired connection to get the driver.
Alternately, download the driver file manually and install.

What card do you have BTW?(see model no on the laptop sticker)

---

### Post by macruadhi on 2011-09-21
> **staticd said:**
> (Did you create a start up disk with the start up disk creator tool? If you did, you will get the install ubuntu icon on your desktop. In this case Ubuntu comes bundled with a few restricted drivers (eg broadcom STA etc.) those work out of the box.)
Yes I did, and it does.
(To save stuff you will have to make the startup disk persistent with a persistence file)
I tried that, but the ubuntu creator did not give me the option set a persistance.

However If you "installed" it to the usb drive on another computer, It may not have the required drivers available to install. try adding the iso file as a repository/ connecting to the net through a wired connection to get the driver.
Alternately, download the driver file manually and install.

What card do you have BTW?(see model no on the laptop sticker)
The "restricted drivers" dialog lists Broadcom B43 and STA wireless drivers.

---

### Post by wildmanne39 on 2011-09-21
Hi, do you have the usb drive as persistent?

please run these commands and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

