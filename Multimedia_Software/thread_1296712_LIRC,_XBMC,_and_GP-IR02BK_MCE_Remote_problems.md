---
title: "LIRC, XBMC, and GP-IR02BK MCE Remote problems"
date: 2009-10-21
forum: Multimedia Software
---

### Post by Maverick7687 on 2009-10-21
I am having trouble with this remote/receiver/blaster setup and I have looked everywhere for answers. Some people say they have it working but I can't find any definitive fix. 

I am setting up an HTPC with Ubuntu 9.04 and XBMC, I have LIRC installed and the receiver plugged in. I used the Windows MCE Remote (New-Phillips) when I installed it. lsusb shows nothing, I can unplug the receiver and I get the same thing with lsusb as I do without it. Have tried different lirc.conf files and different USB ports with no results.  This is listed as an eHome Vista MCE Receiver in Windows and the Remote and Receiver model numbers are both the same (GP-IR02BK) [This is the exact hardware I have, bought from this link.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880121002&Tpk=gp-ir02bk")

I am still learning the Terminal and still not that fluent with all things in Linux so take it easy on me.


Thanks

---

### Post by sites on 2009-12-03
Mine works just fine with XBMC on 9.04.  Here's my command for installing lirc.

sudo aptitude install lirc lirc-x lirc-modules source

During setup I chose the same Windows MCE Remote (New-Phillips) setup as you.  The next step is for the IR blaster, which isn't necessary.  After that it works fine with what i would call the mid-section of the remote.  That is, the three sections with a circle of buttons around the (>) "play" button, the "OK" button, and the "Windows" button.  Other than that only the power button works to shut XBMC down, and the "BACK" button for navigation.

---

