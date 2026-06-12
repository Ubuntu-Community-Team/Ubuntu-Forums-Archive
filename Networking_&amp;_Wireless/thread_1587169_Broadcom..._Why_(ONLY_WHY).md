---
title: "Broadcom... Why? (ONLY WHY)"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by tonosecundino on 2010-10-03
I am not posting this because i need a howto or something like that. I am posting this because:

I want to know (only curiosity) WHY Ubuntu stopped getting Broadcom 43xx cards to work.

I mean, the trend is that more and more hardware can be used with Ubuntu, and NOT that something just stops working... Isn't it?

I insist, this is not a complaint, this is not a request for help... It's just curiosity. I want to know what is the, say, informatics reason.

Thanks!

---

### Post by sanderd17 on 2010-10-03
Sometimes a patch for some piece of hardware can break another piece. If everything goes well, the hardware should be still supported, it's quite possible that the hardware will be supported back in the next release.

---

### Post by pytheas22 on 2010-10-03
I wasn't aware of any issues with bcm43xx chips in any modern version of Ubuntu.  Where did you read that they're no longer supported?

My Broadcom 4306 card works great on Ubuntu 10.04.  I haven't tested 10.10 but I'd be really surprised if it doesn't work there.

---

### Post by tonosecundino on 2010-10-04
> **pytheas22 said:**
> I wasn't aware of any issues with bcm43xx chips in any modern version of Ubuntu.  Where did you read that they're no longer supported?

My Broadcom 4306 card works great on Ubuntu 10.04.  I haven't tested 10.10 but I'd be really surprised if it doesn't work there.

That happened to me exactly the day i went from **8.10** to **9.04**... And it has been impossible to me since then.

But, no problem, I keep researching... Someday, someday! haha

---

### Post by pytheas22 on 2010-10-04
> That happened to me exactly the day i went from 8.10 to 9.04... And it has been impossible to me since then.

But, no problem, I keep researching... Someday, someday! haha

I'd be really surprised if we couldn't get it to work, if you told us the output of a few commands like "lspci -nn", "dmesg" and "lshw -C Network".  But I know you've emphasized above that you're looking for "only why," so if you'd rather do the research on fixing the problem yourself, that's fine.

---

### Post by maclenin on 2010-10-04
I am not having the same joy with my 4312 card and 10.04 (as you are, pytheas22, with your 4306) and would certainly welcome a little assistance ([click here]("http://ubuntuforums.org/showthread.php?t=1579095")) - if it's not too presumptuous to ask (via someone else's thread)!

---

### Post by snowpine on 2010-10-04
The explanation WHY from linuxwireless.org:

> The Broadcom wireless chip needs software, called "firmware", that runs on the wireless chip itself during operation. This firmware is copyrighted by Broadcom and must be extracted from Broadcom's proprietary drivers. To get such firmware on your system, you must download the driver from a legal distribution point, as noted below. Then you must extract the firmware from that Broadcom driver by using b43-fwcutter (or bcm43xx-fwcutter) and install it in the special directory for firmware - usually /lib/firmware. Please note that the firmware from the binary drivers is copyrighted by Broadcom Corporation and must not be redistributed.

If you want to know HOW, instructions are on [the Ubuntu wiki]("https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx").

---

### Post by tonosecundino on 2010-10-04
haha This **great **community, always willing to help!!! And saying: "I know you just have curiosity, **BUT...**"

Thank you very much, this is what makes me prefer Linux better than Windows.

---

### Post by tonosecundino on 2010-10-05
Anyway, here's the definitive solution that worked for me.

[Blacklist dell-laptop]("http://ubuntuforums.org/showthread.php?t=1414946")

---

### Post by MasterNetra on 2010-10-05
I'm using a 4312, while doesn't work vanilla. If you can connect on a physical line or via a USB Wireless Adapter, you can go to hardware drivers (letting it update if necessary then restarting it if it does) you should be able to choose between two drivers, personally I would recommend STA, as my connections with it have been stronger and have been able to connect and maintain connection from further away.

---

