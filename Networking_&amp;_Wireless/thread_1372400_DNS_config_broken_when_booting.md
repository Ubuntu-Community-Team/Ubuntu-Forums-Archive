---
title: "DNS config broken when booting"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by professorYaffle on 2010-01-04
I have a jaunty installation which is working fine, and I'm gradually getting a dual boot of karmic (desktop amd64) up to speed to take over from it. 
I've got a fairly standard ADSL modem/switch/router connected by wires to the machine as eth0.
I setup local static IP etc. during installation (no DHCP at all) and it worked fine for quite a while. Then, after an upgrade one day, DNS broke on reboot.
After booting now, /etc/resolv.conf is essentially empty (just comments) but the networking service is up. I can ping places out on the web.
If I "/etc/init.d/networking restart" then  /etc/resolv.conf gets the correct "nameserver" and "search" lines added to it and everything is fine... until next boot.

I never really worked out exactly how Ubuntu controls its networking config, and I'm further confused by the changes to the booting setup in Karmic. Please could someone help me understand what's going wrong here?

---

### Post by Iowan on 2010-01-04
I saw a similar [thread]("http://ubuntuforums.org/showthread.php?t=1372156") - one suggestion was to install the **resolvconf** package. Have you tried setting up the static addresses in Network Manager (maybe you do) or setting up static leases in the DHCP server?

---

### Post by professorYaffle on 2010-01-05
resolvconf is already installed and my /etc/network/interfaces already has the correct dns-nameservers line these were (I believe) setup by the "manual network configuration" during installation.

Poking around a bit I found a resolvconf startup entry at /etc/rcS.d/S07resolvconf. So I tried running that by hand, but it didn't fix the problem. Only /etc/rc0.d/S35networking seemed to do the job.
So I hazarded a guess that maybe resolvconf was the *problem* not the solution and removed the package.

It now seems to work fine again! :)

---

### Post by Iowan on 2010-01-05
Glad you got it fixed... I guess that's why I don't get paid for advice.

---

