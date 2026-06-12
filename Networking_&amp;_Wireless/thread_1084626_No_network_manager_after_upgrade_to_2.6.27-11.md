---
title: "No network manager after upgrade to 2.6.27-11"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by blissb2599 on 2009-03-02
I did a clean install of kubuntu 8.10 (64bit) with KDE 4 (love it!).  I was happy that my D-Link wireless usb dongle was recognized and configured without any intervention!  I just clicked on the network manager icon, selected my network, entered the WEP key, and was off and running.

Ran the updates -- which updated the kernel to 2.6.27-11.  When I restarted the machine, the network manager icon never showed up, and I had no network connectivity.  Running ifconfig and iwconfig showed the wlan0 adapter attached to an unsecured network, but without having acquired an address.  I tried re-starting networking, running NetworkManager from the command line, ifdown/ifup -- everything my limited little brain could think of, all without success.

I went so far as to wipe and re-install.  Again, the connection worked until I did the updates.  I finally thought to reboot into the previous kernel (2.6.26-7 I think), and everything worked again.

What I've done for the moment is to set grub to boot into the older kernel by default.  Obviously I don't think that's a tenable long-term fix.

Suggestions?

---

