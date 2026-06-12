---
title: "mac address help and arp"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by dazman19 on 2010-12-22
I have a bit of a dilemma, we had a server which had a panic and spat about 1000 errors+ and then lost a lot of files, some recoverable from lost+found and some not. Anyhow, we moved this to another PC temporarily while we were rebuilding the server. 

The server is back up now, but someone has turned off the PC and the site is remote. My server is still on and I can get into it. 

The two machines were talking  before someone powered off the pc.

BUT.. i looked in the arp cache on my box and its empty: 
? (192.168.0.1) at 00:1c:f0:92:eb:ba [ether] on eth0
on the mac address of the router is listed. 

Surely there must be a log file with mac addresses in it somewhere in the PC that i can view to find the Mac address of the machine that was switched off so i can wake it.

---

### Post by gmargo on 2010-12-22
I don't know of any log file, but I could be wrong.  If the IP addresses are handed out with DHCP, then your DHCP server will probably still have a record of it in it's leases cache.

---

### Post by redmk2 on 2010-12-22
> **dazman19 said:**
> 

...

Surely there must be a log file with mac addresses in it somewhere in the PC that i can view to find the Mac address of the machine that was switched off so i can wake it.

MAC addresses are only stored in the ARP cache.  You can get all the running hosts on the network segment with this```
ping -b <your_Network_ID>
```

I'm curious.  What will be gained in having the MAC address of the down host (PC)?  How would you start it using the MAC address?

---

### Post by kistenyer on 2010-12-23
i could find lines like this with mac and ip in the syslog files, in /var/log directory.

Dec 21 18:01:16 kis-laptop arpalert: seq=2, mac=00:17:31:b4:a2:66, ip=192.168.1.100, reference=192.168.1.2, type=ip_change, dev=eth0, vendor="ASUSTek COMPUTER INC."

the two day old info was in my compressed syslog file, syslog2.

---

### Post by tad1073 on 2010-12-23
> **redmk2 said:**
> I'm curious.  What will be gained in having the MAC address of the down host (PC)?  How would you start it using the MAC address?

sounds like he is gonna try some mac spoofing to me

---

### Post by gmargo on 2010-12-23
> **tad1073]
sounds like he is gonna try some mac spoofing to me     
[/quote][QUOTE=dazman19 said:**
> find the Mac address of the machine that was switched off so i can wake it.

He said he wants to wake it up - so it must be set to "wake on lan"?
I didn't know how that worked, but it's explained well here: [http://en.wikipedia.org/wiki/Wake_on_lan](http://en.wikipedia.org/wiki/Wake_on_lan)

Although, at this point, he probably just used the telephone.

---

