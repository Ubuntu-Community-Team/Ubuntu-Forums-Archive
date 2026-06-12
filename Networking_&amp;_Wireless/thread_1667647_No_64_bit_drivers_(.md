---
title: "No 64 bit drivers :("
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by SeanAloisi on 2011-01-15
I have recently purchased an [[COLOR="RoyalBlue"]Edimax EW-7811Un[/COLOR]]("http://www.edimax.com/en/produce_detail.php?pd_id=347&pl1_id=1&pl2_id=44"), and have been unable to get it to work within Ubuntu 10.10 64 bit. There are open source drivers, but they are only for 32 bit Linux. I have been fooling around with it, but to no avail. Perhaps someone out there could shed some light on this. Any help would be appreciated.

I haven't tried ndiswrapper yet, so I'm going to go do that and post back results.

---

### Post by SeanAloisi on 2011-01-15
Ndiswrapper was fruitless. Can't seem to get it to work, and modprobe ndiswrapper now just locks up completely.

---

### Post by bkratz on 2011-01-15
Is this any help?

[http://ubuntuforums.org/showthread.php?t=1590873](http://ubuntuforums.org/showthread.php?t=1590873)

---

### Post by SeanAloisi on 2011-01-15
> **bkratz said:**
> Is this any help?

[http://ubuntuforums.org/showthread.php?t=1590873](http://ubuntuforums.org/showthread.php?t=1590873)

Thank you for the effort, but sadly it is not. Those drivers are for 32 bit only.

---

### Post by SeanAloisi on 2011-01-15
lsusb returns:

```
Bus 001 Device 006: ID 7392:7811 Edimax Technology Co., Ltd 
```

ndiswrapper -l returns:

```

net8192cu : driver installed
	device (7392:7811) present
```

tail /var/log/messages returns:

```

Jan 15 11:43:23 linux loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8192cu
```

Not really sure what's wrong.

---

### Post by SeanAloisi on 2011-01-15
Bump :/

---

### Post by SeanAloisi on 2011-01-16
Last bump D:

---

### Post by kirild on 2011-02-15
I have this working - try the driver source code from the realtek site:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)

Don't bother with their "automated" install.sh command, just cd to the driver directory and do a make && sudo make install.

---

### Post by SeanAloisi on 2011-02-15
You have it working in 64 bit?

---

### Post by jotie on 2011-04-11
Is there are solution for this yet?

---

### Post by kevdog on 2011-04-11
Just wondering if anyone tried building these from source on a 64bit computer?

---

