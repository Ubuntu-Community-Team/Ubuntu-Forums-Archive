---
title: "wifi problem"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by xngjn on 2009-09-07
hi. i using netgear WG111v3 and ubuntu9.04
i can connect to internet but when i type iwconfig :
[IMG]http://i1006.photobucket.com/albums/af182/xngjn/2.jpg[/IMG]
and
[IMG]http://i1006.photobucket.com/albums/af182/xngjn/1.jpg[/IMG]
can any1 tel me what happen?
 
*this is my first time use linux.

---

### Post by jward3010 on 2009-09-07
For some reason I can't expand those images. Can you copy and paste the output of those commands, oe even re-upload the images.

---

### Post by xngjn on 2009-09-07
> **jward3010 said:**
> For some reason I can't expand those images. Can you copy and paste the output of those commands, oe even re-upload the images.
 
ok. i hav re-upload those image.

---

### Post by jward3010 on 2009-09-07
1. Firstly, open a terminal and type 
```
ifconfig -a
```
and post what you get.

Thats much better on the images, thanks. It looks like Ubuntu hasn't recognised your wireless device. Stupid question, but try a restart. Are you connected by wired as well by any chance.

Go to "System" menu > "Administration" > "Hardware Drivers" and see if there are any drivers available, maybe even firmware.

Also, open a terminal and type:
```
sudo lspci
```

---

### Post by xngjn on 2009-09-07
[IMG]http://i1006.photobucket.com/albums/af182/xngjn/1-1.jpg[/IMG]
 
 
[IMG]http://i1006.photobucket.com/albums/af182/xngjn/2-1.jpg[/IMG]
 
 
 
[IMG]http://i1006.photobucket.com/albums/af182/xngjn/3.jpg[/IMG]
 
 
[IMG]http://i1006.photobucket.com/albums/af182/xngjn/5.jpg[/IMG]

---

### Post by xngjn on 2009-09-07
> **jward3010 said:**
> 1. Firstly, open a terminal and type 
```
ifconfig -a
```
and post what you get.
 
Thats much better on the images, thanks. It looks like Ubuntu hasn't recognised your wireless device. Stupid question, but try a restart. Are you connected by wired as well by any chance.
 
Go to "System" menu > "Administration" > "Hardware Drivers" and see if there are any drivers available, maybe even firmware.
 
Also, open a terminal and type:
```
sudo lspci
```
 
 
Ubuntu hasn't recognised my wireless device? but i can online.

---

### Post by jward3010 on 2009-09-07
The output of ifconfig suggests that eth0 must be your wireless adapter, it's got an IP address of 192.168.1.5, and nothing else there has any info.

You're within VMWare or some Virtual machine software, yeah? I think it's emulating a wired connection for virtual machine, even though it's wireless on your Vista side. For example, it's called "Ethernet Controller: Adavanced Micro Devices [AMD]..." - they don't even make ethernet products, just CPU's, chipsets...ok and ATi graphics cards now. Basically I'm very sure it's what VMWare is doing. Try Ubuntu on your PC by booting off a LiveCD or LiveUSB, then you'll get genuine wireless.

---

### Post by xngjn on 2009-09-07
> **jward3010 said:**
> The output of ifconfig suggests that eth0 must be your wireless adapter, it's got an IP address of 192.168.1.5, and nothing else there has any info.
 
You're within VMWare or some Virtual machine software, yeah? I think it's emulating a wired connection for virtual machine, even though it's wireless on your Vista side. For example, it's called "Ethernet Controller: Adavanced Micro Devices [AMD]..." - they don't even make ethernet products, just CPU's, chipsets...ok and ATi graphics cards now. Basically I'm very sure it's what VMWare is doing. Try Ubuntu on your PC by booting off a LiveCD or LiveUSB, then you'll get genuine wireless.
 
 
ya. i using vmware. i know wat u talking. i wil try it first. thanks.

---

### Post by jward3010 on 2009-09-09
No problemo.

---

