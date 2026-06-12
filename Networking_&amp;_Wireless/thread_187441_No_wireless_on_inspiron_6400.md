---
title: "No wireless on inspiron 6400"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Dustismo on 2006-06-03
Hello,

Having major problems getting wireless to work on my dell inspiron 6400.  Just installed Dapper, got everything working except wireless.  The wireless card does NOT show up in the device manager, I've tried every tutorial I've seen, .  aargh...
the lspci listing for the card:

0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

Any help would be greatly appreciated.

Thanks,
Dustismo

---

### Post by lynxus on 2006-06-03
If you have a copy of your windows drivers try using the ndiswrapper OR try the following thread first.

It Should would with mixed setups, So it cant hurt giving it a try.

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by syadnom on 2006-06-03
i have this exact same message on a dell e1505 with a b/g 1390 wireless(e1505=6400)

the bcm43xx driver does not currently work on this bcm4311 chip.  you must use the newest ndiswrapper and use the windows driver.  do a search for 1390 and read my post for some detailed instructions

---

### Post by Dustismo on 2006-06-04
Syadnom,

Thanks for the advice, unfortunetatly it didn't work.  I removed/blacklisted the broadcom mod, and installed the proper driver using the newest ndiswrapper  Seemed to work, but the card is still not recognized.  No entries in teh networking tool for wlan.  and If I try:

```

~$ ifconfig wlan0 up 
wlan0: ERROR while getting interface flags: No such device

```

Any help?
Dustin

---

### Post by Dustismo on 2006-06-05
Can anyone help?  Aarrgh...  I can't even get it to recognize there is a wireless card, much less get it to work.. Maybe this lshw output helps..

```


           *-network UNCLAIMED
                description: Network controller
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0b:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:dfdfc000-dfdfffff irq:4


```


Can someone can out some other ways to get debug information?


thanks,
Dustin

---

### Post by syadnom on 2006-06-20
sorry cant help.  this works for me and i have done it 3 times(3 copies of ubuntu on my machine for testing)

hope the bcm4311 chipset starts to work with the bcm43xx driver soon.

---

### Post by wari on 2006-07-15
hmmm it happened to me. it detects the wireless card when you enable wireless using Fn+F2 (the wireless icon on the keyboard)

(but i also can't get it to work...)

---

### Post by Sh8kR on 2006-09-09
> **syadnom said:**
> i have this exact same message on a dell e1505 with a b/g 1390 wireless(e1505=6400)

the bcm43xx driver does not currently work on this bcm4311 chip.  you must use the newest ndiswrapper and use the windows driver.  do a search for 1390 and read my post for some detailed instructions


I have the same Dell e1505 and thanks for telling me I wish someone would have pointed this out in one of the several other post. So I will do the ndiswrapper and be done with it. What was the walk through that you used. 

David Rumptz

---

### Post by lifeempowered.com on 2006-09-14
Just got my inspiron 6400 working nicely, here's the howto i wrote:

[http://www.ubuntuforums.org/showthread.php?t=256105&highlight=inspiron+6400](http://www.ubuntuforums.org/showthread.php?t=256105&highlight=inspiron+6400)

---

