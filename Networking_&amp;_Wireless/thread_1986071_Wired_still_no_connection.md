---
title: "Wired still no connection"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by chahat on 2012-05-24
I am having problems in connecting to internet.i have installed ubuntu 12.04 and even when my ethernet cable is connected,it says that the wired connection is disconnected,and i am offline.I haven't done any internet connection setup as of now.I have a broadband connection.
Here are the ifconfig -a results:

eth0 Link encap:Ethernet HWaddr 00:24:54:82:bf:bc 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:18 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:1312 (1.3 KB) TX bytes:1312 (1.3 KB) 

wlan0 Link encap:Ethernet HWaddr f0:7b:cb:6e:b3:ab 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 


Here is the result of sudo lshw -C network:

*-network 
description: Wireless interface 
product: AR9285 Wireless Network Adapter (PCI-Express) 
vendor: Atheros Communications Inc. 
physical id: 0 
bus info: pci@0000:05:00.0 
logical name: wlan0 
version: 01 
serial: f0:7b:cb:6e:b3:ab 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=ath9k driverversion=3.2.0-23-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
resources: irq:16 memory:f0100000-f010ffff 
*-network 
description: Ethernet interface 
product: 88E8040 PCI-E Fast Ethernet Controller 
vendor: Marvell Technology Group Ltd. 
physical id: 0 
bus info: pci@0000:09:00.0 
logical name: eth0 
version: 00 
serial: 00:24:54:82:bf:bc 
capacity: 100Mbit/s 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
resources: irq:44 memory:f0200000-f0203fff ioport:2000(size=256) 

Please help me in connecting to internet,as i want some important updates urgently,thanks.

---

### Post by kc1di on 2012-05-24
can you go to a terminal and type the following commands
and list the results here.

I know you don't have internet on that machine 
but copy the results to a text file and past them in the machine your online with so we can see the output -Will try to help.

```
lspci -nn | grep -e 0200 -e 0280
rfkill list all
lsb_release -d
```

---

### Post by chahat on 2012-05-24
Here is the result:
chahat@chahat-N148-N208:~$ lspci -nn | grep -e 0200 -e 0280 
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01) 
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] 
chahat@chahat-N148-N208:~$ rfkill list all 
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
chahat@chahat-N148-N208:~$ lsb_release -d 
Description:	Ubuntu 12.04 LTS 

Please help.
Regards,Chahat

---

### Post by kc1di on 2012-05-24
I'm not sure what's missing with the Lan connection yet.
do you have wireless available?

If so here's a page the may help you get the wireless card going.
[Atheros Communications Inc. AR9285 Wireless]("Atheros Communications Inc. AR9285 Wireless")

Also found this hint that may be why your lan connection is not working .
worth a try.

"It is likely that the network-manager state got corrupted. Open the file /var/lib/NetworkManager/NetworkManager.state. It should look something like this:

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
Change any from 'false' to 'true' to re-enable networking. It may work better if you first stop NetworkManager:

sudo stop network-manager

And start it again once done.. Or reboot"

---

### Post by chahat on 2012-05-24
Thanks for the reply.Will try it.

Regards,Chahat.

---

### Post by chahat on 2012-05-25
Could you please tell how do i open the aforesaid file? I am an absolute beginner.
Thanks.

---

### Post by kc1di on 2012-05-25
> **chahat said:**
> Could you please tell how do i open the aforesaid file? I am an absolute beginner.
Thanks.

to to a teminal and type the following

```
sudo gedit
```
that should bring up gedit in root mode.
 then navigate to the ```
/var/lib/NetworkManager/NetworkManager.state
```file and look and see if it has any false entries.  if so change them to true.

save and reboot.
try again.

---

