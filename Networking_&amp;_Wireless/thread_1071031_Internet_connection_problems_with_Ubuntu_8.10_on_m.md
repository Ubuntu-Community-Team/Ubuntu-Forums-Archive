---
title: "Internet connection problems with Ubuntu 8.10 on my inspiron 6400"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by shmax44 on 2009-02-15
Hey all, I'm new to Ubuntu and was quickly becoming a big fan until I ran into some connection problems with 8.10 and I'm not exactly linux savvy yet. I set up a dual-boot system with Vista on my Inspiron 6400, but can't connect to the internet on Ubuntu. I thought it was a wireless issue alone, but even when I plugged into the router, it would tell me it was looking for an IP and then it wouldn't let me connect.

The system has a Dell Wireless 1390 WLAN Mini-Card and Broadcom 440x 10/100 Integrated Controller listed under network adapters if that helps at all.


I saw that there were many others having trouble with the wireless on 8.10 (although I couldn't find a solution to my problem in any existing forums), but not many people who had issues connecting with the hard line. Is this an issue where I have to set up some kind of IP address or a way to recognize my dell hardware? Any ideas what could be going on cause it's really annoying having to boot to vista every time I want to use the internet.

---

### Post by Philo1 on 2009-02-15
I had an Inspiron 6000 w/ a 1390 as well and the driver the for wifi wasn't a part of the iso for 8.04. I never placed 8.10 onto it. However, after I did an install of 8.04, I would then go to system > admin > hardware drivers. I don't recall the exact driver it found when it searched, but it worked like a charm. I would update it hard lined, reboot and then do this while I was still hard lined.

---

### Post by shmax44 on 2009-02-15
Well the hard line issue turned out to be a modem problem and not a ubuntu problem. I'm online now, but the wireless still isn't working. I'm installing some updates on the system now, so maybe one of those will help ubuntu recognise my wireless card. I checked the hardware drivers before and I had an unnamed proprietary driver recognized and enabled, but still nothing working.




> **Philo1 said:**
> I had an Inspiron 6000 w/ a 1390 as well and the driver the for wifi wasn't a part of the iso for 8.04. I never placed 8.10 onto it. However, after I did an install of 8.04, I would then go to system > admin > hardware drivers. I don't recall the exact driver it found when it searched, but it worked like a charm. I would update it hard lined, reboot and then do this while I was still hard lined.

---

### Post by shmax44 on 2009-02-15
Ok, well I've got it finding the wireless cards now but whenever I go to enable them, it takes me to the authenticate window (where I put in my pw) but just freezes the window before I can put my password in. Any ways around this or does anyone have any idea why the window keeps freezing up?

---

### Post by shmax44 on 2009-02-15
> **shmax44 said:**
> Ok, well I've got it finding the wireless cards now but whenever I go to enable them, it takes me to the authenticate window (where I put in my pw) but just freezes the window before I can put my password in. Any ways around this or does anyone have any idea why the window keeps freezing up?

Nevermind... finally got it working.

---

