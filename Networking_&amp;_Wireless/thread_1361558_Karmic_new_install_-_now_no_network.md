---
title: "Karmic new install - now no network"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by oygle on 2009-12-22
I did have Ubuntu 9.04 on a 64 bit computer. Networking worked okay, internet was via the ethernet, using another computer as a gateway.

I did a clean install of 9.10 on that computer (reformat hdd), and now there is no ethernet, details as follows:

1. Syslog details

> 
Dec 22 19:37:29 asus64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 22 19:37:34 asus64 kernel: [   23.143766] eth0: no IPv6 routers present
Dec 22 19:37:36 asus64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 22 19:37:46 asus64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 22 19:38:01 asus64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Dec 22 19:38:10 asus64 NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Dec 22 19:38:10 asus64 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1086
Dec 22 19:38:10 asus64 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Dec 22 19:38:10 asus64 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Dec 22 19:38:10 asus64 NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Dec 22 19:38:10 asus64 NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Dec 22 19:38:10 asus64 NetworkManager: <info>  Activation (eth0) failed.
Dec 22 19:38:10 asus64 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Dec 22 19:38:10 asus64 NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Dec 22 19:38:10 asus64 NetworkManager: <info>  (eth0): deactivating device (reason: 0).


2. Network manager details

> 
network manager icon says 'no network connection'

network connections shows ....

wired tab - auto eth0

Ipv4 settings - Automatic (DHCP) - with everything grayed out


3. **ethtool eth0**

> 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x00000000 (0)
	Link detected: yes


4. **ifconfig**

> 
eth0      Link encap:Ethernet  HWaddr 00:22:15:39:e2:01  
          inet6 addr: fe80::222:15ff:fe39:e201/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


5. **hostname -i**

> 
127.0.1.1


6. **lspci**

> 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
05:01.0 Communication controller: Agere Systems LT WinModem (rev 02)


7. **cat /etc/hosts**

> 
127.0.0.1	localhost
127.0.1.1	asus64

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


8. **cat /etc/network/interfaces**

> 
auto lo
iface lo inet loopback


Now, what changes do I make in Network manager, to define an IP address of the format 192.168.1.nnn for this computer, and how do I get the ethernet/network working again, with a gateway to another IP address (same network).

The motherboard is a ASUS P5QL PRO, and the lan is a PCIe Gigabit LAN controller featuring AI NET2 (on boot it says Marvell).

Thanks,

Oygle

---

### Post by oygle on 2009-12-22
Does anyone know the answer to this problem please ?

Oygle

---

### Post by oygle on 2009-12-22
I notice from [Wired (LAN)]("https://help.ubuntu.com/9.10/internet/C/connecting-wired.html#connecting-wired-manual") - step 5 "Click the IPv4 tab."

The gateway computer is 192.168.1.100 , the computer where the ethernet is not working (new Karmic install) is 192.168.1.101

Do I just use the IPv4 tab to define the gateway computer only ?

Do I need to specify the DNS settings on the client computer ?  I can't see why I would need to, as the gateway computer has the DNS already specified, and it connects to the internet.

Do I need to specify an IP address somewhere, like in /etc/hosts ?

NetworkManager is lacking the capacity to set this all up, it seems.

Oygle

---

### Post by ankur1990 on 2009-12-22
not getting ur problem.....
u want to establish a ethernet connection if u r using a modem or something else?

---

### Post by oygle on 2009-12-22
Problem is as per thread title. Ethernet worked fine with 9.04. Did a fresh install of Karmic, and now have lost the ethernet connection.

Here are the computers ..

1. 192.168.1.100 - has 9.04, works fine, has ethernet and internet. This is the gateway computer

2. 192.168.1.101 - now has 9.10. No ethernet and no internet

Oygle

---

### Post by oygle on 2009-12-23
Used Network Manager applet, modified the IPv4 tab on the 'auto eth0', so that the gateway IP was defined, and the IP for the Karmic computer defined also.

Now I have at least eth0 up and going. I can ping to each computer okay, and ping to an IP on the net, however no domain names can be accessed.

Oygle

---

### Post by n5wy on 2009-12-23
It sounds like from your last post that you need to define a DNS server in the static address settings tab (IPv4 tab) for "Auto eth0" in Network Manager. You can define DNS servers for your ISP, or use public DNS servers such as Google, or OpenDNS. The addresses are 

8.8.8.8  for Google
208.67.220.220 for OpenDNS

Once you have these in there, then you should be able to resolve URL on the net.

---

### Post by ankur1990 on 2009-12-23
try sudo pppoeconf and configure it accordingly.........
note  down the keywrds for acessing it

---

### Post by oygle on 2009-12-23
Thanks n5wy, I defined the DNS from my ISP, and was able to resolve domain names, and access the internet okay.

---

