---
title: "Wireless is disabled"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by heigren on 2010-08-18
Hello,

```
lshw -C network
```

```

  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:ff:a3:3d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

How can I activate the wireless interface?
Thanks for all help!

---------------

Problem fixed! Thanks for all help!

---

### Post by Darkness Des on 2010-08-18
```
sudo ifup wlan0
```
Is what I would try first.

---

### Post by heigren on 2010-08-18
This happened:
> Ignoring unknown interface wlan0=wlan0

---

### Post by Darkness Des on 2010-08-18
Alright, try 
```
sudo ifup *-network
```

---

### Post by heigren on 2010-08-18
Same result, only with "*-network=*-network" this time.

---

### Post by heigren on 2010-08-19
Is there anyone that have someting? I really need this wireless to work!

---

### Post by Dagw00d on 2010-08-20
Is connecting to the internet via ethernet an option?
 
I had the same problem and was able to fix it by plugging directly into my router to access the internet and then system>admin>hardware, picked the driver for my wireless card, rebooted, and its worked beautifully ever since.
 
If you can't connect directly, then at least this reply is a bump. :)

---

### Post by solace.discord on 2010-08-23
> **Dagw00d said:**
> Is connecting to the internet via ethernet an option?
 
I had the same problem and was able to fix it by plugging directly into my router to access the internet and then system>admin>hardware, picked the driver for my wireless card, rebooted, and its worked beautifully ever since.
 
If you can't connect directly, then at least this reply is a bump. :)

my post in the Dell forum:
[http://ubuntuforums.org/showthread.php?t=1558791](http://ubuntuforums.org/showthread.php?t=1558791)

I have tried this method as well. my wireless is always disabled, and even when connected through wired ethernet, there are no proprietary drivers listed. I have tried through the live cd and by downloading the drivers as well. very frustrating.

---

### Post by heigren on 2010-08-26
Thanks for all the help! My friend tried to fix it, and suddenly it worked! No-one knows what actually happened, but at least the Internet is now working.

---

### Post by WJason on 2010-08-26
LoL  This isn't really solved if you can't provide the solution.

I'm having the same problem here.

---

