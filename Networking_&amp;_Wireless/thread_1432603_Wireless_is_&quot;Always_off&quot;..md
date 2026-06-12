---
title: "Wireless is &quot;Always off&quot;."
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by LosB on 2010-03-17
Hello everyone, this is my first post.  I am very green with Ubuntu and hoping to get to a ripe-old age with it.  

  I have recently installed Ubuntu on a Dell Inspiron 8500 as well as an internal wireless card.  I have downloaded the hardware drivers, which are not proprietary, and I show that I connect to my router as well as other public wireless connections.  The problem is that the bar-service indicators are dim and there is no data transfer.  I open up a web browser and it states: Server not found.  I have viewed my bios and I see that the wireless card is "Always Off" but wireless installed?
   I thank you in advance.

LosB

---

### Post by chili555 on 2010-03-18
> Hello everyone, this is my first post. I am very green with Ubuntu and hoping to get to a ripe-old age with it.Welcome to the party! We have a lot of fun here and we're glad to have you join us.

Does the wireless button light up or flicker? Please open a terminal and do:```
sudo rmmod -f dell-laptop
```Any improvement? If so, we'll need to modify a file for this to be permanent.

---

### Post by LosB on 2010-03-28
To begin, no light on the button.  Tried command, but came back with an ERROR, no such file or directory

---

### Post by chili555 on 2010-03-29
Please open a terminal and post:> lsmod
lspci -nn
iwconfig
rfkill listThanks.

---

