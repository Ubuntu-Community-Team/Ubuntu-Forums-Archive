---
title: "Wireless USB on fisrt Mythbuntu instal"
date: 2010-05-01
forum: Mythbuntu
---

### Post by K4rn4K on 2010-05-01
Hi all,

I'm new in this World and in Linux World. I have installed the Mythbuntu 10.04 on my HTPC, but I not know how can I use my Zyxel USB Wireless key to connect to my internet. Where can I find the internet settings ?

Thanks

---

### Post by colinnwn on 2010-05-02
The first thing is that in Xubuntu, you apparently need to add the nm-applet (which manages network connections), to your autostarted list. It seems to only get added to autostarted automatically if it recognizes a network interface. Since your wifi USB dongle wasn't recognized, you need to kick it off. If it did get kicked off, you can change settings using the little double computer icon in the top right part of your taskbar. 

But I'd suggest screwing nm-applet and using Wicd instead. You can install Wicd from the package manager. nm-applet is standard on regular Ubuntu, but in my experience nm-applet is a steaming pile of crap that expels excrement into your day at high velocity on regular occasions.

The other issue is Wifi USB on Linux is very finicky. I've had enough trouble getting Broadcom and Atheros wifi micro-PCI cards to work on Ubuntu with the ugly Windows driver kludges. I only use Intel cards now. Wifi USB is even worse. I can't remember anymore but I think Zyxel based USB dongles are one of the PITA brands.  If I had to use a wifi USB dongle on Linux, I'd only use a Zydas brand or repackaged one. They have released drivers that I think are in the kernel, so they pretty much just work, and they are about the only brand to do so. Other brands, you are just trying your luck and patience.

Good luck.

---

### Post by K4rn4K on 2010-05-02
> **colinnwn said:**
> The first thing is that in Xubuntu, you apparently need to add the nm-applet (which manages network connections), to your autostarted list. It seems to only get added to autostarted automatically if it recognizes a network interface. Since your wifi USB dongle wasn't recognized, you need to kick it off. If it did get kicked off, you can change settings using the little double computer icon in the top right part of your taskbar. 

But I'd suggest screwing nm-applet and using Wicd instead. You can install Wicd from the package manager. nm-applet is standard on regular Ubuntu, but in my experience nm-applet is a steaming pile of crap that expels excrement into your day at high velocity on regular occasions.

  Thanks for response, but I need more little bit help because I not understand very well how can I do the various commands like nm-applet. In other forums I saw some people use the ndiswrapper, is it correct for Xubuntu ( Is Mythbuntu based on Xubuntu ? )?

Also, I not see the taskbar on my Mythbuntu, in desktop you can do a right click to access to some menu and stop, there isn't the taskbar

Thanks for all help

---

