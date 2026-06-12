---
title: "Wireless Driver help"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Nick Powers on 2009-05-17
[SIZE=3]I just installed it last night... and spent all of today trying to get the wireless internet to connect. [/SIZE]
[SIZE=3]To start off, I couldn't connect through Network manager... So I looked it up and now I have ndisgtk and ndiswrapper. I also have Wifi Radar.[/SIZE]
 
[SIZE=3]I have a Vista and XP partition which I am using now, but I installed Wifi radar through USB, then ran it in terminal "sudo wifi-radar" and i found my connection, configured it, and pressed connect...[/SIZE]
[SIZE=3]It started to connect and then said "aquiring IP" for a few seconds then came "Cannot aquire IP"[/SIZE]
[SIZE=3]So there is my main problem right now, I would use ndisgtk to install a wireless driver BUT I have NO clue where to get the .inf file for my specific driver...[/SIZE]
 
 
 
[SIZE=3]My wireless card = Atheros AR5006x[/SIZE]
 
[SIZE=3]If you need any other details, please let me know.[/SIZE]
[SIZE=3]Thanks [/SIZE]
 
[SIZE=3]P.S. If I said something above that doesn't make much sense... it's probably because when it comes to Linux I have no clue what I am talking about.[/SIZE]
 
[SIZE=3][EDIT] I have installed and tried "madwifi", no luck.[/EDIT][/SIZE]

---

### Post by Peter09 on 2009-05-17
Can you post the output of

```
lshw -C network
```
and
```
ifconfig
```

---

### Post by drpjkurian on 2009-05-17
Hi Nick you can give a try by installing madwifi driver for atheros wifi card.
the instructions are given as 
1. ```
sudo nano /etc/apt/sources.list

```
2. ```
sudo apt-get update && sudo apt-get upgrade
```

3. ```
sudo apt-get install build-essential libssl-dev
```

4. ```
sudo apt-get install linux-headers-`uname -r`
```

5.```
 sudo apt-get install subversion
```

6. ```
sudo -i
```

7. ```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```

8. ```
cd madwifi-ng

```
9. ```
make && make install
```

10. ```
echo ath_pci >> /etc/modules
```

well reboot your machine it should work

Regards
dr kurian

---

### Post by Peter09 on 2009-05-17
Cannot aquiire IP sounds like your network is trying to connect, while Dr Kurian has a valid solution it is worth just pursuing why you are not connecting to your router. Please out put the information requested - also have you a router or modem, is your router configured for DHCP?

---

### Post by Nick Powers on 2009-05-17
> **Peter09 said:**
> Can you post the output of
 
```
lshw -C network
```
and
```
ifconfig
```
 
Hey Peter, 
here's the output I recieved when inserting those two codes into my terminal.
 
 
```
lshw -C network
```
*-network 
description: Wireless interface
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:04:00.0
logical name: wifi0
version: 01
serial: 00:19:7e:8a:2f:c7
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth0
version: 01
serial: 00:16:d4:ff:50:5e
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: e2:4b:2a:bc:c2:c1
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
 
```
ifconfig
```
ath0 Link encap:Ethernet HWaddr 00:19:7e:8a:2f:c7 
inet6 addr: fe80::219:7eff:fe8a:2fc7/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
eth0 Link encap:Ethernet HWaddr 00:16:d4:ff:50:5e 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:252 Base address:0xa000 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
wifi0 Link encap:UNSPEC HWaddr 00-19-7E-8A-2F-C7-00-00-00-00-00-00-00-00-00-00 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:198303 errors:0 dropped:0 overruns:0 frame:12593
TX packets:1634 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:199 
RX bytes:22251053 (22.2 MB) TX bytes:75164 (75.1 KB)
Interrupt:17

---

### Post by Nick Powers on 2009-05-17
> **drpjkurian said:**
> Hi Nick you can give a try by installing madwifi driver for atheros wifi card.
the instructions are given as 
1. ```
sudo nano /etc/apt/sources.list

```
2. ```
sudo apt-get update && sudo apt-get upgrade
```
 
3. ```
sudo apt-get install build-essential libssl-dev
```
 
4. ```
sudo apt-get install linux-headers-`uname -r`
```
 
5.```
 sudo apt-get install subversion
```
 
