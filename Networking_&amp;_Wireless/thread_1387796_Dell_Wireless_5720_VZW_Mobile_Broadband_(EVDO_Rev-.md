---
title: "Dell Wireless 5720 VZW Mobile Broadband (EVDO Rev-A) MiniCard"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by thecomethuner on 2010-01-22
Hi 

I use a _**Dell Wireless 5720 VZW Mobile Broadband (EVDO Rev-A) MiniCard **_on a Dell 1535. I dont want to install windows and i am not able to make this work on Ubuntu 9.10.

using a USB device for the time being...

are there any command-line tutorials available

---

### Post by bkratz on 2010-01-22
> **thecomethuner said:**
> Hi 

I use a _**Dell Wireless 5720 VZW Mobile Broadband (EVDO Rev-A) MiniCard **_on a Dell 1535. I dont want to install windows and i am not able to make this work on Ubuntu 9.10.

using a USB device for the time being...

are there any command-line tutorials available

First, here is a whole 8 page thread on the Dell 1535, but it doesn't look very useful, it appears that they have changed cards again.
[http://ubuntuforums.org/showthread.php?t=857532&highlight=Dell+1535](http://ubuntuforums.org/showthread.php?t=857532&highlight=Dell+1535)

Ofter Dell uses relabeled Broadcom devices, so we need to how the system sees it.

Go to the terminal (Applications>>Accessories>>Terminal) and type in 
lspci  (that is LSPCI in lowercase) and copy/paste the output back here.

---

### Post by thecomethuner on 2010-01-22
hi,

thanks for the reply

i actually figured out that the wireless card is 

_**Broadcom Corporation BCM4312 802.11b/g (rev 01)**_

or another description on the Dell website is 

_**Dell Wireless 1397, 1510 Half MiniCard**_

i also tried and accessed the "Hardware Driver" option in ubuntu and found out that the system does recognize the card but theres an error that it shows when i try to activate.

"These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware."

and then i try to activate it and a pop-up appears

"SystemError: Failed to lock /var/cache/apt/archives/lock"

sorry for the inconvenience

---

### Post by bkratz on 2010-01-22
> **thecomethuner said:**
> hi,

thanks for the reply

i actually figured out that the wireless card is 

_**Broadcom Corporation BCM4312 802.11b/g (rev 01)**_

or another description on the Dell website is 

_**Dell Wireless 1397, 1510 Half MiniCard**_

i also tried and accessed the "Hardware Driver" option in ubuntu and found out that the system does recognize the card but theres an error that it shows when i try to activate.

"These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware."

and then i try to activate it and a pop-up appears

"SystemError: Failed to lock /var/cache/apt/archives/lock"

sorry for the inconvenience

You did have the wired connection in when you tried the update, didn't you?

Anyway here is a good page for the family of Broadcom devices

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Phoreign Phoenix on 2010-04-30
I'm getting the same exact thing on my Dell Inspiron 1525.  I have the same exact card, using the same build.  I followed the advice on other forums regarding broadcom cards on older builds of ubuntu to no avail.  Will wait for wisdom from others.  Until then, I am tethered to my router like it's 2002.

---

