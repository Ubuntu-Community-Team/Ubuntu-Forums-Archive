---
title: "Connecting to the internet with wpn111."
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by switcha on 2009-06-08
Hi folks,

A big thanks to all those who have helped me over the past couple of months trying to resolve my connectivity issue with the WPN111.

I thought I would share some core information with others who may be new to ubuntu and are attempting to create an initial connection to the internet using a NETGEAR WPN111.

This is by no means officially endorsed or promoted info - its just info I've learnt my from my past experiences.

Ok, here it goes.

I was using ubuntu 9.04.

I did not connect to the net initially - as alot of people's advice tends to assume you have a net connection.

I installed Windows Wireless Drivers from the Ubuntu CD.

I installed the netwpn11.inf 1.5 version b/c I didn't have access to the 2.0 version through the Windows Wireless Drivers software.

An error message came up stating Unable to see if hardware is present - just click ok. 

For me, it appeared in the Currently Installed Windows Drivers list as netwpn11 Hardware present:Yes. Just click close.

Now, assuming you have not tinkered with the original install, you should have gnome network manager installed by default.

Scroll up to its icon on the top right of the screen and click on it. It should detect your wireless networks.

Ok. Here is the poo bum part.

You can connect to your network but you have to disable the network security - for some reason gnome network manager doesn't like wpa, wpa + wpa2 or wpa2 settings for the wpn111.

(I should also mention I'm using a Netgear wireless modem router DG834, I think the number is). Anyway, point in case is, I've tried using all three of the above settings and no success.

If you disable it completely, it does, however connect.

This way you can update your system and d/ld whatever necessary software you may think is appropriate.

Just be aware though if you decide to install something like WICD Network Manager, you must uninstall network manager - which is near impossible to reinstall once its removed - trust me, I know, I tried and dependency issues galore! So my suggestion (as was suggested to me by another fellow ubuntian) is to back up your copy before you remove it, just in case.

Cool. I'll keep you posted with more updates.

In the mean time, peace out.

---

### Post by superprash2003 on 2009-06-08
good job..posting..

---

### Post by aimwin on 2009-06-25
[http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111)

show and still confirm security with WEB 128 bit share
which is good enough.

Definitely it is better than no securiy.

Have you try WEB? 

That solved my problems.

---

### Post by switcha on 2011-02-26
Thanks all. Issue resolved with latest edition.

---

