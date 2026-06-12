---
title: "Wireless card has now disappeared"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by mttman on 2009-08-19
Hello,

I have a strange issue where my wireless card is no longer being detected. I have recently reinstalled Ubuntu 9.04, wireless worked fine for several days (did software upgrades etc) then out of the blue it disappeared. 

when this first happened I thought that it had just gone down so I ran this series of commands to try to get it running```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:25:93:f8:a5  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe93:f8a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4151284 (4.1 MB)  TX bytes:419690 (419.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr f2:5d:dd:0d:1c:da  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ lsmod |grep ath5k
$ sudo modprobe ath5k
$ lsmod |grep ath5k
ath5k                 107008  0 
mac80211              217208  1 ath5k
cfg80211               38032  2 ath5k,mac80211
led_class              12036  2 ath5k,thinkpad_acpi
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:25:93:f8:a5  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe93:f8a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4151284 (4.1 MB)  TX bytes:419690 (419.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr f2:5d:dd:0d:1c:da  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ 


```
This happened once before, about three days ago, and I found that there was i file /etc/modprobe.d/blacklist-ath_pci.conf which was blacklisting the driver (for some reason). I removed this file (cp somewhere then rm) rebooted and my wireless worked for a few days. now it's doing the same thing and there is no blacklist-ath_pci.conf file for me to remove.

In case it's important here are the contents of the file I removed
```
$ cat blacklist-ath_pci.conf 
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

```

Any help I could get about this would be very much appreciated.

Thank you

Mttman

---

### Post by oboedad55 on 2009-08-19
> **mttman said:**
> Hello,

I have a strange issue where my wireless card is no longer being detected. I have recently reinstalled Ubuntu 9.04, wireless worked fine for several days (did software upgrades etc) then out of the blue it disappeared. 

when this first happened I thought that it had just gone down so I ran this series of commands to try to get it running```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:25:93:f8:a5  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe93:f8a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4151284 (4.1 MB)  TX bytes:419690 (419.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr f2:5d:dd:0d:1c:da  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ lsmod |grep ath5k
$ sudo modprobe ath5k
$ lsmod |grep ath5k
ath5k                 107008  0 
mac80211              217208  1 ath5k
cfg80211               38032  2 ath5k,mac80211
led_class              12036  2 ath5k,thinkpad_acpi
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:25:93:f8:a5  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe93:f8a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4151284 (4.1 MB)  TX bytes:419690 (419.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr f2:5d:dd:0d:1c:da  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ 


```
This happened once before, about three days ago, and I found that there was i file /etc/modprobe.d/blacklist-ath_pci.conf which was blacklisting the driver (for some reason). I removed this file (cp somewhere then rm) rebooted and my wireless worked for a few days. now it's doing the same thing and there is no blacklist-ath_pci.conf file for me to remove.

In case it's important here are the contents of the file I removed
```
$ cat blacklist-ath_pci.conf 
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

```

Any help I could get about this would be very much appreciated.

Thank you

Mttman

Hey, I'm having the same problem. Had to do a reinstall after Windows trashed my system and now I have no wireless. Works under windows but under no version of Linux. I'm having a guy help me via IM tomorrow night. I can let you know if he gets anywhere.

Jon

---

### Post by t0mppa on 2009-08-20
> **mttman said:**
> I have a strange issue where my wireless card is no longer being detected. I have recently reinstalled Ubuntu 9.04, wireless worked fine for several days (did software upgrades etc) then out of the blue it disappeared. 

when this first happened I thought that it had just gone down so I ran this series of commands to try to get it running

A more descriptive command would be **lshw -C network** as it will display the status of your wireless card and the driver (if any) that's getting associated with it.

> **mttman said:**
> This happened once before, about three days ago, and I found that there was i file /etc/modprobe.d/blacklist-ath_pci.conf which was blacklisting the driver (for some reason). I removed this file (cp somewhere then rm) rebooted and my wireless worked for a few days. now it's doing the same thing and there is no blacklist-ath_pci.conf file for me to remove.

That does not blacklist ath5k, it blacklists the earlier version of the ath driver developed by Madwifi (and often referred to as "the madwifi driver", even though ath5k and ath9k are also developed by the same folks). So, removing that file will likely just add more trouble, if you use ath5k, as having two drivers for the same interface active simultaneously often means neither one works due to conflicts.

---

### Post by madhavhmk on 2009-08-20
check out this comprehensive guide to ndswrapper related problems:

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by mttman on 2009-08-23
I have some new information about this issue.

I have found that when my wireless card disappears power cycling my battery will bring it back (let the battery run down until it is dead and then plug in the laptop to let it start up again.) As it is this will only bring it back for a few days (2-3) before it disappears again. 

I have also gone through and blacklisted the drivers ath9k, madwifi, ath_pci and ndiswrapper in the hopes that this will stop the collisions (no effect). 

I was also wondering why you sent me to the ndiswrapper information  madhavhmk, when this is a problem with a native Linux driver? Not that I don't appreciate the help, just wondering about the why to learn for the future.

hopefully this new clue will help 

And thank you all for your input so far.

Mttman

---

### Post by mttman on 2009-08-23
Oh yeah,

Since I can sometimes get it working I will post some info from when it is running.

```

$ lsmod |grep ath
ath5k                 107520  0 
mac80211              217592  1 ath5k
led_class              12036  2 ath5k,thinkpad_acpi
cfg80211               38288  2 ath5k,mac80211
$ sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e2:86:62:83
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.2.2 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:25:93:f8:a5
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:0d:9d:97:53:39
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
and the blacklist file I created for review (in case I messed it up)
```

$ more /etc/modprobe.d/blacklist-wireless.conf 
#blacklisting wireless drivers that could be causing conflicts
blacklist ath9k
blacklist ndiswrapper
blacklist madwifi
blacklist ath_pci

```

Will post the "sudo lshw -C network" command again after it goes down next.

Once again - thank you to everyone helping me with this

Mttman

---

