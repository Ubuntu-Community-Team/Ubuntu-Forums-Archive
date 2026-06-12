---
title: "IP traffic shaping +GUI"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by azarias on 2012-01-17
How Everybody!!

I'm currently searching for some software with GUI, where I can configure traffic shaping per IPs for several clients in my network. 

Any suggestions ??

BR Alex

---

### Post by jonobr on 2012-01-17
Not sure about GUIs :-(
[This post ]("http://ubuntuforums.org/showthread.php?t=1373799")involving Iptables may be useful

or I have seen an application called [trickle ]("http://monkey.org/~marius/pages/?page=trickle")mentioned.

---

### Post by cruising on 2012-06-05
You can give [pfSense]("http://www.pfsense.org") and [zentyal]("http://www.zentyal.org") a try (if you don't use USB modems for Internet WAN connectivity). They both have excellent traffic shaping rules (especially pfSense) and zentyal offers UTM (Unified Threat Management) option too.

I did, however, had problems properly configuring USB Modems for connectivity; but they work great if your connection comes in through an Ethernet port.

Hope this helps.

---

