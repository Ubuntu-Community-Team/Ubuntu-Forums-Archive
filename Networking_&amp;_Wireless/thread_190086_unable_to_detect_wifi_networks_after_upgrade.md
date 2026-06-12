---
title: "unable to detect wifi networks after upgrade"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by carleton on 2006-06-05
So I upgraded to Dapper this morning, and everything seems to be great except (surprise surprise) the wifi. My card (d-link dwl-g630) is completely recognized in Network Settings, the only problem is that it seems unable to detect any wireless networks. I tried it at home and at school and it can't seem to find any networks at all. I have a windows laptop connected to my home network presently, so I know that's not the issue. 

I installed Network Manager and ndiswrapper but that don't seem to help. A lot of people seem to be having wifi issues with Dapper but most issues seem to be driver related while I'm fairly certain mine isn't. 

The confusing part of this is that in Breezy I didn't have any problems at all, it connected automatically. 

Has anyone run into similar issues? and If so how might I go about remedying  it?

---

### Post by ds694 on 2006-06-07
I also have a dwl-g630 wireless card and am experiencing the same problem after upgrading from breezy to dapper.  I am unable to pick up any wireless networks.  I have yet to find a solution.  If anyway can offer any suggestions, I would appreciate it.

---

### Post by Hilbert Schraal on 2006-06-07
See [http://www.ubuntuforums.org/showthread.php?t=186607](http://www.ubuntuforums.org/showthread.php?t=186607)

---

### Post by khughes on 2006-06-07
I just thought I would throw out some information about my trouble with this. I am running an hp nc6120 that is a centrino laptop with the intel bg2200 wireless card and the manual radio switch. When I first installed breezy I had this same problem and I went into the bios and found a boot option for the different modes the card could be in at boot. I just tried all the modes until the card stayed on (according to the wireless LED) on bootup. I am now running Dapper and never experienced the issue a second time.

---

### Post by ds694 on 2006-06-07
PROBLEM FIXED!
After browsing the forums some more last night and trying various suggestions, I finally managed to get the problem fixed.  My wireless is working better than ever now.  Just follow the instructions in the third post of the following thread: [http://ubuntuforums.org/showthread.php?t=145836](http://ubuntuforums.org/showthread.php?t=145836)

I know it says its for the DWL-G650, but it worked like a charm for my 630.  

Thanks to all who replied.

---

