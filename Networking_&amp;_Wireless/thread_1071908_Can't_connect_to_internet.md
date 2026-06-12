---
title: "Can't connect to internet"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by toolow50 on 2009-02-16
I deleted some programs I never use and now I can't connect to internet. I read some where to type this in the terminal: sudo lshw =c network and this is what shows up:

PLEASE HELP ME! THANKS IN ADVANCE

friebel@friebel:~$ sudo lshw -c network
[sudo] password for friebel: 
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:21:85:c8:f6:72
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=69.23.99.82 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
friebel@friebel:~$

---

### Post by x33a on 2009-02-16
how did you delete the programs? programs should be uninstalled and not deleted.

anyway, post the output of
```

ifconfig
cat /etc/network/interfaces
```

---

### Post by Mud.Knee.Havoc on 2009-02-16
Which programs did you delete?

---

### Post by toolow50 on 2009-02-16
> **x33a said:**
> how did you delete the programs? programs should be uninstalled and not deleted.

anyway, post the output of
```

ifconfig
cat /etc/network/interfaces
```


friebel@friebel:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:c8:f6:72  
          inet addr:69.23.99.82  Bcast:69.23.103.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42422 (42.4 KB)  TX bytes:692 (692.0 B)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5152 (5.1 KB)  TX bytes:5152 (5.1 KB)

friebel@friebel:~$ cat /etc/network/interfaces

---

### Post by toolow50 on 2009-02-16
> **x33a said:**
> how did you delete the programs? programs should be uninstalled and not deleted.

anyway, post the output of
```

ifconfig
cat /etc/network/interfaces
```

friebel@friebel:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by toolow50 on 2009-02-16
friebel@friebel:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:21:85:c8:f6:72
inet addr:69.23.99.82 Bcast:69.23.103.255 Mask:255.255.248.0
UP BROADCAST RUNNING MULTICAST MTU:576 Metric:1
RX packets:692 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:42422 (42.4 KB) TX bytes:692 (692.0 B)
Interrupt:219

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:64 errors:0 dropped:0 overruns:0 frame:0
TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5152 (5.1 KB) TX bytes:5152 (5.1 KB)



cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by x33a on 2009-02-17
you'll need to reconfigure the network.

try
```
sudo pppoeconf
```

this should connect you to the net. 

if you don't like this method, you can also use the network-manager.

---

