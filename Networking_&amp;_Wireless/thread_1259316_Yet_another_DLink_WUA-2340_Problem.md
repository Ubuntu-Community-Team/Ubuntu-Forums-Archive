---
title: "Yet another DLink WUA-2340 Problem"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by adamlen on 2009-09-06
First off I am having the exact same problem as here: [http://ubuntuforums.org/showthread.php?t=1188702](http://ubuntuforums.org/showthread.php?t=1188702)
The only difference is that in ```
lshw -C network 
``` the network interface is not listed. Also there is no sign of wlan0 anywhere.

Alright, so I've scoured the forums, and after repeat attempts at google searches I'm left posting. I have it setup Dual-Boot Vista-Ubuntu(9.04). I have installed ndiswrapper with utils and ndisgtk and disabled the "stock" drivers using rmmod (b43, b43legacy, ssb) which just told me that the modules aren't there(not listed in /proc/modules). 

I have installed multiple driver releases, all of them being the WINXP_2K versions. 

In the System > Administration > Windows Wireless Driver I have installed the inf file. Upon installation I received an error "Unable to see if hardware is present" but it says of course, "Hardware present: Yes".

I have done all the instructions from the thread listed above([http://ubuntuforums.org/showthread.php?t=1188702](http://ubuntuforums.org/showthread.php?t=1188702)) to no avail.

If anyone can help me with this problem it would be greatly appreciated as I can not afford to buy another "supported" dongle. 

Thanks in advance, 
Adam.

EDIT: Updated the post with attachments: the results of iwconfig, lshw, and the rc.local file contents

---

### Post by bkratz on 2009-09-06
> **adamlen said:**
> First off I am having the exact same problem as here: [http://ubuntuforums.org/showthread.php?t=1188702](http://ubuntuforums.org/showthread.php?t=1188702)
The only difference is that in ```
lshw -C network 
``` the network interface is not listed. Also there is no sign of wlan0 anywhere.


In the System > Administration > Windows Wireless Driver I have installed the inf file. Upon installation I received an error "Unable to see if hardware is present" but it says of course, "Hardware present: Yes".

If anyone can help me with this problem it would be greatly appreciated as I can not afford to buy another "supported" dongle. 

Thanks in advance, 
Adam.

This gentleman seems to have solved the problem in steps 3 and 4.

[http://ubuntuforums.org/showthread.php?t=1080863&highlight=WUA-2340](http://ubuntuforums.org/showthread.php?t=1080863&highlight=WUA-2340)

Good Luck!

---

### Post by adamlen on 2009-09-06
Will look, thanks.

EDIT: Already found this earlier, retried with 1.4 driver and still no wlan0, it did not work. Thanks anyway.

Still no luck, All the research I'm doing is leading to the same 'fixes'. If anyone can help it would be appreciated, as I really don't want to default back to vista for development :(.

---

### Post by peter.weyant on 2009-09-07
After many hours with my HP laptop the ndiswrap with 1.40 works.  I now have visibility on wlan0.  I would urge those having trouble to retry following the directions in this forum, and use the 1.40 xp driver.  Drop me a note if you are struggling.  [EMAIL="peter@weyant.com"]peter@weyant.com[/EMAIL], IM peter.weyant on gmail, ms, or yahoo.  Good luck.:P:guitar:


> **adamlen said:**
> Will look, thanks.

EDIT: Already found this earlier, retried with 1.4 driver and still no wlan0, it did not work. Thanks anyway.

Still no luck, All the research I'm doing is leading to the same 'fixes'. If anyone can help it would be appreciated, as I really don't want to default back to vista for development :(.

---

### Post by adamlen on 2009-09-07
Thanks, and yeah still struggling. I may end up IMing you soon, I'm on the IRC going over some things as this forum post hasn't mounted to a whole lot ;)

---

