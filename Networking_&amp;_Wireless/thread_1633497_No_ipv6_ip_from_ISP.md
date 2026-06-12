---
title: "No ipv6 ip from ISP"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by graafderk on 2010-11-29
I have Ubuntu 10.10 installed on my laptop. My ISP natively supports ipv6, but since last weekend, I do not get an ipv6 ip. When I use a live cd however, I do get an ipv6 ip. For as far as I can see, all settings (/etc/network/interface and the settings in network manager) are exactly the same.

Output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:XXX.XXX.XXX.XXX  Bcast:XXX.XXX.XXX.XXX  Mask:XXX.XXX.XXX.XXX
          inet6 addr: XXXX::XXXX:XXXX:XXXX:XXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21369292 (21.3 MB)  TX bytes:696510 (696.5 KB)
          Interrupt:17 
```when using the live cd, an extra line is added showing:

```
inet6 addr: XXXX:XXXX:XXXX:XXXX:XXXX:XXXX/64 Scope:Global
```I also have a Ubuntu server, which also does show the additional line (with scope:global). 
Can anybody help me find the right settings or suggest some steps to take to get my ipv6 working again? It used to work and (as far as I can recall) I did not change any settings.

EDIT: is there a way to let the netwerk be automatically configured as happens during installation? It would be nice to start with a clean and new set of network config files as there were just after I installed Ubuntu on my system, without a full reinstall of my system.

---

### Post by Gorkhaan on 2010-12-02
I'm experiencing the same issue! I'm thinking about downgrading to 10.04.1 LTS due to I couldn't find anything why doesnt my interface gettin' ipv6 address ( Global ).

---

### Post by graafderk on 2010-12-07
I reinstalled my system and it works again. I have no idea how it got broken, but a reinstall did the trick for me.

---

### Post by Gorkhaan on 2010-12-10
Yeah, but this sux.

Does anybody can fix this?

---

### Post by graafderk on 2011-04-29
After upgrading to Natty, again I do not get an IPv6 address with global scope. Any ideas how to fix this?

---

### Post by lemming465 on 2011-05-04
Is your network connection managed by NetworkManager?  If so, does the configuration file such as "/etc/NetworkManager/system-connections/Auto eth0" say *method=ignore* in the ipv6 block?

When I upgraded, I had at least one "method=auto" downgrade to "method=ignore".  If you are using the GUI interface, when you edit the network connection there is a dropdown on the IPv6 tab to control this.

---

