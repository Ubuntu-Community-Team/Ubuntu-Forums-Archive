---
title: "Empathy (Google Talk) will not connect with static IP"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by alldunn on 2009-11-14
After setting a static IP, I cannot get Google talk to connect with Empathy.  I can change it back to DHCP and everything works fine.  All other Internet connectivity works fine.  Google talk is all I use, so I don't know if other services would have the same issue.  Has anyone else had this issue?  If so, how did you correct it?  Thank you in advance for your help.

---

### Post by driftertx on 2009-11-14
Are you also setting static dns? It would help if you showed how you're configuring either via a screen shot within network manager or **ifconfig -a** from terminal. I also recommend using OpenDNS as your dns servers. 208.67.222.222, 208.67.220.220

---

### Post by alldunn on 2009-11-14
> **driftertx said:**
> Are you also setting static dns? It would help if you showed how you're configuring either via a screen shot within network manager or **ifconfig -a** from terminal. I also recommend using OpenDNS as your dns servers. 208.67.222.222, 208.67.220.220

I am using network manager to configure the static IP.  See attached.  192.168.15.1 is my router which has the DNS settings configured.  I can browse the internet without any problems, so obviously connectivity is not the issue.  Also, here is the output from ifconfig -a.  Thanks for your assistance.

```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:f4:42:60  
          inet addr:192.168.15.205  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fef4:4260/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41329790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21385367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33741578776 (33.7 GB)  TX bytes:1442759491 (1.4 GB)
          Interrupt:28 Base address:0xa000
```

---

### Post by driftertx on 2009-11-14
Manually set DNS Server section to OpenDNS **208.67.220.220,208.67.222.222** save your settings, try empathy, if it still doesn't work reboot and test again, should work.

Also are you able to reach your default gateway?

from terminal: **ping 192.168.15.1 ** (paste response below)

from terminal: **host talk.l.google.com** (paste response below). 

install traceroute from terminal: **sudo apt-get install traceroute** 
then finally from terminal: **traceroute talk.l.google.com**

I hated empathy cos I think it's feature pale in comparison to pidgin which was a bad choice as the installed 9.10 IM client. If all else fails you can try what I run, pidgin (multi IM client just like empathy). 

From terminal "**sudo apt-get install pidgin**" then run it from Applications/Internet 

Good Luck!

---

### Post by alldunn on 2009-11-14
Setting the DNS to OpenDNS actually fixed my problem!  I must say though that it is quite strange that everything else network wise was working as it should, but Empathy.  I have had this problem with Pidgin also in earlier releases, but never bothered trying to figure it out and just stayed on DHCP.  I agree with you that Pidgin is far superior to Empathy and will most likely switch back soon.  Thank you again for the help!

---

