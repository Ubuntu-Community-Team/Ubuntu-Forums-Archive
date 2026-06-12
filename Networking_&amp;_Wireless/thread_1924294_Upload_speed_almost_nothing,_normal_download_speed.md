---
title: "Upload speed almost nothing, normal download speed in Ubuntu 11.1"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by Howard-BJ on 2012-02-12
I have just installed Ubuntu 11.1 (alongside Windows 7) on my new desktop (Gigabyte GA-EP45-DS5 mobo, Intel i7 CPU 2600 @3.4Ghz, 8 GB RAM, 2 TB HDD) . Initially I was surprised that the wired internet speeds were very slow (~ 1 Mbit/S download, 100KB/s upload), as measured by speedtest.net. 

Disabling IPv6 improved download to ~ 4 Mb/s, but upload still very very slow (speedtest .net fails to get a connection on the upload cycle  of the test

I traced the source of a bug related to the realtek RTL8111/8168B ethernet controller, and followed the instruction to replace the driver. (see forums.linuxmint.com/viewtopic.php?f=49&t=80757)

Download speed now OK (~9 Mb/S = same as other computers on my network, including this new computer on W 7), but the upload speed is still almost non existent, and hence internet doesn't really work. 

Can anyone shed light on this (I am a relative newbie, so might need a bit of guidance on a technical answer). Thanks.

Howard B-J

---

