---
title: "xubuntu 9.04 broke my wireless"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by giancast on 2009-05-20
Hello I have been using ubuntu for a while. Saturday I decided to update my old Sony Vaio that was running perfect 8.04 to 8.10 and then to 9.04. These updates were all done via the wireless. From 8.04 to 8.10 the update went fine, then I decided to go to 9.04 since it is working fine in my desktop. The entire update was done wireless. After the reboot my wireless does not work anymore. I get the message no network tools available.
After doing some forum search I commented out in the blacklisted modules the ath rebooted and nothing.

This is the output of my lshw -C network
giancarlo@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:21:b2:2f:ca:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
giancarlo@ubuntu:~$

The card that I have when I first used it I had to do nothing Ubuntu recognized it automatically. The card is a Plug&Share from AT&T 6700G.

At least now when I open my network connections I can see my Home network, I am typing this email connected hardwire to the network.

Any help would be appreciated.

Thanks

---

### Post by mhpathfinder on 2009-05-20
I have two options to suggest.  Connect an ethernet cable and perform an update.  Jaunty may recognize your card, but may not have the drivers installed for it.  You should see a green Hardware icon on the upper right of your top panel, if this is the case.  Open the Hardware installer, and it should identify your WIFI card with the proper drivers suggested for activating it.

Option two, which worked for me, after failing a Jaunty install with my WIFI.  I have an HP L2005US Special Edition with a Broadcom WIFI card.  I conducted a clean install of Jaunty 9.04 with a wired ethernet connection.  The new system recognized that I had the card and a NVidia video card, and provided the option of installing the proprietary drivers for them with a little hardware alert icon to the upper right of my top panel at my post-install boot.  It needed the wired connection to download and install the drivers.  From that point, I was wireless again.  Jaunty automaticaly recognized the card and WIFI.

Chances are that someone may come up with an easier method without reinstalling Jaunty, but if this doesn't happen, option two should work just fine.  It just means a couple of extra hours of backing up your documents and files then restoring them after the system install.  But, you'll get your WIFI back in jaunty.

---

### Post by giancast on 2009-05-21
Thanks for your reply. I will try it tonight when I get home. This is a very old laptop, The wired and wireless cards are pcmcia cards, so I have to remove the wireless to use the wired and viceversa. Also the CD ROM is an external one that has a pcmcia slot so when I am installing Ubuntu via CD-ROM I do not have either the wired or wireless cards in. As I said this is a very old laptop. VAIO PCGN505VE, maybe the original netbook, it is very light and small, everything is external it only has 128Mb RAM but it runs ubuntu like a champ. I do not use it for anything critical just to surf the net when I do not want to go to my desktop, and when I travel I take it with me to check mail. Maybe I should look into USB boot (as they say fat chance that it will work, but worth a try). Thanks again and I will post my results.

Update May 20: I did the wired update and it had nothing to do with wireless. After the update the wireless still did not work. Then based on the suggestion went to Applications- System - Hardware Drivers and the Atheros showed up and it said that it was not activated. I activated it and the card started working immediately. Thanks for your help. I am writing this email with the Sony Vaio connected wireless.

---

