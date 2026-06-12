---
title: "Ubuntu 11.04 slow wireless with rt2x00usb drivers"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by borzwazie on 2011-05-05
I thought I would post a note here for anyone else struggling with crappy wireless in 11.04.

I have a usb wifi adapter from Belkin that uses the rt2x00usb driver, and it would either not connect, or connect so slowly as to be absolutely useless.

Try running the following command:

      **sudo iwconfig wlan0 power off**

This disables power management for this adapter. Once I disabled power management, my wireless worked at full speed. Not a full fix, to be sure, but should at least get some of you working.

To see if you're using this chipset, try running the following commands:

lsmod | grep rt
lsusb | grep rt2

My own example:

```


root@junkheap:/var/log# lsmod | grep rt
parport_pc             32111  0 
rt73usb                26569  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19915  1 rt73usb
rt2x00lib              47400  2 rt73usb,rt2x00usb
mac80211              259924  2 rt2x00usb,rt2x00lib
cfg80211              156299  2 rt2x00lib,mac80211

root@junkheap:/var/log# lsusb | grep -i rt
Bus 002 Device 002: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]


```

You might also try this on other wireless chipsets - can't guarantee results there, however.

---

### Post by redpiersystems on 2011-05-16
Thanks! I tried this with my WUSB600N adapter, and it worked. However, the built in wireless adapter for my HP G72 17.3" Notebook, w/ Ubuntu 11.04 and updated drivers directly from the realtek website, seems to stay just as slow. I ran the command for both wlan0 (built in adapter), and wlan1 (the USB adapter).

Still though, progress is progress. Thanks! :popcorn:

> **borzwazie said:**
> I thought I would post a note here for anyone else struggling with crappy wireless in 11.04.

I have a usb wifi adapter from Belkin that uses the rt2x00usb driver, and it would either not connect, or connect so slowly as to be absolutely useless.

Try running the following command:

      **sudo iwconfig wlan0 power off**

This disables power management for this adapter. Once I disabled power management, my wireless worked at full speed. Not a full fix, to be sure, but should at least get some of you working.

To see if you're using this chipset, try running the following commands:

lsmod | grep rt
lsusb | grep rt2

My own example:

```


root@junkheap:/var/log# lsmod | grep rt
parport_pc             32111  0 
rt73usb                26569  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19915  1 rt73usb
rt2x00lib              47400  2 rt73usb,rt2x00usb
mac80211              259924  2 rt2x00usb,rt2x00lib
cfg80211              156299  2 rt2x00lib,mac80211

root@junkheap:/var/log# lsusb | grep -i rt
Bus 002 Device 002: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]


```

You might also try this on other wireless chipsets - can't guarantee results there, however.

---

### Post by jarkko jaatinen on 2011-05-17
Thank you i cried many nights when i tried watch online videos from my networkspace
GREAT JOB!!!:)

---

### Post by esc1 on 2011-05-17
I am going to try this later tonight as the download speed is awful. For torrents I get a quarter of the speed I used to and sometimes can't browse the net at all even when not running any torrents.

---

### Post by zappadragon on 2011-05-17
Thanks I will have to try this later tonight too. I am having many problems with my HP dv6 using the ar9285 wirless

---

### Post by esc1 on 2011-05-18
I do believe it helped me to turn it off. Thanks.

---

### Post by peskadot on 2011-05-20
Have same problem with NETGEAR WN111v2 wireless.  Unfortunately, this solution did not work for me.

---

### Post by modmidget on 2011-05-21
I tried the command on my rt3070 USB wireless but it didn't help very much.  After running the command I can get a super fast connection for 20 seconds, then it disconnects for 1 to 2 minutes, then it reconnects for another 20 seconds.

---

### Post by redpiersystems on 2011-05-24
> **peskadot said:**
> Have same problem with NETGEAR WN111v2 wireless.  Unfortunately, this solution did not work for me.

Well, if that still doesn't help, it may be a DNS lookup config issue. See this post:

[http://ubuntuforums.org/showthread.php?p=9693360#post9693360](http://ubuntuforums.org/showthread.php?p=9693360#post9693360)

---

### Post by 5sm on 2011-08-24
I have had a solid connection since I applied this fix.  It was dropping every 20-30 sec before this.  I'm keeping my fingers crossed and hoping it continues to work well.  

thanks

---

### Post by Hackslife on 2011-09-02
> **peskadot said:**
> Have same problem with NETGEAR WN111v2 wireless.  Unfortunately, this solution did not work for me.

i had the same issue with WN111v2. This solution worked on me:
see: ubuntuforums.org/showthread.php?t=1742231
In two words, edit blacklist-ath_pci.conf and comment-out with a hash (#) the following line:
# blacklist ath_pci
Hope this helps.

---

### Post by velkypivo on 2012-07-26
Works great for Belkin F5D7050B wireless g adapter !

It fixed the slowness and replug issue.
Most importantly it also fixed a complete loss of network connection after system update.

Wish I knew this some time ago;
I previously scrapped both Ubuntu 10 and 11 installs because of this.

---

### Post by Juvencio on 2012-07-26
I had lots of issues with 11.04 and 11.10.
since I loaded 12.04 things have gone a lot smother for me.

I'm not saying it will solve your problems, but it's stability it better than version 11.

---

