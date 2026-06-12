---
title: "Twinhan DVB-S CI (1034) channel scan problem"
date: 2009-03-01
forum: Multimedia Software
---

### Post by pc1 on 2009-03-01
I am trying to get a Twinhan DVB-S CI PCI Card AD-SP300 (1034) working with 8.10 with 2.6.27.

I have installed the latest drivers from [http://jusst.de/hg/mantis](http://jusst.de/hg/mantis) and the card appears to be installed correctly when I run dmesg | grep DVB.

When using mythtv, I can install the adapter card, set the LNB and various frequencies but when the channels are scanned the system hangs irrecoverably.

I've testing using 'scan' with the same results.  Sometimes it will return some scan results for a second or two but then hangs.

I've tried setting:
options saa7115 ignore=1,0x25,1,0x24,1,0x21,1,0x20

in the /etc/modprobe.d/options but this does not help.

Has anyone been able to get this card working successfully?

---

### Post by dabubu on 2009-07-28
Hi, 

I have been using Twinhan 1034 card on 2.6.24-24-generic (Hardy) for about a year.

I use the drivers at [http://www.jusst.de/hg/mantis](http://www.jusst.de/hg/mantis)

However, I cannot get the latest version (mantis-5292a47772ad) to install properly, the only one that seems to work is mantis-303b1d29d735.

My only problem is that when I boot I have to recompile and do an insmod. 

This is probably due to my lack of Linux kernel knowledge. 

I run this script after every time I boot (which takes several minutes to run and I would love to get rid of it). 


#!/bin/bash
#
cd ~/source/Twinhan/currentversion
sudo make rmmod
sudo make install
sudo make rmmod
sudo make insmod
test -c /dev/dvb/adapter0/demux0 && echo TV seems to be OK || echo TV Not working
   

Any ideas why it doesn't remember my insmod after I boot???

Thanks

Daniel

---

