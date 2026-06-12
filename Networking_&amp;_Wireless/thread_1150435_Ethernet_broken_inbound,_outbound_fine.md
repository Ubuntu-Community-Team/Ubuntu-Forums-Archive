---
title: "Ethernet broken inbound, outbound fine"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by HarvesterOfBeer on 2009-05-06
I have a 40GB AppleTV that I have installed Mythbuntu 8.04 (now updated to 9.04) onto the internal disk. In general, the machine is working fine. Up until last night, I was using only the wireless interface (eth1 in my case) and it was ok, but I did have issues with insufficient bandwidth.

I ran a CAT5e cable to the machine, deactivated the wireless, and
enabled eth0. The wired interface comes up fine and gets an IP, etc. Typical operations at the SSH console work fine. However, during testing, I've observed some very odd behavior:

When I do something like this to send a big file from the ATV to
another machine:

appletv> scp bigfile.tgz remotebox:/tmp

...things go great. Fast speeds, etc. Unfortunately, when I try sending a big file to the ATV, like this:

otherbox> scp bigfile.tgz appletv:/tmp

I get an initial burst of traffic through, and it just stalls, never recovering. Seems like there is something for inbound traffic that can handle a low rate, but once some threshold is crossed, it dies. Similar behavior when I've tried copying a file over NFS, etc.

I've tried different ports on my switch, and different ethernet
cables. I have the "options processor max_cstate=2" in modprobe.conf. The update to 9.04 did not resolve the issue.

It smells like some kind of driver interrupt problem, but there are no messages in the logs, etc. Output from ifconfig and mii-tool are below.

Any ideas on how to troubleshoot? Thanks!



```
peterl@AppleTV:~$ ifconfig -v eth0
eth0      Link encap:Ethernet  HWaddr 00:17:f2:fa:fe:91  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fefa:fe91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31338 errors:20 dropped:33 overruns:20 frame:0
          TX packets:26425 errors:0 dropped:0 overruns:4 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3219999 (3.2 MB)  TX bytes:14938460 (14.9 MB)
          Interrupt:20 Base address:0x1000


peterl@AppleTV:~$ sudo mii-tool -v eth0
eth0: negotiated 100baseTx-FD flow-control, link ok
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
```


-Pete

---

