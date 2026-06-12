---
title: "Wireless password not recognized after Meerkat upgrade"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2010-10-16
I have an Asus K60 laptop with the Athlon chipset.  I had wireless working just fine under Lucid.  But after upgrading to Meerkat, I can't get my password to be recognized.  The router connection is seen without any difficulty, but the WPA password is rejected every time.  I've rechecked it, of course, and also checked that it works in the Windows partition on the same machine.  I'm using wicd and madwifi, recompiled for the -35 kernel.  Here's the relevant output of lspci:

> 02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)


I had the problem as soon as I restarted after the upgrade, before I reinstalled wicd and madwifi.  I assume that I was operating with network-manager at that point.

Any ideas?  Anyone else seen this?

---

### Post by SteveWD on 2010-10-16
Hi pwabrahams,

I have exactly the same problem.  My system was fine under lucid but when I upgraded to Meerkat I cannot log on to my wireless network.  I don't know if my password is being rejected but I guess this the case.  All I get is the wireless icon in the top right corner of the screen pulsing while it tries to connect but it never succeeds just telling me I have been disconnected from the wireless network.

I have a USB wireless dongle - D-Link GWL 122 (?) which can see the network fine.  My mobile and Windows machines can all see and access the internet through my router so I am confident there is nothing wrong with it.

Can anyone help?

Many thanks,

Steve

---

### Post by SteveWD on 2010-10-16
Hi pwabrahams,

Back again and I've solved my problem (and I hope yours too!).  If I reboot my system and run the 2.6.32-5 kernel (not the default -2) then all is well.  There must be something left out/broken in the default kernel build but all now works for me.

Cheers,

Steve

---

### Post by pwabrahams on 2010-10-17
I have the choice between two kernels: 2.6.32-25 and 2.6.35-22.  2.6.32-25 (is that the one you used?) is the old one from Lucid, I believe.  In any event, starting from it didn't help, although in the past the approach of going one kernel back has saved me.  Reverting the kernel requires recompiling madwifi, which is tricky because the kernel headers from that version aren't around any more and the recompilation of madwifi needs them.

---

