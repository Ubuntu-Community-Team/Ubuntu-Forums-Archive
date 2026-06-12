---
title: "No dsl connections"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by FilthyLucre on 2010-01-17
Hello, I've installed ubuntu 9.10. Established the Dsl connection with

sudo pppoeconf

After this my connection worked just fine, but soon it just dissapeared.  There are no available connections at the Networkmanager at all! I've reinstalled ubuntu 3 or 4 times and every time its the same. I'm very new to Ubuntu, plz help me to solve this problem. I havent found any solutions yet, so I hope to get here some :)

Regards
FilthyLucre

P.S. ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:24:1d:c4:8d:b2  
          inet6 addr: fe80::224:1dff:fec4:8db2/64 Scope:Host         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:930 (930.0 B)  TX bytes:1060 (1.0 KB)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap: PPP (Point-to-Point Protocol)  
          inet addr:84.63.9.1  P-t-P:84.63.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:198 (198.0 B)  TX bytes:174 (174.0 B)

---

### Post by shredder12 on 2010-01-17
When you configure your dsl connection with pppoeconf, the network manager will show netowrk disconnected. This is because NM starts ignoring the interface thinking that you are manually configuring it, which you actually are.

And as far as disconnecting goes, you should use the pppoeconf command line tools to restart the connection..
if you want to turn off the connection use
```
sudo poff dsl-provider
```
to turn it on
```
sudo pon dsl-provider
```
In order to know the status of your connection, you may get some useful info using this command
```
plog
```
This command actually just prints out the logs related to dsl connection. But the info can be useful.
or you may even try 
```
sudo /etc/init.d/networking restart
```

You can actually configure the dsl connection from Network Manager but I guess there is this bug [https://bugs.launchpad.net/network-manager/+bug/394218](https://bugs.launchpad.net/network-manager/+bug/394218) because of which you won't be able to make a connection.

---

### Post by FilthyLucre on 2010-01-17
[FONT=monospace]Well, I've already tried

[/FONT]sudo pon dsl-provider

but it doesnt rly help :/

---

### Post by shredder12 on 2010-01-17
When the network doesn't connect after using pon.. try to check the output of plog.. you may find some useful informatio there e.g. modem hangup etc. 

But I would like to suggest you to try gnome-ppp or try using this fix, i am not sure if this works.. [http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html)

---

