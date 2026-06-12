---
title: "RT3090 Wirelss driver not in use on boot up"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by G Force on 2010-01-26
I have an MSI600 laptop with the Ralink RT3090 wireless chipset in it.  Ubuntu 9.10 would not recognise this in the base install.  I tried the NDISWrapper approach which seemed to yield no results so have since downloaded and installed Markus Herberling's driver from [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

This works but only if I first Deactivate the driver and then activate it again in the hardware drivers gui.

How do I set the driver so that it always boots activated?

Thanks,

G.

---

### Post by chili555 on 2010-01-26
Please try:```
sudo gedit /etc/modules
```Add a new line:```
rt3090sta
```Proofread, save and close gedit. Does it load correctly upon reboot?

---

### Post by G Force on 2010-01-26
Yep that worked.

I've got to say that I'm really impressed with this forum.  Responses are nearly as quick as Linux itself.

Thanks for your help.

G.

---

### Post by liakos101 on 2010-04-17
Has anyone gotten rt3090 on U 9.10 to go faster than 54Mbps? If so, what is the trick?

---

### Post by pierrevb on 2011-01-25
> **chili555 said:**
> Please try:```
sudo gedit /etc/modules
```Add a new line:```
rt3090sta
```Proofread, save and close gedit. Does it load correctly upon reboot?


This worked for me too! 

thank you!

Pierre

---

### Post by santosh_2809 on 2011-06-27
This works for me too....

Thanks....

Santosh

---

### Post by zubairw on 2011-07-01
Thanks man. worked like a charm

---

### Post by Marcos.Rufino on 2011-07-22
Thank you man!

---

