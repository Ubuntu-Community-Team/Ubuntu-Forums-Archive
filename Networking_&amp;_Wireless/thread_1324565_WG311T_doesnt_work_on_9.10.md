---
title: "WG311T doesnt work on 9.10"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by frito on 2009-11-12
The Ath5k website lists my adaptor as having the chipset:
AR5002G (b/g) (AR5212)
which is supposed to work well
"802.11g works well."

I upgraded from a distro with an old kernal which used madwifi which worked great. 

How can I either make this work with ath5k, or switch to madwifi? Or should this be posted somewhere else?

thanks!

EDIT:
Here is some stuff which may be of interest... when I use iwconfig the card isnt seen at all.
```

lspci
...
05:0a.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
profx@Cerebro:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by raritzu on 2009-11-23
I have the same problem. And I decided that life is too short for this.

See ya'
:)

---

### Post by raritzu on 2009-12-03
This one worked: [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

You will have to manually sort out the blacklist files (because the actual blackist is separated out in wifi specific files)

---

