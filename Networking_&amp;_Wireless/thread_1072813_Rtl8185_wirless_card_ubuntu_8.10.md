---
title: "Rtl8185 wirless card ubuntu 8.10"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by kkilps on 2009-02-17
I need help getting this card to work properly. It show about 10% for signal no matter how far or near to the router I am. I know this is a drover problem and need help installing the driver from here [http://wireless.kernel.org/](http://wireless.kernel.org/) . I have followed the steps and can't get it to work. Ended up reinstalling to get the old drivers back. Now can some one help me please?

---

### Post by haddog on 2009-02-17
kkilps. Try using this site. It explains ndiswrapper, which allows you to use a windows driver. The install was for a different wifi card but just substitute the card you use.

[http://technoemperor.blogspot.com/2008/10/getting-wireless-to-work-in.html](http://technoemperor.blogspot.com/2008/10/getting-wireless-to-work-in.html) 

I have an AirLink101 AWLH3028 pci card that I couldn't get working. I followed these instructions, using the appropriate driver of course and a wired connection. It got my card working.

I'm using 8.04.2 but should work in 8.10. Good luck.

---

### Post by kkilps on 2009-02-18
Didn;t work. The wireless card doesn't show up in ifconfig or iwconfig and doesn't work when I try to use sudo ifconfig wlan0 up.

---

### Post by gnusci on 2009-02-18
Could you please post to output of the following command:

$ uname -a

---

### Post by kkilps on 2009-02-19
This afternoon when I am home I will.

---

### Post by kkilps on 2009-02-19
Linux Ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

---

### Post by brons2 on 2009-02-21
> **kkilps said:**
> Didn;t work. The wireless card doesn't show up in ifconfig or iwconfig and doesn't work when I try to use sudo ifconfig wlan0 up.

it worked for me on an AWLC3028, same rtl8185 chipset in a PCMCIA card.  Install ndisGTK and go into the Windows Wireless Drivers in the administration menu.  Use the Windows 98 driver from the Airlink CD, not the XP one.  I can send it to you if yours doesn't have Win98 drivers.  Let me know.

On a side note, I don't know why they bothered putting the rtl8185 in 8.10 if their implementation was going to suck so bad.  I've had the same problem with my 8185 card when booting from a CD, it recognizes it but the signal strength is krap.  Better to just use ndisGTK.

---

### Post by kkilps on 2009-02-22
> **brons2 said:**
> it worked for me on an AWLC3028, same rtl8185 chipset in a PCMCIA card.  Install ndisGTK and go into the Windows Wireless Drivers in the administration menu.  Use the Windows 98 driver from the Airlink CD, not the XP one.  I can send it to you if yours doesn't have Win98 drivers.  Let me know.

On a side note, I don't know why they bothered putting the rtl8185 in 8.10 if their implementation was going to suck so bad.  I've had the same problem with my 8185 card when booting from a CD, it recognizes it but the signal strength is krap.  Better to just use ndisGTK.

It works! :D My problem was I kept using the XP driver when I would try ndiswrapper. 

I also wonder what they were thinking adding very buggy drivers. :(

---

