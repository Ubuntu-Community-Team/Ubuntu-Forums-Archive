---
title: "wirless and eth0 not working together"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by movchan on 2010-05-14
Goal: setting up Ubuntu (Ultimate) to work as a gateway for mixed OS on local lan. Wired connections jumping to Inet source via wireless hop.

Issue: When i have the LAN connected on linux the wireless connects but unable to browse the internet, if eth0 is unplugged then it works just fine. Need the Eth0 to be connected for this to work as a gateway...

Info:
1: for some reason Etho0 shows never connected but i am able to see other networked devices...

2: Not sure if there is some routing config that i have to setup

3: I have walked through the firestarter (firewall) wizard.. didn't seem to do much.

---

### Post by Iowan on 2010-05-14
Check results of **route -n** with eth0 dis/connected. If default gateway (UG) uses eth0...

---

### Post by movchan on 2010-05-14
This is what i get, first is disconnected
grindz@LinuxUE:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
11.11.1.0       0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         11.11.1.1       0.0.0.0         UG    0      0        0 wlan0
grindz@LinuxUE:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
11.11.1.168     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
11.11.1.0       0.0.0.0         255.255.255.0   U     2      0        0 wlan0
11.11.2.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         11.11.1.168     0.0.0.0         UG    0      0        0 eth0
grindz@LinuxUE:~$

---

### Post by Iowan on 2010-05-14
Does the "Shared to other computers" method for eth0 work as advertised for you? Otherwise, there should be an NM option to edit **routes** for eth0.

---

### Post by movchan on 2010-05-15
So i think my problem might be that once the ETH0 is plugged in it takes over as the DG (UG) how do i change this to use the wireless instead?

---

