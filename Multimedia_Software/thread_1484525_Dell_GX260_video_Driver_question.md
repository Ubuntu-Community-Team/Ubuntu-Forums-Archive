---
title: "Dell GX260 video Driver question"
date: 2010-05-15
forum: Multimedia Software
---

### Post by elgthg on 2010-05-15
I first installed ubumtu 6.06 in 2006 on  a spare computer in my home for the purpose of becoming familiar with it over time so that I can eventually eliminate most or all of the MS-based computers in my home. So I have only been a casual user.
I installed it on a Dell Optiplex GX260 desktop computer.
It was very stable. I would often leave it running for 3 weeks at a time without rebooting. Over the years I have upgraded from time to time. I began experiencing some problems that I believe are related to the video drivers around the time of one of the releases  in 2008.  Just last week I upgraded to 10.4 and the problem is now worse than ever.  It has actualy  manifested itself with different symptoms with different releases, but currently if I leave the computer running for a while, sometimes 5 minutes, sometimes 30 minutes, unexpectedly the screen goes black and about every 5 seconds vertical white bands flash on the top half of the monitor. The only way I can recover is to either hold down ctl alt del or power it off. I have read the video help page where I learned to use lspci|grep VGA to find out what video adapter I have. I had an idea to boot up from my ubuntu 6.06 CD and run off of that to see if it is stable, and it is. Then I determined what the video adapter is and looked at the xorg.conf file. Here is the results of lspci|grep VGA:

0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Here is an excerpt from the xorg.conf file:

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Int egrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "AG191"
        Option          "DPMS"
EndSection

This shows that the driver name is "i810"
So I opened the Synaptic Package Manager and searched this string "intel i810". It brought up only one result, which was:

Package                           Installed Version        Latest Version          Description
xserver-xorg-driver-i810   1:1.4.1.3-0ubuntu6   1:1.4.1.3-0ubuntu6   X.Org X server -- i8xx,i9xx display driver

It showed that this driver was installed.

So I got the bright idea that I could email a copy of the xorg.conf file to myself, reboot into 10.4, go to Synaptic Package Manager, search on "intel i810", install the driver described above then replace the existing xorg.cong file with the one that I emailed to myself.

The problem I encountered was that after booting into 10.4 and searching for that driver, it does not show up in Synaptic Package Manager. I think 10.4 uses a newer driver, but I think the old driver actually works better for me. Does this seem reasonable? Can someone talk me through how to find and install and use the older driver?

Thanks

---

### Post by cheruvim on 2011-01-08
on LTS it doesn't list a driver, I guess maybe the kernel is driving it. It might be in one of the repositories not meant for LTS but I'm not sure which.

---

