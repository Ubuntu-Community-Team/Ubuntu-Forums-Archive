---
title: "How can I install wireless drivers in ubuntu?"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by dealrocker on 2009-04-28
Hi all,
  I am a new Ubuntu user and just downloaded ver 8.10. This is my very first Linux OS and I am not good savvy with it. I have a Ralink RT2860 card and downloaded the Linux drivers from their website. Now wondering how do I install wireless drivers in Ubuntu?:confused:
  
  [FONT=Verdana]Please help.[/FONT]

---

### Post by t0mppa on 2009-04-28
That depends on what kind of a package you downloaded. For instance, if it was a .deb file, then you can just double click it to install and if it was binary, ie. a .tar or .tar.gz or something like that, then you have to unpack it and compile it manually (there is usually a README and/or INSTALL file included, which will tell you what to do).

So, if you still need some help, post back with what exactly you downloaded and we'll go from there.

---

### Post by helmut0 on 2009-04-28
Go to System-administration-hardware drivers and click activate..

---

### Post by coffeecat on 2009-04-28
> **dealrocker said:**
> I have a Ralink RT2860 card and downloaded the Linux drivers from their website. Now wondering how do I install wireless drivers in Ubuntu?:confused:
  
  [FONT=Verdana]Please help.[/FONT]

Ralink cards should just work out of the box in Ubuntu 8.10, I believe. Drivers are aready installed. Have you tried connecting to your network?

**Edit:** apologies - I was looking in /lib/firmware in Jaunty. The firmware for the rt2860 card is there, so the driver will be in the kernel. But looking in the 8.10 /lib/firmware, I see that rt2860 firmware is not there. If you don't get on with activating your wireless card in 8.10, you might think of upgrading to 9.04 (or downloading the iso and reinstalling). It looks as though rt2860 will work out of the box in 9.04/Jaunty.

---

