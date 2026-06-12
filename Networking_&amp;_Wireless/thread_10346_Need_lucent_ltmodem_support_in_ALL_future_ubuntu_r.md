---
title: "Need lucent ltmodem support in ALL future ubuntu releases"
date: 2005-01-06
forum: Networking &amp; Wireless
---

### Post by JD2 on 2005-01-06
It would save me a lot of time if the lucent ltmodem-2.6.8.1-3-386_8.31a8_i386.deb driver was included in all future ubuntu installs and provide an automatic installation and configuration application for it. Is there a wvdial account gui application setup tool? If so, could you include it in ubuntu CD? Perhaps, rewrite the modemlights to be also an account setup tool? Anything but hand editing config files. I would really love to see ubuntu implement gui config tool for things such as fstab and hdparm. Actually, for every config file ubuntu uses. I don't want to scrounge the internet for these tools, they should be part of the distro.

---

### Post by hardcandy on 2005-01-07
Since you need lucent modem support, why not add all the other modems that other people need as well?  And why stop with modems? How about all the printers, scanners, video cards, usb devices? Give me a break! 
There is only so much space on a cd. 
Besides, you probably learned a lot getting the modem to work, it was a good learning experience.

---

### Post by nocturn on 2005-01-07
[QUOTE=JD2]It would save me a lot of time if the lucent ltmodem-2.6.8.1-3-386_8.31a8_i386.deb driver was included in all future ubuntu installs and provide an automatic installation and configuration application for it. Is there a wvdial account gui application setup tool? If so, could you include it in ubuntu CD? Perhaps, rewrite the modemlights to be also an account setup tool? Anything but hand editing config files. I would really love to see ubuntu implement gui config tool for things such as fstab and hdparm. Actually, for every config file ubuntu uses. I don't want to scrounge the internet for these tools, they should be part of the distro.[/QUOTE]

Things like hdparm are *optional*.   Your system will work with the defaults detected at boot/installtime.  Windows also does this (windows usually uses the lowest common denominator).

If you want/need the best performance you can get out of your hardware, hdparm is there.    Why do you want to edit your fstab after install?  (Ubuntu detects and mounts removable devices without it, so unless you change partitioning...)

On the drivers, I sympathize if this has cost you a lot of time, but it is impossible to include *ALL* drivers on the CD.  No OS does this currently, and won't do this until generic device drivers exist (one driver for all devices of the same class).

---

### Post by az on 2005-01-07
ltmodem-2.6.8.1-3-386_8.31a8_i386.deb is nonfree.  It contains a precompiled binary that is distrubuted without a free licence.

---

### Post by daniels on 2005-01-07
As I understand it, the problem with the ltmodem driver is that it is wholly binary, so if we change our kernel, it will suddenly stop working.  So it won't actually work.  Most drivers have a small wrapper around their binary blobs (nVidia, Atheros), which lets us work across multiple kernel changes.

---

### Post by JD2 on 2005-01-08
Daniels, thanks for reading my post. 

I think this website that has my modem driver provides a source code.

