---
title: "Airlink 300N pci model AWLH6090 with RT 2860 chiip"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by holbrooka on 2009-01-02
Hi folks,

Just posting my journey to get my wireless adapter up and running, since it took some playing around to get it working.

This is an Airlink 300N PCI Adapter, Model AWLH6090.  From research it has a chip on that is an RT 2860 chip (I believe ralink chip, but not confirmed).

System Info:
Ubuntu 8.10 Intrepid Ibex 2.6.27-9
ASUS A8N-VM/CSM motherboard with nVidia 6150B NForce 430
AMD Athlon 64 3500 CPU
2GB DDR PC3200

First off:  I had some problems finding the right info and was not sure I was doing this right and am still not sure if it was the easiest way to do it, but it works now, so here is how it got going...

I followed this link [http://www.ab9il.net/linuxwireless/rt2860.html]("http://www.ab9il.net/linuxwireless/rt2860.html") which gave a great description on how to install some drivers that are available for the Ralilnk processor.

The instructions on this page were very accurate, with only a few changes for Ubuntu, mostly you will not find the file in this location :/lib/modules/*yourkernel*/extra/rt2860sta.ko (RT2860 driver), in Intrepid it shows up in a different location.

This alone did not do the trick for me.  I found this site that helped explain about a different tool for managing the network, [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

Following those instructions (except the search part, which for some reason did not find the wicd package, despite it being there? - I had to list packages by source to find it to allow package manager to install it.)

Once that was installed, I restarted and suddenly my card showed me available networks and I was able to connect without a problem.

I'm not sure if simply installing the wicd package would have allowed me to connect, as it says it has support for the ralink chips, but you can try it and see.

Good Luck!  And thank you to all of you who have posted so much to help us all out!

Adam:D

---

### Post by holbrooka on 2011-03-07
Update:

I upgraded from 9.04 to 9.10 to 10.04.  Somewhere in the last upgrade WICD was no longer able to see any wireless networks.

After trial and error here is what I found:

The Wireless Network Interface that had always been "ra0" in the WICD preferences was no longer there.  While trying to trouble shoot the problem, the network tools dialogue box indicated that there was now a "wlan0" wireless device and no "ra0" device.

Changing this in the WICD preferences fixed me right back up and we are off and running again!

Best of luck to you!

---

