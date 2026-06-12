---
title: "Intel PRO/Wireless 3945ABG in Lenovo T60 not working"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by heke80 on 2012-01-17
Hello,

I have wireless network problem after clean Ubuntu 11.10 installation for Lenovo T60 laptop. I have tried sevaral tips/hints I found from forum, but have not succeed. I have few years experience with Ubuntu but mostly in surface level, I havent used terminal much. Its time for my first post.

Lets start from beginning: Command lshw -c network
 
```
karhu@ThinkPad:~$ sudo lshw -c network
[sudo] password for karhu: 
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:e5:0c:9f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=0.5-1 ip=192.168.0.142 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:44 memory:ee000000-ee01ffff ioport:2000(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:98:26:91
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-14-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:edf00000-edf00fff
karhu@ThinkPad:~$
```


After boot rfkill list
```
karhu@ThinkPad:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
karhu@ThinkPad:~$ 
```

By pressing FN+F5 soft block from bluetooth is removed.
```
karhu@ThinkPad:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
karhu@ThinkPad:~$ 
```

After boot all are back in blocket status, and I am in the beginning.
Rfkill unblock all + rfkill list all
```
karhu@ThinkPad:~$ rfkill unblock all
karhu@ThinkPad:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
karhu@ThinkPad:~$ 
```

This is the far I I has got. I cannot remove hard block from Wireless lan. What ever I do it stays.

I would appreciate if someone has solved similar problem, and could guide me. 

Thank You,
regards
Heikki

---

### Post by aromo on 2012-01-17
If you close the laptop, look on the edge of the keyboard closest to you, towards the left there is a Wireless switch.  Move it so it shows the green spot.  That should do it.

---

### Post by heke80 on 2012-01-17
Giving big thanks for your help.

Which was there and after using it situation is following

```
karhu@ThinkPad:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
karhu@ThinkPad:~$
```

I am able to continue. Lets see will I connect secured wireless network,

regards
Heikki

---

### Post by heke80 on 2012-01-17
Hihaa,

Its working, cable is useless.

Big credits for forum,

regards
Heikki

---

