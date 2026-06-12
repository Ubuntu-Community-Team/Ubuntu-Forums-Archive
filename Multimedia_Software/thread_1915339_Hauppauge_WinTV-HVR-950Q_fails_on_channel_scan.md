---
title: "Hauppauge WinTV-HVR-950Q fails on channel scan"
date: 2012-01-26
forum: Multimedia Software
---

### Post by hopeididgood on 2012-01-26
I'm trying to get my Hauppauge WinTV-HVR-950Q tuner card working.  

I went to the LinuxTVWiki page ([here]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q#Making_it_Work")) and saw that I needed to install firmware.  I went to the Software Center and added (or, it may have already been installed) the firmware-linux-nonfree package.  If I look in /lib/firmware, there is, in fact, the file "dvb-fe-xc5000-1.6.114.fw".  

Next, I saw on the wiki page that the drivers were already part of the latest Linux kernel.  I'm running 2.6.38-13-generic, so I thought the drivers should be there...  However, when I tried to run "scan" (and also) "w_scan" both failed.  

I'm not sure where I went wrong. (Do additional drivers need to be installed?) 

I would greatly appreciate any suggestions you can provide.  

Thank you.

(I'm running Natty, just in case that makes a difference.)

---

### Post by wolfen69 on 2012-01-26
Have you tried an actual tv app like TvTime, or XawTV? You can do channel scans from within those apps.

---

### Post by hopeididgood on 2012-01-26
I did try TvTime.  It just kept saying "no signal", however it didn't have an option for ATSC (and I think that was the problem, rather than the tuner).  

I wasn't aware of XawTV... I'll give that a try once I'm at home.  

Thank you for the suggestion!

---

### Post by hopeididgood on 2012-01-26
Okay, so I tried XawTV.  I had no luck with the program.  

Next, I tried Kaffeine.  I significantly increased the tuner timeout in the configuration area.  I actually managed to get it to scan and picked up a few channels.  

I re-scanned with w_scan and also managed to get a channel.conf file setup.  

However, I ran dmesg and noticed that I'm having the firmware reloading problem that's mentioned over [here]("http://ubuntuforums.org/showpost.php?p=8470912&postcount=4").  I tried their solution and think I managed to get the file created properly with vi.  

I'll keep trying it out over the next few days and see if it behaves consistently.

Thanks again!

---

