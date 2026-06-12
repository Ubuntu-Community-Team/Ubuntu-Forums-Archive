---
title: "GC-WB150 - WiFi works, bluetooth does not - Ubuntu 12.04"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by Quepali on 2013-01-06
[http://www.gigabyte.com/products/product-page.aspx?pid=4134&dl=1#ov](http://www.gigabyte.com/products/product-page.aspx?pid=4134&dl=1#ov)

The card followed in the package with the motherboard, so I know they're a match. No problems with the WiFi, but bluetooth can't find any devices, and devices can't find the the device the card is installed on.

I can enable and disable bluetooth in Ubuntu, but it just can't find any devices. (The devices I try to connect to is found by my other computer.)

I've tried numerous serches on Google, but no matching results.

I hope there is someone out there with more experience with this than me out there, because I am sort of stuck.

---

### Post by Muratturat on 2013-01-06
with the bluetooth devices many problems have been found in ubuntu 12.04

Easiest way is just to upgrade to Ubuntu 12.10.

check bluetooth with "sudo service bluetooth status" command.
What it say? running/start or disabled?

Then try blueman, it should help.
```
sudo apt-get update
```
```
sudo apt-get install blueman
```

---

### Post by Quepali on 2013-01-06
The light on back on the card, that indicates if the bluetooth is activated or not is off even if bluetooth is enabled og disabled in the software.
The WiFi acts as it sould be. The light is on if WiFi is enabled, and off if it is disabled.

The status says start/running. So I guess that part is as it sould be.

Ran the two codes. Tested. Restarted the computer. 
I still have the same problem.

---

