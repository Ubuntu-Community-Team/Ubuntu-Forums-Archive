---
title: "No network connection"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by paulXPS on 2010-11-23
[B]The problem I have is when I install 10.10 I get no wired connection my wifi works great, just no wired connection. I dont have wifi where I am right now. It works fine when I run off the dvd , but when I install it i get nothing. I have tried static ip, reinstalling, reinstalling drivers. Don't know what else to do. If anyone has any ideas on how to solve this problem I would  be thankful.

 I have a Dell Inspiron 1720
  the ethernet is a broadcom 440x
[/B]

---

### Post by uncaspi on 2010-11-23
Will you please post the content of sudo /sbin/ifconfig

---

### Post by paulXPS on 2010-11-23
eth1        Link encap:Ethernet    HWaddr  00:1e:4c:c1:cd:47
              inet6 addr:  fe80::21e:4cff:fec1:cd47/64 Scope:Link
              UP BROADCAST MULTICAST   MTU:1500   METRIC:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)
              Interrupt:17 Base address:0xc000

  lo          Link encap:Local Loopback
               inet addr:127.0.0.1  Mask:255.0.0.0
               inet6 addr: ::1/128 Scope:Host
               UP LOOPBACK RUNNING  MTU:16436  METRIC:1
               RX packets:1008 errors:0 dropped:0 overruns:0 frame:0
               TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:0
               RX bytes:78768 (78.7 KB)  TX bytes:78768 (78.7 KB)

---

### Post by uncaspi on 2010-11-23
Will you please post the content of sudo /sbin/iwconfig
and sudo lshw -C Network

---

### Post by paulXPS on 2010-11-23
eth1          IEEE 802.11bg  ESSID:""
                Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
                Bit Rate:54 Mb/s   Tx-Power:24 dBm
                Retry min limit:7   RTS thr:ff   Fragment thr:ff
                Encryption key:ff
                Power Management:ff
                Link Quality=5/5  Signal level=0 dBm  Noise level=-97 dBm
                Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by uncaspi on 2010-11-23
Will you please post the content of /etc/network/interfaces

Your wireless card is called eth1 and there should be and eth0 for your ethernet. Do you run VMware? Will you please post sudo lshw -C network

---

### Post by paulXPS on 2010-11-23
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:4c:c1:cd:47
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.11 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:fe5fe000-fe5f




No I dont use VMware. permission denied when I put this in  /etc/network/interfaces.

---

### Post by uncaspi on 2010-11-24
Your Ethernet card have not got a logical name such as eth0. Please post the content of dmesg | grep net

You should not put anything in /etc/network/interfaces but only post the content of the file.

---

### Post by paulXPS on 2010-11-24
/etc/network/interfaces    is   auto  lo
                                           iface lo inet loopback


dmesg | grep net is
  Usage: dmesg [-c] [-n level] [-r] [-s bufsize]

---

### Post by uncaspi on 2010-11-24
Is it 10.10 (64 bit) you have installed? Which kernel do you use?
uname -r

---

### Post by paulXPS on 2010-11-24
It's 32 bit 2.6.35-22- generic

---

### Post by uncaspi on 2010-11-24
Ok you are probably missing a line for eth0 in

/etc/udev/rules.d/70-persistent-net.rules

Here is the content of mine. I have 3 cards. eth0,eth1 and eth2.
You must add the line containing eth0 and put in yours PCI device code and ATTR{address} which is the MAC address (found when you boot into windows and edit network somewhere) 

# PCI device 0x10de:0x0066 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:2f:49:96:6b", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:10:a7:10:65:d6", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14b9:0x4800 (airo)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:40:96:28:a4:f3", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"



You can log in as su in ubuntu to edit the file or 
sudo nano /etc/udev/rule.d/70-persistent-net.rules

After you've done the changes save the file (Ctrl-o) and reboot.
Check now with sudo /sbin/ifconfig if you have eth0.

If you don't find the PCI device code numers try lspci -nn before you edit the file.

---

### Post by uncaspi on 2010-11-24
If you don't have windows partition you can boot from your live CD and try to locate the file and copy it to the directory I mentioned.

---

### Post by paulXPS on 2010-11-24
I found the file and Here's what my file /etc/udev/rules.d/70-persistent-net.rules reads.

#PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add', Drivers=="?",  ATTR{address}=="00:1d:09:c7:a4:3f", ATTR{dev_id}=="0x0",  ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


#PCI device 0x14e4:0x4315 ()
SUBSYSTEM=="net", ACTION=="add', Drivers=="?",   ATTR{address}=="00:1e:4c:c1:cd:47", ATTR{dev_id}=="0x0",  KERNEL=="eth*", NAME="eth1"


Haven't done anything yet

---

### Post by uncaspi on 2010-11-24
Ok. I looks ok to me. Nothing to edit. Then I don't know what  to do.

---

### Post by uncaspi on 2010-11-24
Looks ok to me. Nothing to edit.

---

### Post by bkratz on 2010-11-24
Sorry to interrupt, but when you were enabling the STA driver for the wireless card, did you follow some set of instructions that may have said to "blacklist b43, b44 and ssb"?

The ethernet controller you are using requires b44 and ssb.

---

### Post by paulXPS on 2010-11-24
When I activated the sta driver it didnt say anything about a blacklist..How to I check to see if it put the b43 and b44 on the blacklist?

---

### Post by bkratz on 2010-11-24
> **paulXPS said:**
> When I activated the sta driver it didnt say anything about a blacklist..How to I check to see if it put the b43 and b44 on the blacklist?



No this would have been something you did.

---

### Post by paulXPS on 2010-11-24
OK I just reinstalled 10.10 and have not done nothing and still it doesnt auto detect my ehternet only driver option it gives me is the sta wireless driver..

---

### Post by bkratz on 2010-11-24
The drivers for the ethernet device ( this system has the same chipset) do not require the user to download anything. If you go to Applications>>Accessories>>Terminal (this is the terminal) and enter in 

lsmod

that is LSMOD in lowercase, do you see the modules listed for b44 and ssb?
The reason being that when you did the driver install for STA you must have been connected to the internet through ethernet to get them. At least that is the easiest way!

If you don't see them you might copy/paste the output back here.

---

