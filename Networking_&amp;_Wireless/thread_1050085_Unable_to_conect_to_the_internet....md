---
title: "Unable to conect to the internet..."
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Polar Bear64 on 2009-01-25
Hi

I’m a newbie to Ubuntu and the Linux world in general.

The problem I’m having is that I recently installed Ubuntu 8.10 onto my machine and when I’m in Ubuntu I do not see the network.

Here is a quick rundown of what I have:

A Dell Dimension 3000, which has in it:
Dimension 3000 Celeron D processor 330
1024NB DDR333 Dual Channel memory (2x512MB)
Samsung 80GB IDE (7,200RPM) HDD

On the Samsung drive I have Windows XP Home Edition.

For connecting to the Internet via Windows I use Netgear.

The Netgear is made up of WG111T 108Mbps Wireless USB 2.0 adapter, which is loaded with version 1.1. And a 108Mbps Super Wireless ADSL Router DG834GT, which is loaded with version 1.0.

I have recently installed another HDD (80GB Western Digital Caviar 7,200RPM HDD).
On this drive I have installed Ubuntu 8.10.

When I boot up I have the option to go into Windows or Ubuntu, which is great.

When I boot into windows I can access the Internet, the LED flashes on the Netgear USB adapter.

When I boot into Ubuntu I cannot access the Internet, the LED does not flash on the Netgear USB adapter. In the network manager under the wireless tab nothing is listed.

---

### Post by diablo75 on 2009-01-25
[http://kbserver.netgear.com/release_notes/d102626.asp](http://kbserver.netgear.com/release_notes/d102626.asp). You'll want to install athfmwdl.inf and netwg11t.inf with ndiswrapper.  So hook your laptop up to a ethernet connection.  Then open Applications>Add/Remove and search for "ndiswrapper".  Install it, as well as downloading the linked driver above.

After that's installed, you should see a new entry in your System>Administration folder called something like "Windows Wireless Drivers".

That will open up a simple gui that will ask you to browse for an *.inf file.  You just extract the above zip file out to a folder temporarily, add that inf, and that should do the trick.  You can delete the folder once the inf has been added.

---

### Post by Polar Bear64 on 2009-02-01
> **diablo75 said:**
> [http://kbserver.netgear.com/release_notes/d102626.asp](http://kbserver.netgear.com/release_notes/d102626.asp). You'll want to install athfmwdl.inf and netwg11t.inf with ndiswrapper.  So hook your laptop up to a ethernet connection.  Then open Applications>Add/Remove and search for "ndiswrapper".  Install it, as well as downloading the linked driver above.

After that's installed, you should see a new entry in your System>Administration folder called something like "Windows Wireless Drivers".

That will open up a simple gui that will ask you to browse for an *.inf file.  You just extract the above zip file out to a folder temporarily, add that inf, and that should do the trick.  You can delete the folder once the inf has been added.
Hi

Thanks for your reply.

I&#8217;ve done what you said, but get Invalid Driver for both athfmwdl.inf and netwg11t.inf files when I&#8217;ve added them in the Windows Wireless Drivers gui.

Any advice would be much appreciated.

---

