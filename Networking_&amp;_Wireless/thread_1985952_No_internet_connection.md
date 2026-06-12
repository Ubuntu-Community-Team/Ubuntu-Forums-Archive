---
title: "No internet connection"
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

Please help me in connecting to internet,as i want some important updates urgently,thanks.

---

### Post by papibe on 2012-05-24
Hi chahat.

Could you post the result of this command?
```
sudo lshw -C network
```
Regards.

---

### Post by chahat on 2012-05-24
Thanks for the quick reply.
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

I am clueless please help,thanks.

---

### Post by papibe on 2012-05-24
Let's solve one interface at a time.

Connect your ethernet cable and run:
```
sudo service network-manager restart
```
If that not fix the problem, please post the result of this command:
```
lsmod | grep -i sky2
```
sky2 is your ethernet driver, and the command check if it is loaded. If the last command returns nothing, do this to load the driver:
```
sudo modprobe sky2
```
If that is successful, run again:
```
sudo service network-manager restart
``` 

Tell us how it goes.
Regards.

---

### Post by chahat on 2012-05-24
Thanks for the quick reply.
The first command didn't work(still offline).
The result of the second command was:

sky2                   53628  0 

This probably means that the driver is loaded(also, I could connect to internet from windows in the same netbook earlier.).But then what could be the problem?

Please help,thanks.

---

### Post by papibe on 2012-05-24
Could you post the result of these other commands?
```
dmesg | grep -i sky2

sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
Regards.

---

### Post by chahat on 2012-05-25
Thanks for the time you are giving here.Here are the results of the aforesaid commands:

> chahat@chahat-N148-N208:~$ dmesg | grep -i sky2 
[    1.721028] sky2: driver version 1.30 
[    1.721157] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    1.721222] sky2 0000:09:00.0: setting latency timer to 64 
[    1.721368] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0 
[    1.721977] sky2 0000:09:00.0: irq 44 for MSI/MSI-X 
[    1.724287] sky2 0000:09:00.0: eth0: addr 00:24:54:82:bf:bc 
[   15.774882] sky2 0000:09:00.0: eth0: enabling interface 
[   66.064404] sky2 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both 
chahat@chahat-N148-N208:~$ sudo ifconfig eth0 down 
[sudo] password for chahat: 
chahat@chahat-N148-N208:~$ sudo ifconfig eth0 up 
chahat@chahat-N148-N208:~$ 

I would like to add(is it too late?) that i didn't enter any ip or gateway address after installation.Am i supposed to do that ? If yes,how do i do that?

Thanks.

---

