---
title: "WPA wireless on Eee PC 1000"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by astrobeaver on 2010-06-24
I am having trouble establishing a connection with my WPA wireless network at home.

Other laptops at home can connect to this network and even the Eee PC can join ***free ***wifi networks. The problem seems to be only with WPA networks.

When I enter the password for the WPA network, it tries to connect for a while and then shows me the password dialog box again.

I don't get any IP during this time, its always 0.0.0.0

I would really appreciate any guidance!

I reinstalled my Ubuntu netbook remix but that didn't help. This problem was occurring in the standard Ubuntu 10.04 too.

cheers

---

### Post by ajgreeny on 2010-06-24
Perhaps the adapter in the eee PC is not WPA enabled.  I have an old laptop with a netgear wg511v2 adapter which only works on WEP, not any form of WPA, though I thought the eee PCs all worked well.

---

### Post by astrobeaver on 2010-07-04
It worked for like 10 minutes before getting disconnected again. To make it work for those 10 minutes, I went to [ftp://ftp.debian.org/debian/pool/non-free/r/rt2860-source/](ftp://ftp.debian.org/debian/pool/non-free/r/rt2860-source/) and downloaded the rt2860-source_1.8.0.0-3_all.deb file. From [http://ubuntu-tech-blog.blogspot.com/2010/07/wireless-issues-with-ubuntu-1004-on-eee.html](http://ubuntu-tech-blog.blogspot.com/2010/07/wireless-issues-with-ubuntu-1004-on-eee.html)


But now I have downgraded my netbook to 9.10 and the wireless works just fine! 

I have always known that it's an issue with 10.04 so I finally kinda gave up on this release.

---

