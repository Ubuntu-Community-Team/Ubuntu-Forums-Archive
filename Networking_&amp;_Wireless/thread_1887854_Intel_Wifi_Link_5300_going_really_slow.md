---
title: "Intel Wifi Link 5300 going really slow"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by travlemon on 2011-11-28
Hello,

I am running Ubuntu 11.10 on a laptop that uses an Intel Wifi Link 5300 wireless-N built-in PCI card for wireless.  My upload speeds are at a crawl, even though I have a cable connection to the internet.  Speed tests show only about 14 Kb/s upload, but a healthy 4+ MB/s for downloads.  

When I sign into Windows to do the Speed tests, using the same Firefox profile (I symlink my Linux firefox profile to the Windows firefox profile), the speed tests fly at nice high speeds.

I proceeded to try a speed test in Linux again, with the Chromium web browser.  But the test remains awful.

Does anyone know how to optimize the wireless card so I can use it to its full potential? I don't recall having speed issues before upgrading from 11.04 to 11.10.  The driver that I'm using is the default driver that installs with Ubuntu.

Any help is much appreciated.  Thanks in advance!

---

### Post by travlemon on 2011-11-30
I've solved this problem somewhat.  I removed the wireless drivers packaged with Ubuntu (the iwlwifi*.ucode files in /lib/firmware) to remove the wireless card from being installed.  Then I installed the XP driver with ndiswrapper.  

With this, my speeds increased greatly and the speed tests show better results, and my router config pages no longer take forever to load.  However,  the speed is still remarkably slow, considering the capability of the card and close distance to the router.  

Just wanted to post an update, hopefully someone will be able to help me optimize the connection to work the way it should.

Thanks again

---

### Post by travlemon on 2011-12-04
This is my last update on this issue.  As stated above,  I have it working by installing the Windows driver via ndiswrapper.

Recent speed tests were reaching just about the same speed the card was reaching in Windows.  Only problem now is that sometimes when I start my system, the card absolutely refuses to connect to the wireless network.

If I reboot enough times, it eventually works without having changed any settings.  If anyone has any advice or insight on that, I like to hear it!

Otherwise, I can say that this thread is as solved as it gets!

---

