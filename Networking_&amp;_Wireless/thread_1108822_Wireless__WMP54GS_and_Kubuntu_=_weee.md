---
title: "Wireless  WMP54GS and Kubuntu = weee"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by elb0w on 2009-03-28
I may not be the most experienced linux user but I usally find my way. I have been using linux at work and enjoyed it very much I decided to install it at home. I had no idea that wireless was so hard to get to work. 

I've loaded the windows driver using ndiswrapper , I can see wlan0 showing the adapter yet I cannot connect or even see my router. Im so lost. I dont know if it is because its the new kubuntu beta or my error, but im probably reinstalling windows xp unless someone tosses me a hail mary.

The card is linksys wmp54gs on the newest kubuntu

---

### Post by kerschi on 2010-05-23
Had the same difficulty with Kubuntu. Then I switched to Ubuntu 10.04 and did the following.

Hardware:
Linksys WMP54GS, Broadcom Chipset BCM4306

Needed:
Live CD Ubuntu 10.04
Wired internet connection

What to do:
Clean install Ubuntu 10.4 from Live CD (I had to do it twice, before the install was right)
connect wired network cable to you have internet access

After the install is complete, Ubuntu detects new hardware and installed the required driver (b43)

I ran the Update Manager to get everything up to speed and my wireless was working.

Also check the Ubuntu Wireless Troubleshooting page [https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html)

Good luck!

---

