---
title: "Slow download speeds compared to Windows XP"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by rsm4nn on 2010-03-17
Hi All,

I have just made a move into Linux from Windows XP, there are now only two things that are holding me back from consigning Windows to the bin, one is connecting to my corporate VPN and the other I want to discuss here is the huge difference in download speeds between the two O/S's.

I use a paid Rapidshare account to download various things, in Windows XP using jDownloader I get over 1MB/sec easily, however on Linux I only get 400KB/sec using jDownloader!!!

This disparity is unacceptable in my eyes, I have tried numerous things such as changing RWIN values but still no luck.  In Windows I ran TCP/IP optimizer (from SpeedGuide.com) for my 10MB cable broadband connection, I believe my Linux is not optimized like Windows and I can't find a Linux equivalent of TCP/IP optimizer.

I was under the assumption and have been told by a few individuals that Linux has superior networking capabilities so I really hope someone can kindly help me with this problem so I can fully migrate to Linux.

Many Thanks

---

### Post by johnson.d on 2010-03-22
You can use the following command to change the MTU setting of the Network Interface to 1400 and try again.

$ sudo ifconfig ethX mtu 1400

---

