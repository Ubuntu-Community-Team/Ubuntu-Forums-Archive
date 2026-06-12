---
title: "Thoughts on wireless"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by XxLepriconxX on 2010-02-20
This isn't more of a question as it is an idea, so today my computer went kaput, and i had to reinstall kubuntu. now given the internet wasn't availble and i didn't have a ethernet cable to reinstall it with. so i went into the pool of the boot usb for Kubuntu, and my restricted driver was there. i installed other things inside of the pool there and restarted my computer, finding that it worked for Internet. Is it possible to use Kubuntu's installation pool drivers, to use on a different distribution?

---

### Post by northd_tech on 2010-02-20
While those drivers might work for ubuntu, xubuntu, edubuntu, Ultimate Ubuntu, Linux Mint, etc. (other variants of Ubuntu and even possibly Debian Linux), I would not expect them to work on a Mandriva or SUSE Linux distribution.

Some of the drivers are written somewhat "universal" like my Broadcom wireless' STA driver, and you might be able to compile them on different versions.

Sorry it's such a non-answer, but I tried about 2 dozen different LiveCD versions of Linux before settling on Ultimate Ubuntu 2.3 (based upon Jaunty Jackalope 9.04).  There were pluses and minuses with about all of them, and I needed to use ndiswrapper for wireless with many of them (this was before Broadcom released that STA driver though).

One of my favorite things about ubuntu 9.04 and 9.10 was that it actually came with ndiswrapper pre-installed.  Of course, my wireless just worked "out of the box" with PCLinuxOS, so that was my favorite for a long time about 2 years ago.  For work and since my university had a hand in its development, I'm a little partial to Scientific Linux because it comes with so much great software already on the LiveDVD- that reminds me... I need to see if there is a newer version of that. ;)

edit:  Yep, 5.4- WOOHOO!!

[http://www.scientificlinux.org/](http://www.scientificlinux.org/)

---

### Post by XxLepriconxX on 2010-02-21
> **northd_tech said:**
> While those drivers might work for ubuntu, xubuntu, edubuntu, Ultimate Ubuntu, Linux Mint, etc. (other variants of Ubuntu and even possibly Debian Linux), I would not expect them to work on a Mandriva or SUSE Linux distribution.

Some of the drivers are written somewhat "universal" like my Broadcom wireless' STA driver, and you might be able to compile them on different versions.

Sorry it's such a non-answer, but I tried about 2 dozen different LiveCD versions of Linux before settling on Ultimate Ubuntu 2.3 (based upon Jaunty Jackalope 9.04).  There were pluses and minuses with about all of them, and I needed to use ndiswrapper for wireless with many of them (this was before Broadcom released that STA driver though).

One of my favorite things about ubuntu 9.04 and 9.10 was that it actually came with ndiswrapper pre-installed.  Of course, my wireless just worked "out of the box" with PCLinuxOS, so that was my favorite for a long time about 2 years ago.  For work and since my university had a hand in its development, I'm a little partial to Scientific Linux because it comes with so much great software already on the LiveDVD- that reminds me... I need to see if there is a newer version of that. ;)

edit:  Yep, 5.4- WOOHOO!!

[http://www.scientificlinux.org/](http://www.scientificlinux.org/)





lmao well i wasn't so sure if it would work or not. i gota say best begginer linux would be mint, xD well at least that was the one i started with. came with the wireless driver, bust switching from that to the other dist, through me off so much it was just horrible. There has got to be a better way to set up wireless then to compile it. I'm sure a lot more people would move to linux if there wireless worked correctly. I would turn to knoppix if i didn't have to compile for the wireless. I just can't figure it out. =/ 

All the instructions in the world on how to compile a driver and such and i still can't figure it out. lol


Oh and my wireless driver is the same as yours.

---

### Post by northd_tech on 2010-02-21
> **XxLepriconxX said:**
> 
Oh and my wireless driver is the same as yours.
Well mine is a Broadcom "4328" 4321AG wireless, and that was a breeze using both the Broadcom STA driver under ubuntu 9.xx or ndiswrapper under ubuntu 8.xx.  It is one of the easier ones.

Other Broadcoms aren't necessarily as easy as mine is.

---

### Post by XxLepriconxX on 2010-02-23
> **northd_tech said:**
> Well mine is a Broadcom "4328" 4321AG wireless, and that was a breeze using both the Broadcom STA driver under ubuntu 9.xx or ndiswrapper under ubuntu 8.xx.  It is one of the easier ones.

Other Broadcoms aren't necessarily as easy as mine is.

huh well maybe not, but still gota say so far the same disk for mint 8 gnome, has worked for kubuntu, xubuntu, and mint 8 kde version....i was going to try it out on mandriva, but it came preinstalled on that.

---

### Post by northd_tech on 2010-02-23
So what flavor of Broadcom is yours?

```
lspci | grep BCM
```People keep asking me what the "easy" Linux hardware is... :confused:

---

### Post by XxLepriconxX on 2010-02-23
> **northd_tech said:**
> So what flavor of Broadcom is yours?

```
lspci | grep BCM
```People keep asking me what the "easy" Linux hardware is... :confused:

lmao well mine is
Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

