---
title: "Realtek 8111E wired internet problems under 11.10"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by vanaema78 on 2011-10-14
Hey,

I installed today the new ubuntu 11.10 on my new computer featuring Gigabyte plate and AMD chipset.
It has allso got the Realtek 8111E internet chip, which seems to give me some trouble.
Internet works under the Windows 7 and allso under ubuntu with my hspda usb stick.
Ubuntu seems to recognize the internet connection, but I cant connect and it just keeps repeating and failing.

Maybe you can help me out. All help is appreciated.
Thanks.

---

### Post by jogrady on 2011-10-16
Have you found a solution?  I suspect you are using the Realtek r8169 driver.  The solution is to downgrade the r8168 as described here. [http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora](http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora).

The problem I'm having is that driver isn't compatible with the Linux kerenel 3.0 used by ubuntu 11.10 so I can do what this article describes.    Anyone find a work around.

By the way, I suggest you go to the Realtek site and download the latest drivers for your card.  The drivers shipped with my Asus motherboard worked so I didn't think much about it.  Since I was having problems with the linux drivers I decided to upgrade my Window's 7 drivers.  I got a huge boost in performance with the latest Windows 7 drivers.

---

### Post by praseodym on 2011-10-18
See here

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

the "manipulated" file.

---