[http://www.heby.de/ltmodem](http://www.heby.de/ltmodem)

The modem driver when uncompressed includes a script that sets things up so that I could dial the modem and connect. But after a reboot I have to invoke the same script again. Maybe this could be handled by ubuntu each time? It would be refreshing to have ubuntu work with my modem out of the box. I think I would cry for joy if this happened. One little bug I found and it has to do with the yellow sticky notes not remembering their size and position on the desktop after a reboot. I can't think of anything more and just goes to show you how good of a job you guys did :)

---

### Post by az on 2005-01-08
"Besides, you probably learned a lot getting the modem to work, it was a good learning experience."

People go to Slackware or debian for that.

"As I understand it, the problem with the ltmodem driver is that it is wholly binary, so if we change our kernel, it will suddenly stop working. So it won't actually work. Most drivers have a small wrapper around their binary blobs (nVidia, Atheros), which lets us work across multiple kernel changes."

It (the ltmodem source) is a precompiled object file distributed with headers and scripts which can be linked with the kernel-headers to make an appropriate kernel module.  Lucent makes the precompiled binary and will not share the source.  

If the kernel changed, the package would be reompiled and the module would be updated like you describe.  Source and precompiled modules could be distributed.

If this package were to be included, it would have to go into restricted.  In debian, it would have to go into non-free.

I got into contact with the maintainer of the package for the [www.heby.de/ltmodem](www.heby.de/ltmodem) website.  I had asked him if he intended to get his package into debian.  He said that he wanted to, but was busy.  This would make it's presence in Ubuntu a fact of life like the sl-modem packages.  I have not spoken with him in a while.  I will try him again.

---

### Post by JD2 on 2005-01-08
azz, if you could make it happen that would be incredible for me and for a lot of other people I'm sure :) Thanks for trying.

---

### Post by daniels on 2005-01-08
I'll try to get it into linux-restricted-modules.

---

### Post by az on 2005-01-09
"I'll try to get it into linux-restricted-modules"

How about the sl-modem modules, too, please?

I would suggest others (like Intel), but they tend to have conflicting pci ids and so putting them toegeth in the same package would be messy...

---

### Post by JD2 on 2005-01-09
Will this also be available on the ubuntu download iso? Because that's where I need it to be the most so right after installing ubuntu I could log onto the internet. Just trying to avoid catch-22 situation.

---

### Post by occy8 on 2005-02-08
Hello,
I am new to linux, played with a few distributions and the biggest problem always was to get these software modems running. I am still using Windows 98 and try to find a replacement.
It is very important for a newbie to connect to the internet because of the support forums. So it would be nice if these drivers could be included, perhaps something else could be left of the CD. Anyway these are only my thoughts. 

Now my question

I understand there is a similar problem if you use a USB ADSL modem?! Is that the case with Ubuntu? Or do they run out of the box?

---

### Post by gfxdude on 2005-02-21
Hey **azz**, great to see some real help here in the forums.

*On the subject of Lucent drivers' relative importance:*
I tried for the longest time to find a **genuine hardware modem** that fitted internally as a PCI card.  Not that long ago you could apparently, but since I started looking it proved impossible.  I even called a local manufacturer of such a modem (it was at that time even advertised among their other products on the company website), only to have them tell me that they no longer made or supported it.  This seems true for the PC modem scene in general now - no internal hardware modems.

**So I reasoned, OK, Linux supports certain Winmodems now -- I'll get one that's well supported.**  After some digging around, it seemed the Lucent chipset was the best-supported in the Linux world (drivers that are current, available and work), and I made a purchase on that basis.

I still believe that's true, and therefore would also like to see better out-of-box support for the Lucent-chipset modems in Ubuntu, if at all possible.

NB, I installed Ubuntu (Warty)  for the first time the other day, and although I now have (after some work) functional drivers,  connection is still painful.  I've had two online sessions but only managed it each time after an hour's messing-around with module scripts, wvdial and pon/poff.  Each time I reboot, /dev/modem is missing again and the connection that had been so great fails to activate. Woe.

I hope Hoary will have  things more together in this area!  Ubuntu is great in every other way, especially Synaptic -- but without a valid connection you'd never really get that far, right? ;)

---

### Post by jllitvay on 2005-03-18
Hello, there are distibutions that suport a lot of softmodems. I dont know if it is legal or not, but here in Brasil is one of the most used linux (semi)distribution, in the linux entry-level.

[http://www.guiadohardware.net/kurumin/index.php#download](http://www.guiadohardware.net/kurumin/index.php#download)

But it is in Brasilian portuguese.  :?

---

### Post by GeneticAlgo on 2005-03-25
[QUOTE=JD2]It would save me a lot of time if the lucent ltmodem-2.6.8.1-3-386_8.31a8_i386.deb driver was included in all future ubuntu installs ... .[/QUOTE]

Where can one download this from? The only link I can find to it is broken.

EDIT: Its OK, I was trying an obviously older version (a9), the a10 link [www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a10_i386.deb](www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a10_i386.deb) seems to work. 

Why doesn't this show up in apt-get? I included the line is sources.list so that I can get the ltmodem packages, but the only 2.6 version I have available is for i686.

---

### Post by az on 2005-03-25
"EDIT: Its OK, I was trying an obviously older version (a9), the a10 link [http://www.vif.com/users/mzajac/ltm....31a10_i386.deb](http://www.vif.com/users/mzajac/ltm....31a10_i386.deb) seems to work.

Why doesn't this show up in apt-get? I included the line is sources.list so that I can get the ltmodem packages, but the only 2.6 version I have available is for i686."

Because it is not a repository,  It is just a file.  Download it and dpkg -i it.

It is working for you?  I beleive that it is hopelessly screwed up.

---

