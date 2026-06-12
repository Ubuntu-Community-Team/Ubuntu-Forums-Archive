---
title: "Help I'm desperate!  vpnc dns issues"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by bad_mo_fo on 2008-12-03
I have been trying to get vpnc to work in intrepid for a few days now.  I have no problem connecting to the cisco vpn.  The problem is that once I connect my resolv.conf gets overridden and dns no longer works or works painfully slow.  I have included an example of my resolve.conf file before and after connecting to the vpn.  Can someone please advise?  I have not tweaked my network settings at all.  This is a fresh install of Intrepid.  I was able to run vpnc on Hardy no problem with the exact same vpnc profile conf file.

Before running vpnc

nameserver 68.87.72.130
nameserver 68.87.77.130
nameserver 68.87.66.196
search hsd01.il.hsdl.il.comcast.net


After starting vpnc and connecting to vpn

nameserver 10.0.30.21
nameserver 10.0.10.138
nameserver 68.87.72.130
search wbb.corp.hsd01.il.hsd1.il.comcast.net

---

### Post by mosimea on 2008-12-03
I had this happen when I didn't disconnect properly (vpnc-disconnect).  You'll need to repair both your /etc/resolv.conf and the /var/run/vpnc/resolv.conf files, if I recall.

---

### Post by bad_mo_fo on 2008-12-03
> **mosimea said:**
> I had this happen when I didn't disconnect properly (vpnc-disconnect).  You'll need to repair both your /etc/resolv.conf and the /var/run/vpnc/resolv.conf files, if I recall.


I tried changing resolve.conf manually but it gets overridden. I forgot to include in my origianl post I am running the 64 bit Intrepid.

---

### Post by bad_mo_fo on 2008-12-04
Just compiled the latest version of vpnc-0.5.3 and I still have the exact same issue.

---

### Post by bad_mo_fo on 2008-12-04
Done wasting time on this issue....  I regretfully installed the cisco vpn client and it is working.

---

