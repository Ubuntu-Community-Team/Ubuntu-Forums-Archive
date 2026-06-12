---
title: "Ubuntu won't connect to the internet"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by Niguere on 2010-08-23
Hello.  First post here.  Sure enough it's help thread.

I've got the latest Ubuntu installed on a partition on my ASUS N61J laptop.  But I'm writing this on my Windows partition because like the thread title says... it won't connect.  I plug my ethernet cable in and out.  Reset my cable modem etc.  Nothing.  I'm pretty noobish but I know the ip /release /renew trick with Windows.  Would something like that work here?

---

### Post by dineshs on 2010-08-23
In a terminal (applications-accessories-terminal)try the following commands and please post the results back here
```
ifconfig -a
```and```
sudo lshw -C network
```

---

### Post by Niguere on 2010-08-27
I'm back.  Very sorry for taking as long as I did but I was busy with a few things and I completely forgot about my Ubuntu partition.

This is what I got from fiddling about in the terminal like you said.

```
clyde@Gallahad:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:69:4c:df  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

pan0      Link encap:Ethernet  HWaddr d6:2e:79:01:2b:a7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:cf:86:97  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

clyde@Gallahad:~$ sudo lshw -c network
[sudo] password for clyde: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:cf:86:97
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d3e00000-d3e0ffff
  *-network DISABLED
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:69:4c:df
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:17 memory:d0200000-d023ffff ioport:8000(size=128)
clyde@Gallahad:~$ 

```

---

### Post by bkratz on 2010-08-27
This would probably be a good place to start

[http://ubuntuforums.org/showthread.php?t=1447313&highlight=AR8131](http://ubuntuforums.org/showthread.php?t=1447313&highlight=AR8131)

---

### Post by dineshs on 2010-08-27
Which ubuntu version are you using?
Do you use Network manager?If yes rightclick NM icon(top panel near the loudspeaker symbol)and ensure that Enable networking and enable wireless are ticked
You may also check BIOS

---

### Post by Niguere on 2010-08-28
Okay I'm back and I'm posting this from my Ubuntu partition.

Oh my f*ing god I can't believe this.  I installed the packages recommended from that other thread and restarted.  Nothing happened.  It turned out I just had to select wired network by LEFT-CLICKING the little connections icon.  Gah.

Sorry you guys.  I'll try and get more familiar with the gui and cli in the future.  >.>

---

