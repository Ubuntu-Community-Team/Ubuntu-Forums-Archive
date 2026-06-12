---
title: "Network traffic stalls"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by jakertberry on 2010-11-12
I've been running into an odd issue with two different Ubuntu machines. Most internet traffic on these machines will stall. At first I thought it was a time-based issue, but now it seems like it could be an issue based on the amount of traffic that takes place (the more traffic, the faster the stall).

The two machines in question are both running the 64-bit version of 10.10. They're both fresh installs (within the past day or two), and both exhibited the problem immediately.

**Machine #1:** Dell Latitude D630 Laptop
*Network Interface:* Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61) (driver: iwlagn, speed: 54Mb/s)

I first noticed the problem on this machine when I tried to download the Ubuntu installation CD (I forgot it at work, and needed the ISO so I could begin installing on machine #2). Using Chromium, I would start the download. I would get normal speeds (2.0MB/s) until I hit the 300MB mark or so. Chromium would then show that the speed was dropping. I opened System Monitor and saw that there was zero traffic taking place. I tried restarting the download, and it worked like a charm, until I hit the 310MB mark. Once again, the download stalled.
My first assumption was Chromium, so I tried running wget to download the ISO. To my surprise, it too stalled after about 250MB of data.
I can be browsing the web while this takes place and I don't run into any issues. It's only during long downloads where the problem seems to happen.

Interesting side-note: As I'm writing this, I'm noticing that file transfers from a Windows machine inside my network worked. I transferred about 1GB of data and it maintained a steady speed of 1.2MB/s to 1.6MB/s the entire time.

**Machine #1:** HP Elite 7000 MT Desktop
*Network Interface:* Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
 (driver: r8169, speed: 1000Mb/s)

This machine exhibited the same issue as the laptop. I attempted to download the Ubuntu installation CD using both Chromium and wget--both stalled. This machine also had the World of Warcraft downloader running. This program also stalled, usually after downloading anywhere from 300MB to 800MB of data. I would have to close the program and restart it.

To verify that this wasn't an issue with my internet connection, I had another laptop running Gentoo download a large file during these tests. When the Ubuntu machines stalled, the Gentoo machine only started to download faster (which is expected, since it magically got more bandwidth to play with).

Both of these machines are running the latest kernel provided in the updater: Linux hostname 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

What are your thoughts?

Thanks,

jaker

---

### Post by jakertberry on 2010-11-14
It would appear as though I've found a solution. I don't believe Ubuntu is at fault, but it's still technically an issue with Linux.

My router is running DD-WRT, and it apparently has issues when you connect to an ISP that has specific DHCP lease times. In this case, AT&T has a 10 minute DHCP lease for the DMZ Plus port, which is causing the router to release and renew with a different IP address after 10 minutes.

[http://svn.dd-wrt.com:8000/dd-wrt/ticket/973](http://svn.dd-wrt.com:8000/dd-wrt/ticket/973)

I think we can file this under "problem solved."

---

