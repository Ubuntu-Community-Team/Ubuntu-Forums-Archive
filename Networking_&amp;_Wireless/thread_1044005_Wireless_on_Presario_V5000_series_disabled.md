---
title: "Wireless on Presario V5000 series disabled?"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by somavirex on 2009-01-19
I am new to Ubuntu (2 hours to be precise) so please forgive the ignorance in advance. 

Here's what's been done so far:
-I imported the windows wireless driver for my device, and that seems to be installed properly. 
-When I check the status of the internet adapters, both say DISABLED. (However, the wired connection works when plugged in.)
-I've checked to see if the device is Blacklisted, it is not. 
-The wireless IS enabled in Windows. 

The adapter is a Broadcom 802.11b/g using bcm43xx.inf for the driver. 

How do I enable the device in Ubuntu? (The built-in Help file is useless here.)

Also, I'm using the 64-bit version of Ubuntu.

Thanks so much!!
~jaime

---

### Post by Ayuthia on 2009-01-19
You might first try plugging in your wired connection and go into System->Administration->Hardware Drivers and select the Broadcom option.  If you have the b43 option, it might ask you to have it fetch the firmware for you.  Say yes if you are connected to the internet.  You will then need to restart and hopefully, it should work.

If you have the Broadcom STA option, you should only have to enable that option and it should work.

Hope that helps.

---

### Post by damatrix on 2009-05-24
Im guessing this fixed it?

---