6. ```
sudo -i
```
 
7. ```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```
 
8. ```
cd madwifi-ng

```
9. ```
make && make install
```
 
10. ```
echo ath_pci >> /etc/modules
```
 
well reboot your machine it should work
 
Regards
dr kurian
 
 
Hey Dr. Kurian,
 
Thanks for the advice but I already have madwifi installed, and have tried Activating, Deactivating, Rebooting... the whole 9 yards.
 
Thanks again though.

---

### Post by Peter09 on 2009-05-17
Can you show the contents of the file

> /etc/network/interfaces

---

### Post by Nick Powers on 2009-05-17
> **Peter09 said:**
> Can you show the contents of the file
 
contents of file ```
etc/network/interfaces
``` is:
 
auto lo
iface lo inet loopback

---

### Post by Peter09 on 2009-05-18
I have looked at your config, to me, you seem to have wifi up and running and it is transmitting and receiving but you have no IP address. 
What is the configuration of you wireless router, is DHCP  enabled on your router? Have you any other devices which are connecting?

---

### Post by Nick Powers on 2009-05-18
> **Peter09 said:**
> I have looked at your config, to me, you seem to have wifi up and running and it is transmitting and receiving but you have no IP address. 
What is the configuration of you wireless router, is DHCP enabled on your router? Have you any other devices which are connecting?
 
Yes I can fully scan for networks and connect and everything, it basically just won't "Aquire the IP" and also I don't have router access through the browser, but it says I am connected...
 
Anyways, to answer your question about DHCP enabled router, I have no clue, I have a Linksys router so how would I go about doing that?
And to answer your other question, yes I can connect perfectly on Windows XP and Vista partitions of my harddrive.

---

### Post by Nick Powers on 2009-05-18
> **Peter09 said:**
> I have looked at your config, to me, you seem to have wifi up and running and it is transmitting and receiving but you have no IP address. 
What is the configuration of you wireless router, is DHCP enabled on your router? Have you any other devices which are connecting?
 I take that back, I logged into my router and at the top it said "Automatic Configuration - DHCP"
So apparently I am DHCP configured as far as that goes, sounds like we are running out of options fast.

---

### Post by Peter09 on 2009-05-18
Can you try the following command in a terminal

```
sudo route add default gw <your routers IP address> wifi0
```

---

### Post by Nick Powers on 2009-05-18
> **Peter09 said:**
> Can you try the following command in a terminal
 
```
sudo route add default gw <your routers IP address> wifi0
```
 
Here is what I got when I typed that into my terminal... 
```
nick@ubuntu:~$ sudo route add default gw 192.168.1.1 wifi0
[sudo] password for nick: 
SIOCADDRT: No such process
```
 
So that didn't seem to work out, also, when I attempt to connect through wifi-radar... this is what I get in the terminal window.
```

wifi0: unknown hardware address type 801
can't create /var/run/dhclient.ath0.leases: Permission denied
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7e:8a:2f:c7
Sending on LPF/ath0/00:19:7e:8a:2f:c7
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12

```And right as soon is that is done after about... 5 seconds it says that it cannot obtain and IP.Hope that is of more help possibly.

---

### Post by Peter09 on 2009-05-19
Try

```
sudo route add default gw 192.168.1.1 ath0

```

You most probably need to run wifi-radar with sudo from a terminal.

---

### Post by Nick Powers on 2009-05-19
> **Peter09 said:**
> Try
 
```
sudo route add default gw 192.168.1.1 ath0

```
 
You most probably need to run wifi-radar with sudo from a terminal.
 
 
Ok, well I have been running wifi-radar through terminal, won't let me run it through it's icon for some reason... but I tryed the code to you me, this is what I got.
```

nick@ubuntu:~$ sudo route add default gw 192.168.1.1 ath0
[sudo] password for nick: 
SIOCADDRT: No such process

```

---

### Post by Nick Powers on 2009-05-20
UPDATE: I was messing with wifi-radar, and manually configured it to assign me an IP... and it gave me the IP finally, but STILL NO INTERNET =(

---

### Post by Nick Powers on 2009-05-22
WELL GOODBYE LINUX! I couldn't resolve my problem, after about two weeks... I just said screw it, I'll put Windows 7 in it's place and maybe I can get it's wireless internet working...

---

