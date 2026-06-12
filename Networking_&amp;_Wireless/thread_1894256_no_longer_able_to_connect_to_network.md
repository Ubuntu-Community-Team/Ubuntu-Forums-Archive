---
title: "no longer able to connect to network"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by blucalculatr on 2011-12-12
Hi everyone, first post

Okay, so i have ubuntu server 11.10, its been working since i downloaded it however many months ago, but all of a sudden it cant connect to the network. so i tried installing a new network card. that didnt help. i got out my usb which had ubuntu 10.04 (normal version, with gui and stuff), and it connected to the internet straight away, no problems.

also, on startup, "The disk drive for /dev/mapper/matt--server2-swap1 is not ready yet or not present." pops up, tries to do a pile of things "stopping cold plug devices, stopping log initial device creation starting enable boot-time encrypted block devices" etc, and then waits for 60 seconds for network configuration, and says continuing without network configuration.

ifconfig returns
> 
eth0	Link encap:Ethernet  HWaddr 00:11:2f:5f:cb:c6
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
	Interrupt19 Base address:0xb400

and then lo and virbr0. will type them up if needed.


cat /etc/resolv.conf returns
> 
domain BigPond
search BigPond
nameserver 10.0.0.138

10.0.0.138 is my router

cat /etc/network/interfaces
> 
#<description of the file>

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


cat /etc/udev/rules.d/70-persistent-net.rules
> 
#<description of the file>

#PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net, ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:2f:6f:cb:c6", ATTR{dev_id}==0x0", ATTR{TYPE}=="1", KERNEL=="eth*", NAME="eth0"

#PCI device 0x1814:0x0302 (rt61pci)
SUBSYSTEM=="net, ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:5a:08:9e:65", ATTR{dev_id}==0x0", ATTR{TYPE}=="1", KERNEL=="wlan*", NAME="wlan0"

#PCI device 0x13f0:0x1023 (Sundance Technology IPG Triple-Speed Ethernet)
SUBSYSTEM=="net, ACTION=="add", DRIVERS=="?*", ATTR{address}=="20:cf:30:d6:fd:16", ATTR{dev_id}==0x0", ATTR{TYPE}=="1", KERNEL=="eth*", NAME="eth1"


lspci -nnk | grep -iA2 net
> 
02:0a.0 Ethernet controller [0200] Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet [13f0:1023] (rev 41)
        Subsystem: ASUSTeK Computer Inc. NX1101 [1043:8180]
        Kernel driver in use: Sundance Technology IPG Triple-Speed Ethernet
        Kernel modules: ipg
02:0e.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]
--
02:0f.0 Ethernetcontroller 0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
        Subsystem: ASUSTeK Computer Inc. Device [1043:80b3]
        Kernel driver in use: 8139too


lsmod | grep 81
> 
ip_tables 18106  3 iptable_nat,iptable_mangle,iptable_filter
stp       12811  1 bridge
8139too   23283  0
8139cp    26762  0


Can i please get some help to try and get back on my network?

EDIT1: typed the output of 
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
lspci -nnk | grep -iA2 net

EDIT2: typed out lsmod | grep 81

---

### Post by praseodym on 2011-12-12
Hi,

please show:

```
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by blucalculatr on 2011-12-12
cat /etc/network/interfaces
> 
#<description of the file>

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


cat /etc/udev/rules.d/70-persistent-net.rules
> 
#<description of the file>

#PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net, ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:2f:6f:cb:c6", ATTR{dev_id}==0x0", ATTR{TYPE}=="1", KERNEL=="eth*", NAME="eth0"

#PCI device 0x1814:0x0302 (rt61pci)
SUBSYSTEM=="net, ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:5a:08:9e:65", ATTR{dev_id}==0x0", ATTR{TYPE}=="1", KERNEL=="wlan*", NAME="wlan0"

#PCI device 0x13f0:0x1023 (Sundance Technology IPG Triple-Speed Ethernet)
SUBSYSTEM=="net, ACTION=="add", DRIVERS=="?*", ATTR{address}=="20:cf:30:d6:fd:16", ATTR{dev_id}==0x0", ATTR{TYPE}=="1", KERNEL=="eth*", NAME="eth1"


lspci -nnk | grep -iA2 net
> 
02:0a.0 Ethernet controller [0200] Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet [13f0:1023] (rev 41)
        Subsystem: ASUSTeK Computer Inc. NX1101 [1043:8180]
        Kernel driver in use: Sundance Technology IPG Triple-Speed Ethernet
        Kernel modules: ipg
02:0e.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]
--
02:0f.0 Ethernetcontroller 0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
        Subsystem: ASUSTeK Computer Inc. Device [1043:80b3]
        Kernel driver in use: 8139too


lsmod
uh, thats a LOT of stuff to type out. any particular bits of info that'll be useful?


also, updated original post

---

### Post by Bucky Ball on 2011-12-12
Why not paste it? Ctrl/Shift C to copy in a terminal and paste in here.

---

### Post by blucalculatr on 2011-12-12
because its on a different computer.

---

### Post by praseodym on 2011-12-12
Check with

```
lsmod | grep 81
```

if two modules are loaded (8130too and 8139cp)

---

### Post by blucalculatr on 2011-12-12
lsmod | grep 81

Module ... Size ... Used by
> 
ip_tables 18106  3 iptable_nat,iptable_mangle,iptable_filter
stp       12811  1 bridge
8139too   23283  0
8139cp    26762  0


---

### Post by praseodym on 2011-12-12
Blacklist the wrong one:

```
echo "blacklist 8139cp" | sudo tee /etc/modprobe.d/blacklist-8139cp.conf
sudo modprobe -rfv 8139cp 8139too
sudo modprobe -v 8139too
```

---

### Post by blucalculatr on 2011-12-12
just for a better understanding (i'm an amateur), how do we know its the wrong one, and what does blacklisting do?

bonus points: what is it?

---

### Post by praseodym on 2011-12-12
> **blucalculatr said:**
> just for a better understanding (i'm an amateur), how do we know its the wrong one, and what does blacklisting do?

bonus points: what is it?

Blacklisting prevents the wrong driver being loaded at boot-up. Wrong one: experience ;-)

2 drivers normally dont work in parallel

---

### Post by blucalculatr on 2011-12-12
ohyeah, that just reminded me of some probably crucial information. some messages come up on startup, i'll try and write it down.

edit: got it! 
The disk drive for /dev/mapper/matt--server2-swap1 is not ready yet or not present.

adding to original post.

---

### Post by blucalculatr on 2011-12-12
okay, so done the steps to blacklist like you said, still not working. What else can i try?

---

### Post by blucalculatr on 2011-12-30
Bump. Anyone else got suggestions?

---

### Post by AMusingFool on 2011-12-30
> **blucalculatr said:**
> because its on a different computer.

Just as a future possibility, you could use a thumb drive to copy over the files/outputs, or go to the forums from that computer when you booted up with the thumb drive.

Sorry, I have nothing substantive to answer the original question, though.  Good luck.

---

### Post by blucalculatr on 2011-12-30
well, when booting from the thumb drive, i cant access the server's files. when booting from the server, i cant mount USB or access the network.

---

