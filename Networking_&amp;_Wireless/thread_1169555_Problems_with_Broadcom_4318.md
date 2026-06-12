---
title: "Problems with Broadcom 4318"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by notamuppet on 2009-05-25
I've been trying to get my broadcom 4318 card to work by reading how-to's and even the thread in this forum on trying to get a 4328 to work.  I'm running into errors left and right, though, and need help.

When I enter "lspci | grep Bro" , I get 
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I tried the command "sudo apt-get install ndiswrapper-utils-1.9" to install ndiswrapper but I get this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

---

### Post by gibbylinks on 2009-05-25
Have you tried using synaptic ?

Also try FWcutter. I was using nsdiswrapper with my Broadcom 4318 and it was very flaky. I've ditched it now and using the device driver and had no problems.
:D

---

### Post by notamuppet on 2009-05-25
How do I use FWcutter?

---

### Post by t0mppa on 2009-05-25
[Here's]("http://linuxwireless.org/en/users/Drivers/b43") a nice tutorial on how to set it up.

---

### Post by notamuppet on 2009-05-27
I tried that tutorial but when I run "[B]sudo apt-get install b43-fwcutter"

I get "E: Couldn't find package b43-fwcutter"

[/B]

---

### Post by Ayuthia on 2009-05-27
You will need a working internet connection inside of Ubuntu and then you can try:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

---

