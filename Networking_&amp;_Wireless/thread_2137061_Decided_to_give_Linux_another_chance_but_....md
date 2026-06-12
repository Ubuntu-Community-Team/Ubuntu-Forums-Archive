---
title: "Decided to give Linux another chance but ..."
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by cardu on 2013-04-19
Hi, 

I don't know where to post this so I decided this to be a good place. You can delete my post if you want. This is my fourth attempt to replace my Windows with Linux. The third one was 3 years ago and the experience was pretty much the same as today. I don't want to discuss old failures now. I want free, secure, stable and fast system. My old laptop is running Ubuntu quite fine, so I decided to put Ubuntu on my top-noch desktop PC. My Windows 7 is quite a pain and I definitely don't want to pay another dime Microsoft for Windows 8. I've installed Ubuntu 12.10 and everything was smooth. BUT I have no internet. I use my PC only for internet stuff. My wireless adapter is TP-LINK WDN-3200. Guess what? No driver. Come on, guys! It is 2013. How hard is to put all drivers in a distro. Anyway, I want to move to Linux and I decided to pay my dues. Followed the instructions here: 

[http://www.ctheroux.com/2012/09/ralink-rt5572-based-wifi-usb-dongle-setup-on-ubuntu-12-04/](http://www.ctheroux.com/2012/09/ralink-rt5572-based-wifi-usb-dongle-setup-on-ubuntu-12-04/)

and here:

[http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2](http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2)

Guess what? Nothing seems to work. I did all the file modifications and when I try to build the driver - it says it cannot find some directory and exits with error. 

Come on, you guys! It is 2013. 99.99% of the user cannot build drivers and configure stuff using terminal. 

How do you expect people to get on Linux OS when nothing seems to work. Now I have to re-install my Windows 7 again ... :((((((((((((((((

See ya in 3 years. Then will be my next try to use Linux.

---

### Post by ahallubuntu on 2013-04-19
> **cardu said:**
> My wireless adapter is TP-LINK WDN-3200. Guess what? No driver. Come on, guys! It is 2013. How hard is to put all drivers in a distro.

The next time you buy a printer and plug it into your Windows computer and nothing happens - what do you do?  Curse Microsoft for not being able to put all the drivers into Windows?

Or like most people, do you look in the printer box for a CD with drivers?  And if there's no CD - or no driver for Windows on the manufacturer's website - ?  Still a Windows problem?  (Of course, manufacturers have to provide Windows drivers for products they wish to sell.)

Why is it that when Windows doesn't have a driver, people blame the manufacturer - but if Linux doesn't have the driver, it must be "Linux's fault" and not the manufacturer's?

By the way, people with different attitudes about this would be appreciative of the immense amount of work that goes into provide this great free software in a Linux operating system and simply take a little time (with some help) to get their hardware working.

And also - when I installed Windows 7 on my Dell laptop, I had to download a bunch of drivers from Dell after installing Windows.  But Ubuntu had all the drivers for everything - including my wireless card - already installed.

---

### Post by Maheriano on 2013-04-19
You're pretty quick to blame Linux without understanding it.
I had a similar problem with an Atheros card in a tablet when I installed Ubuntu to it, it turned out to actually be a Windows problem. Or manufacturer really. They built a hardware lock into the firmware so it would only enable the wireless card after booting into Windows and unlocking it. To test this boot into Linux and run "rfkill list all" and see what it comes back with. It'll tell you what's locked and if it is a hardware or software lock.

---

### Post by Elfy on 2013-04-19
No need to post then really was there.

Closed

---

