---
title: "Cant even boot CD daily build or Alpha 3"
date: 2010-08-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ToxicBurn on 2010-08-19
I have tried daily builds over the past 3 days and the Alpha 3 live cd 

all builds i have used were the 

Live-desktop iso

this is the msg i get

FATAL : Error inserting Ramzswap ( / lib/modules/ 2.6.35-15-Generic/Kernel/drivers/swap.ko ):

Unknown symbol in Module or Unknown Parameter

No Init Found

thats it on a black screen 


My hardware is 

[LIST]
[*]GIGABYTE GA-H55M-S2H LGA 1156 Intel H55 HDMI Micro ATX Intel Motherboard
[*]Intel Core i 3 540 cpu
[*]ATI HD 5770 Video
[/LIST]

any help would be great i find it kind of hard to believe we don't have drivers for this hardware in the alpha so i am not sure whats going on.

---

### Post by ToxicBurn on 2010-08-19
sorry looks like Alpha 3 is Broken as it was reported here

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/600782](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/600782)

guess ill have to wait untill beta 1 to get back in testing ](*,)

---

### Post by ranch hand on 2010-08-19
Or try the Alt install ISO;
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

They have a better record for success.

---

### Post by VMC on 2010-08-19
> **ToxicBurn said:**
> sorry looks like Alpha 3 is Broken as it was reported here

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/600782](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/600782)

guess ill have to wait untill beta 1 to get back in testing ](*,)

What's strange regarding the bug report is, at one point they state its with users <512mb and others report the same issue with >2gb. Ive never seen this error and wonder why? I have amd64, but that's also reported. It looks like Colin Watson has a fix for it though.

---

### Post by ToxicBurn on 2010-08-20
im sorry but what fix are you talking about i relly want to get things working and installed

---

### Post by VMC on 2010-08-20
> **ToxicBurn said:**
> im sorry but what fix are you talking about i relly want to get things working and installed

The fix to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/600782/comments/19") that you link to.

---

### Post by ToxicBurn on 2010-08-22
it says This bug was fixed in the package initramfs-tools - 0.98ubuntu2 on 2010-08-20
 
so i guess i need to wait to get a daily build dated after the 20th ?

---

### Post by VeeDubb on 2010-08-22
> **ToxicBurn said:**
> it says This bug was fixed in the package initramfs-tools - 0.98ubuntu2 on 2010-08-20
 
so i guess i need to wait to get a daily build dated after the 20th ?

This wasn't fixed in the daily build for the 21st or the 22nd.  :(

---

