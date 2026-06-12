---
title: "Have to reset router to acess internet"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by Bree_M on 2011-06-17
Hey all, 

So I have been a Ubuntu user for a few months now, and loving it so far... Only problem I just can't seem to figure out ; Every time I try to access the internet from home I get a "server not found' in firefox, when this happens I go reset the router hit 'try again' or 'refresh' and then I connect and my homepage comes up. 

Also at some point during the process any devices currently using the connection are temporarily cut off.. which I found to be bizarre. Another thing that is probably note-worthy my home connection is the ONLY placed this happens.. school, work, library, and other people's home connections have all connected no problem so far.

If anyone has any ideas on how to solve this mystery would be greatly appreciated!

---

### Post by compmodder26 on 2011-06-17
Can't exactly point out why you have to constantly reboot your router.  But I can tell you that rebooting the router will most certainly cause all connected devices to lose their connections until it is fully booted back up.  So I wouldn't worry too much about that problem.

As for your primary problem, how often does this occur?  Is it just when you first try to connect to your home network or does it happen at other times (ie, leaving your laptop for a while and coming back to the connection dropped)?

---

### Post by DirtyPC on 2011-06-17
if you're using a broadcom b43 driver it's probably that as they're renound for not being very stable. if it supports it try and get the sta driver.

post the output of lspci

---

### Post by Bree_M on 2011-06-17
Wow, thanks for the quick replies!!

sorry should have been more specific. while I'm trying to connect before resetting the router is when the other devices are cut off.. i agree tho.. that if we figure out whats going on w/ me that this will go away... 
I dont believe i'm using the driver mentioned...

my output for lspci:

bree-Compaq-Presario-CQ60-Notebook-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by Bree_M on 2011-06-17
oh yeah.. connection is usually good as long as laptop is on... as soon as it is rebooted or shutdown and started back up again is when problem comes back...

it's and easy enough work-around... but it gets a bit inconvenient and I know there must be a permanent fix... i just haven't been able to find it... :P

---

### Post by pricetech on 2011-06-17
What you're describing sounds like a router issue, not a computer issue, unless I'm completely missing something.

If you don't have the issue anywhere but home, and other devices at home are affected as well, it points squarely at the router.

They're not that expensive any more.  Just pick up a replacement.

---

