---
title: "Wireless connectivity in Ubuntu Server 10.04.3"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by dylan_m on 2011-10-28
Hey, haven't posted here in a while because I gave up on Ubuntu a while ago, but I'm giving it another go. I'm not impressed though :/

So I've been trying to connect Ubuntu Server 10.04.3 to the internet with a USB wireless adapter (Netgear WG111v2), and after 6 hours of frustratingly playing around, I got it to work (could ping google.com etc). The problem is, the connectivity was lost after a reboot.. I don't know how I got it to work for a second, it seemed like a miracle. I tried re-running the commands I used before this "miracle", but nothing worked. 

Here's a bit of info:

```
iwlist scanning
```

Looks good. ESSID and all other details show up.

However, 

```
iwconfig
```

doesn't. It states 

```
ESSID:off/any
```


I've tried following every howto out there and running basically every possible network related command, so don't bombard me with *run this, run that*, because none of them work.

I've got files like /etc/network/interfaces set up as well, so don't tell me how to configure those.. I just need to know how to connect to the network which shows up in iwconfig scanning.

Thanks

---

### Post by dylan_m on 2011-10-29
Thanks for all the help guys, but never mind about that, I ended up installing the xubuntu GUI and using it's network manager to connect. 

I only have one question now, if I uninstall the GUI, will the network still be configured?

---

### Post by varunendra on 2011-10-30
> **dylan_m said:**
> if I uninstall the GUI, will the network still be configured?
It depends. You may have to configure it manually as described here: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

