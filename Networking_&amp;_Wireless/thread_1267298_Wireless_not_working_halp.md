---
title: "Wireless not working halp?"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by pcox on 2009-09-15
So I have decided to take the plunge in ubuntu, but for real this time, before I used to dual boot just for fun but seeing as I have ****** my computer and lost all my harddrive files, why the hell not give ubuntu a real shot.

so the problem is that I have forgotten how to get wireless up and running, I dont know how to check my wireless driver, so sorry for not posting my driver info.

Also, I think last time I just went into applications and added an application that did it for me, is there one that exists?

I know you guys are awesome here with stuff like this, thanks for the help in advance

ps, I have the latest Ubuntu 9.04.

---

### Post by Iowan on 2009-09-15
Post results of **ifconfig -a** and **lshw -C network**. I tend to assume that people know how, but I can explain how to get to a terminal if necessary.

---

### Post by pcox on 2009-09-15
```
philip@pcox:~$ ipconfig-a
bash: ipconfig-a: command not found
philip@pcox:~$ ipconfig -a
bash: ipconfig: command not found
philip@pcox:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:8f:c9:89  
          inet addr:192.168.0.155  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe8f:c989/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8389277 (8.3 MB)  TX bytes:965431 (965.4 KB)
          Interrupt:248 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr a2:f2:74:19:01:48  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

philip@pcox:~$ 
philip@pcox:~$ ishw -C network
bash: ishw: command not found
philip@pcox:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:8f:c9:89
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.155 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a2:f2:74:19:01:48
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
philip@pcox:~$ 
philip@pcox:~$ 


```

Ok I did as you said is that what you wanted?

---

### Post by Iowan on 2009-09-15
> **pcox said:**
> Ok I did as you said is that what you wanted?
Yup... Now I suppose you want an answer. ;)
Wired looks peachy - wireless... not so much.
The wireless card shows up, but lists no hardware address or alias. Possibly a driver problem...
A lot of what I found is somewhat dated:
According to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom") sticky, the BCM4328 should work. 
[Another]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") helpful page.
I keep finding possible [Broadcom]("http://ubuntuforums.org/showthread.php?t=1219592") help.

---

### Post by pcox on 2009-09-16
ok well it says my wireless card is installed but it does not pick up any connection, which leads me to believe that it is indeed, still not working.

I have tried doing some of the things in the above post but it still wont pick up a connection, and in my hardware window, it says it is installed?

So i dont get it ill post screenshots soon

---

