---
title: "How to install drivers for a modem, for USB use"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by linux_dream on 2009-12-03
Hi all!
I'm happy, I finally made the step of installing Ubuntu (version 7.04 I think) after more than a year of doubting.  I thought I couldn't get Internet because Ubuntu wasn't recognizing my modem, but I've read that it needs some drivers.
I believe I have the drivers in a CD that came with my modem.  There's a PDF file that explains how to install the drivers, but I must say I'm stuck at the first step.
It says to open Redhat 8.0.  How do I do this?  I don't even think I have it.  
I'm very new to linux and not an expert at all with computers.  
I need help to be able to connect to Internet with Ubuntu.  (I have the dual boot with windows XP where I have Internet).

By the way I've tried to send the PDF file here, but it is 300 kb, exceeding the limit...  
My modem is Huawei SmartAX MT882.

Any help is greatly appreciated!
Thanks!

---

### Post by puppywhacker on 2009-12-03
Version 7.04 is 2.5 years old, lots of things have improved over these years. After a bit of googling I found a LOT of cries for help, but no real solution. Only one link says that upgrading may help.

[http://www.linuxquestions.org/questions/linux-newbie-8/network-config-broadband-xdsl-595810/page2.html](http://www.linuxquestions.org/questions/linux-newbie-8/network-config-broadband-xdsl-595810/page2.html)

Redhat 8.0 is another linux distribution than Ubuntu 9.10, it uses the same building blocks, but a different way to install packages.

---

### Post by coffeecat on 2009-12-03
According to this:

[http://superuser.com/questions/47923/how-to-configure-huawei-smartax-mt882-modem-on-ubuntu](http://superuser.com/questions/47923/how-to-configure-huawei-smartax-mt882-modem-on-ubuntu)

... and a couple of other things that came up on a Google search, that modem should work out of the box with Ubuntu **[SIZE=3]if[/SIZE]** you use a recent release. Version 7.04 is hopelessly out of date, is not longer supported with security updates and won't have the driver for that modem.

Why not download the ISO for the latest release, Karmic Koala ( [Link]("http://www.ubuntu.com/") ),  burn it to CD and run it live? You can test the modem from the live desktop session and, if it works, install Karmic in place of the Feisty Fawn..

---

### Post by linux_dream on 2009-12-03
Thank you so much to both!  I'm confident now, and I'm downloading the latest version, 9.10.
I'll post here as soon as I have the result.

---

### Post by linux_dream on 2009-12-04
I didn't get lucky.  I still have the same problem with the version 9.10.  Any other ideas?

---

### Post by linux6994 on 2009-12-04
I had trouble with the latest fresh installation of Karmic and tried many things to correct my wireless troubles. I ended up loading Linux Mint8 which is Karmic based and wireless works like a charm. Can't hurt to try it, it allowed b43-cutter to actually run with out any shenanigans.

---

### Post by coffeecat on 2009-12-04
> **linux_dream said:**
> I didn't get lucky.  I still have the same problem with the version 9.10.  Any other ideas?

That link I gave suggests using the ethernet port on the modem rather than the USB. Did you try that? Is it correct in saying there are both?

Apart from that I'm sorry but I don't have any other suggestions except this. USB modems are almost always a hassle and, if your budget stretches to it, a proper modem-router is **always** a better option for so many reasons. It doesn't matter what OS you are running and with a built-in firewall and NAT, a modem-router is much better on security grounds alone. Is this something you would consider?

**Edit:** I've just looked on the 'manual' link in the link I gave (the user manual for the Huawei) and it does do NAT, so if you connect to it with an ethernet cable it should just work. Don't bother with the USB port - that's just giving yourself grief.

> **linux6994 said:**
> I had trouble with the latest fresh installation of Karmic and tried many things to correct my wireless troubles. I ended up loading Linux Mint8 which is Karmic based and wireless works like a charm. Can't hurt to try it, it allowed b43-cutter to actually run with out any shenanigans.

Thanks for that - useful to know that Mint 8 includes b43-fwcutter which can't be included in Ubuntu for licensing reasons. But did you accidentally post in the wrong thread? :?

---

### Post by linux_dream on 2009-12-04
Indeed, I just bought an ethernet cable and it works great.  I thank you both so much, I'm very happy with Ubuntu!  In fact I was scared to use the ethernet port since I had a problem with it under Windows XP (blue screen of death appearing each 15 minutes, so the computer couldn't be of any use).
Thank you and long life to Ubuntu!

---

### Post by puppywhacker on 2009-12-04
=) victory! ... to be honest, I didn't think ethernet was an option to you. It would have been my favorite option. USB is just not meant for networking. For anything else it is perfect.

---

### Post by coffeecat on 2009-12-04
Good Heavens! Windows BSOD-ing every 15 minutes because you're using the ethernet port. :-s I wonder if that was a driver issue. You might want to see if there's a later Windows driver for whatever ethernet card you're using.

Whatever - happy Ubuntu-ing! :)

---

