---
title: "Wireless card working BCM4306 (rev 03) but unable to connect to router"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by vonstershubby on 2010-05-18
I'm a Linux newbe who knows his way around Windows but am fascinated by Linux so am experimenting with Ubuntu.  Everything works (fast too) but for my wireless card on Ubuntu.  I have spent countless hours looking through the threads on this website but to no avail - nothing works for me.

I have an old Dell Inspiron 1000 that was slow but worked OK with Windows and the PCMCIA wireless card plugged in (so I know that this hardware combination works).  The wireless card has a Broadcom BCM4306 (rev 3) chipset.  I did a fresh install of Ubuntu 10.04 and in theory, Ubuntu should work with the default b43 Ubuntu Broadcom plug and play driver, but it doesn't.  Ethernet works fine.  Therefore, I used the graphical version of ndiswrapper (System>Admin>Windows Wireless Drivers) and installed the bcmwl5.inf Windows driver.  This gives me a green light on the card and it "seems" to be over the first hurdle.

At the command line, "sudo iwlist scan" returns all the wireless networks that are in range (some encrypted, some not) under the device wlan0 with their signal strengths, whether they are encrypted or not and the usual stuff.  Therefore, the card "seems" to be talking to the laptop and the operating system (unless someone tells me otherwise).  However, whenever I try and connect to any of the networks listed, encrypted or not (with a key that I know works), it fails.  

I don't understand what I'm doing wrong - it seems to work all the way up to making a connection but then fails at the final hurdle.  Does anyone have any idea what I need to do to make this wireless card work?

Many thanks in advance.

---

