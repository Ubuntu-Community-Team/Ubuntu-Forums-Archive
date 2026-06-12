---
title: "intermittent network connection since installing 9.04"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by wrathkeg on 2009-09-23
Hi all,

Updated to 9.04 on Friday. Since then my network connection has been intermittent: not so much dropping out (I'm not aware that this has happened), but about half of the time it doesn't connect on booting up.  Resetting the router and then rebooting the machine seems to clear the problem but that seems like a sledgehammer fix....

Any ideas what the problem might be, or how to diagnose it?  I haven't fooled around with network settings, and have all update manager updates installed.  The computer is connected (by wire) to a D-Link DSL-G624T router.  The output of ifconfig right now, while the connection is working, is this:

```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:73:ef:c2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe73:efc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4424 errors:0 dropped:0 overruns:0 frame:2
          TX packets:3695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4483161 (4.4 MB)  TX bytes:575281 (575.2 KB)
          Interrupt:23 Base address:0xc000
```
Thanks in advance,
wrathkeg

---

### Post by rafemonkey on 2009-09-23
I had network problems after the 9.04 upgrade too. In my case the problem was that ipmasq was starting before eth0 was up. This left me with no route to the network. The fix was to restart ipmasq after the machine had finished booting. I don't know if this is what's going on with your machine, but try the following...
```
sudo /etc/init.d/ipmasq restart
```
Good luck!

---

### Post by wrathkeg on 2009-09-23
```
$ sudo /etc/init.d/ipmasq restart
sudo: /etc/init.d/ipmasq: command not found
```
I'm no guru, but I guess that can't be the problem :) but thanks for the suggestion.
wrathkeg

---

### Post by wrathkeg on 2009-10-11
turned out it was the modem router starting to die.  now it's dead, and has been replaced everything is working fine.  for reference, the modem router which started to die was [this DLink one]("http://www.dlink.co.uk/cs/Satellite?c=TechSupport_C&childpagename=DLinkEurope-GB%2FDLTechProduct&cid=1197319459522&p=1197318962293&packedargs=locale%3D1195806691854&pagename=DLinkEurope-GB%2FDLWrapper").  It died after about 2 years, which doesn't seem all that good to me.  I replaced it with [this Netgear one]("http://www.netgear.co.uk/wireless_adslrouter_dg834g.php") which was a dream to set up:  only had to enter ISP username and password, and all other settings were automatically detected.

---

