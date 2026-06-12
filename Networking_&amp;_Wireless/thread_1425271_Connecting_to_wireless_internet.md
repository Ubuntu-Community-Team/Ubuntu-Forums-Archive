---
title: "Connecting to wireless internet"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by al's on 2010-03-08
Hi. I just installed Ubuntu on my computer and have been trying to connect to the internet through it. I am using a Linksys wireless card. My computer doesn't seem to recognize it, though. In the menu it says 'devices not ready' under 'Wireless Networks'. I searched in the Synapsis Package Manager for 'linksys' and 'broadcom' and downloaded a few of the packages, but none of it worked. Can anyone help me out?

---

### Post by bkratz on 2010-03-08
> **al's said:**
> Hi. I just installed Ubuntu on my computer and have been trying to connect to the internet through it. I am using a Linksys wireless card. My computer doesn't seem to recognize it, though. In the menu it says 'devices not ready' under 'Wireless Networks'. I searched in the Synapsis Package Manager for 'linksys' and 'broadcom' and downloaded a few of the packages, but none of it worked. Can anyone help me out?

The first thing to do would be to post the output from the terminal Applications>>Accessories>>Terminal for the following command

```
lspci | grep Wireless
```

(that is LSPCI in lowercase W in upper). So that someone familiar with Linksys devices can determine a direction for you to follow.
You can copy/paste the results. If you receive nothing back, try just

lspci

---

### Post by al's on 2010-03-09
07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I typed in lspci | grep Wireless and that's what I got.

---

### Post by mark bower on 2010-03-10
while the assistance of bkratz, coffeecat, chili555 is in valuable in many cases, i still recommend jumping to hardware that just works.  admittedly i am using ndiswrapper and PCI wifi cards for transmission improvements.

the Belkin F5D7050 USB has a high probablility of working and i have posted this many, many times, and if you can purchase it but return it if it does not work you have nothing to lose.  also, you might want to look at 

[www.linuxemporium.co.uk](www.linuxemporium.co.uk)  re guaranteed hardware.

mark

---

### Post by bkratz on 2010-03-10
> **al's said:**
> 07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I typed in lspci | grep Wireless and that's what I got.




Actually you should be able to get it working fairly easily, just see this page for instructions

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

See the section that starts with 

Ubuntu/Debian

About 3/4ths the way down.

---

### Post by al's on 2010-03-10
> **bkratz said:**
> Actually you should be able to get it working fairly easily, just see this page for instructions

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

See the section that starts with 

Ubuntu/Debian

About 3/4ths the way down.

Thanks so much. That website was very helpful. 
For future reference, I downloaded the b43 fwcutter package from the Synaptic Package Manager. used the command:  
"sudo apt-get install b43-fwcutter"  in Terminal. I had to wait before installing the package.

---

### Post by bkratz on 2010-03-10
> **al's said:**
> Thanks so much. That website was very helpful. 
For future reference, I downloaded the b43 fwcutter package from the Synaptic Package Manager. used the command:  
"sudo apt-get install b43-fwcutter"  in Terminal. I had to wait before installing the package.

Be sure to come back and report on your success.

Also, when you are successful be sure to mark the thread [solved] in the thread tools to help others.

---

