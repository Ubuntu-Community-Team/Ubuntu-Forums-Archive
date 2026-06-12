---
title: "Problem with broadcom 4313 and screensaver"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by ravengangrel on 2011-01-21
I have Ubuntu Desktop 10.10 i386 installed in an HP-mini Netbook, which has a bcm4313 wireless network device.

When the screen is set to sleep due to inactivity (with the default settings), I lost my wireless connection. It shows as connected in NetworkManager but it doesn't receive data. For example, if I let it updating my system, when I get back I see that the last packet downloads are being cancelled. Then if I try to browse google, I get a timeout after a couple minutes.
Disconnect the network, connect again, and everything works.

I am not sure if it's just the screensaver or putting the screen to sleep what causes the problem. I have experienced this also in Linux Mint 10. 

Also, at work I have a server machine with Ubuntu Desktop Maverick installed, and I think I experience similar problems with the wired network.
However, I can't say for sure that it's the same problem, I haven't been able to test it enough.

Is this a well known problem? I haven't found info in google but also I'm not sure how to search for it. Is there any workaround? 
Besides turning off screensaver

---

### Post by ravengangrel on 2011-01-23
Browsing the forums I have found that it's a pretty common problem.

I have found a workaround, although not a good one. I have post it in other threads, but will let it here too just in case someone finds this useful.

It's unrelated to the screensaver. The problem lies within the "put screen to sleep" in Power saving settings.

So to avoid this, it's enough to set it to "Never" in both AC and Battery modes.

If someone has any idea about this issue, please share it. I find it quite annoying having to trade battery life for internet connection...

---

### Post by grahammechanical on 2011-01-23
You say

> I find it quite annoying having to trade battery life for internet connection...

So, who is to blame? Ubuntu or Hewlett Packard and all the other companies that manufacture netbooks and notebooks that do not give a satisfactory battery useage to meet their claims of product usefulness?

Or, perhaps it is us, the users who expect more from machines than technology is able to give at the present time?

Regards.

---

### Post by ravengangrel on 2011-01-23
grahammechanical, the battery life meets (quite surprisingly for me, TBH) the claims from HP.

The issue here is that, if I need to download something from Ubuntu, and I don't need to do anything else, I have to let the screen turned on, wasting some battery life.

So, Ubuntu is clearly to blame.

Regards.

---

