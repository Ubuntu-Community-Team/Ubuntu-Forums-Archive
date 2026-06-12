---
title: "no wifi options after ubuntu studio install"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by chamb244 on 2009-04-26
I'm using Xubuntu 8.04. Installed ubuntu studio and now no wireless:  I can enable/disable networking (from context menu of network icon), but I cannot see any available networks; "edit wireless networks" opens the standard box, but nothing is editable; "connection information' is greyed out. what to do?  I've tried rebooting into the different kernel options, but all the same.  help, please!

---

### Post by the_lex on 2009-04-26
Could you give a bit of information on what computer you have, and what kind of wireless card if you know?

Also, if you're using a laptop and you have a hardware switch or a button/function key to enable and disable your wireless, try switching it on then off and check your wireless connections again. I am having issues with Ubuntu Jaunty and wireless after using it for 2 years on my Thinkpad without a hitch, and flipping the switch on/off each time I log in is the only fix I've found at the moment.

I'm not as experienced as most of the people on here, but with your hardware info we can start looking in to this!

---

### Post by chamb244 on 2009-04-26
It is a ThinkPad T400, using Atheros wireless card.  

Output from lspci -v :

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Atheros Communications Inc. Unknown device 0035
        Flags: fast devsel, IRQ 21
        Memory at f4200000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>


Everything else seems working fine. I hope there's an easy way to get this going again.  For what it's worth, output from iwconfig:

lo        no wireless extensions.
eth0      no wireless extensions.

and output from iwlist scan:

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

Thanks for any help!

forgot to mention: I've tried toggling the wireless switch, but no changes.

---

### Post by t0mppa on 2009-04-26
> **chamb244 said:**
> 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

That's a common chip here. It's apparently featured in a few different types of cards, so you might have to try a few things out, shouldn't be anything too complex ahead though.

Can you post results of 'lshw -C network' from the terminal too? To see if it says the wireless interface is UNCLAIMED, which will mean it's the drivers that need configuring.

---

### Post by chamb244 on 2009-04-26
Yes, you're right! Output from "lshw -C network" is here:

  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:97:3c:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e-ich9m driverversion=0.2.9.5 firmware=1.8-3 ip=35.11.55.145 latency=0 module=e1000e_ich9m multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

Sorry to have to ask this, any advice on how to determine which driver I need and where to find it?

---

### Post by t0mppa on 2009-04-26
All right, with that settled let's grab you some drivers that should support your chip properly. The easiest and closest to Ubuntu way of life method is to follow the instructions in [this tutorial]("http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html"). The tutorial is aimed for Intrepid, 8.10, but I believe it should apply for Hardy as well. To follow it you'll have to make a few subtle changes ie. getting 'linux-backports-modules-hardy' instead of ' linux-backports-modules-intrepid' and using replacing gedit with mousepad (Xubuntu equivalent of gedit) for instance, but other than that it should work.

Ath5k works for most people and is actually pushed into Ubuntu core in the later releases, but if it doesn't or you run into some trouble, do post back here.

---

### Post by chamb244 on 2009-04-26
Thanks so much for this help!  Okay, I've followed the steps there (making changes where necessary for Xubuntu 8.04) but unfortunately still no changes.  lshw output is as before, which means the drivers aren't working, right?  One thing I'm confused about: it seems that the tutorial instructions have you install a driver, and then blacklist the same driver.  Is that what's going on?  Now, when I enable my Atheros drivers in (system>hardware drivers), they are disabled after a reboot.  I assume it is the blacklisting doing this, but I'm probably just not understanding.  Any suggestions?

---

### Post by t0mppa on 2009-04-26
You did try it without blacklisting first, right? Blacklisting is only an emergency fix that isn't recommended, since as far as I've grasped the subject it can cause other problems elsewhere.

---

### Post by chamb244 on 2009-04-26
yes, I tried connecting before blacklisting.  Either way, the wireless options are not visible (except for "edit wireless connections" which doesn't do anything).  And the output of lshw is the same.

I wonder could it have to do with a mismatch between driver and system architecture?  The width in in the unclaimed network is 64.  The The version of Xubuntu is 32 bit.  The processor supports 64 bit OS (and came with 64-bit Vista installed).  I don't know if this is a helpful clue or not.

---

### Post by t0mppa on 2009-04-27
Ok then, try [this tutorial]("http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/"). These are still native Linux drivers for Atheros cards from the same organization, just the older generation. And it seems to work a bit better than ath5k in the older Ubuntu versions, that don't yet have the latest ath5k available. It's a bit more work, as you have to compile the drivers manually.

---

### Post by chamb244 on 2009-05-19
Sorry for late follow up on this. I had to put everything aside as work deadlines intervened.  When revisiting my situation, I decided to upgrade to 8.10, upon which my wireless problem was magically fixed. So far, so good..  

However, I must say SINCERE THANKS to Tommpa for help.  I did learn a lot and hopefully this thread will help others out in similar situations.

---

