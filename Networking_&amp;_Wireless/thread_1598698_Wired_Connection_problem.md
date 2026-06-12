---
title: "Wired Connection problem"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by boydude on 2010-10-16
i'm a beginner to linux but will explain the problem i'm having

having upgrade from 10.04 to 10.10 i am unable to connect to my network. (all instances below is wired)

i have a cable connection which is shared via a router. when i login to ubuntu it tried to search for the network but then gives up saying network is disconnected.

if i connected directly from my pc to my modem i am able to surf on the net. i've tried rebooting my router & modem and updating the linux drivers for my network card (intel 82566dc)but to still no avail i am not able to connect to the router.

can anyone help?

p.

---

### Post by garvinrick4 on 2010-10-16
You have right clicked on applet and enabled your wireless? When you left click on
applet does it give you choices of routers it finds? Right click edit connections to wireless
highlight to edit and make sure connect automatically. Is anything at all in:below
```
gedit /etc/resolv.conf
```What about 
```
ifconfig
```does it show a functioning envirement (above)
[FONT=monospace]```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```[/FONT]they all say true (above)

---

### Post by boydude on 2010-10-16
i thought i may have messed some setting up so i just did a fresh install and getting the same problem

if i do 'router -n' i got destination as 169.254.0.0 and genmask as 255.255.0.0

ifconfig
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:80:c6:08  
          inet6 addr: fe80::219:d1ff:fe80:c608/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31798 (31.7 KB)  TX bytes:16081 (16.0 KB)
          Interrupt:21 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55264 (55.2 KB)  TX bytes:55264 (55.2 KB)




```

resolv.conf and NetworkManger.state are blank

---

### Post by garvinrick4 on 2010-10-16
Run this and copy and paste results, Highlight whole thing and hit # sign in upper corner
of Message box and will put in nice scroll box. This just tells all about your system so other users
can see if they have same card or cards and maybe can help. A little much but gives all anyone would want.
```
sudo lspci -v | less
```

---

### Post by boydude on 2010-10-16
I have a Dlink Dir-615 Router running the latest DDWRT firmware. NIC is a on-board Intel 82566dc


```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Dell Device 01db
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dfd00000-dfefffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
        Subsystem: Dell Device 01db
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at dffe0000 (32-bit, non-prefetchable) [size=128K]
        Memory at dffdb000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ecc0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: e1000e
        Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ff20 [size=32]
        Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff00 [size=32]
        Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at dffdac00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 01db
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
 Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: dfc00000-dfcfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0200000-d03fffff
        Prefetchable memory behind bridge: 00000000d0400000-00000000d05fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at ff80 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff60 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff40 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: d8000000-dfbfffff
        Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: d8000000-dfbfffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Dell Device 01db
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at fe00 [size=8]
        I/O ports at fe10 [size=4]
        I/O ports at fe20 [size=8]
        I/O ports at fe30 [size=4]
        I/O ports at fec0 [size=16]
        I/O ports at eca0 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Device 01db
        Flags: medium devsel, IRQ 10
        Memory at dffdab00 (32-bit, non-prefetchable) [size=256]
        I/O ports at ece0 [size=32]
        Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Dell Device 01db
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at fe40 [size=8]
        I/O ports at fe50 [size=4]
        I/O ports at fe60 [size=8]
        I/O ports at fe70 [size=4]
        I/O ports at fed0 [size=16]
        I/O ports at ecb0 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series] (prog-if 00 [VGA controller])
        Subsystem: XFX Pine Group Inc. Device 2990
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dfde0000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at dc00 [size=256]
        Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: radeon
        Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
        Subsystem: XFX Pine Group Inc. Device aa58
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at dfddc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

02:00.0 Multimedia video controller: Micronas Semiconductor Holding AG Device 0720
        Subsystem: Avermedia Technologies Inc Device 032e
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at dfce0000 (32-bit, non-prefetchable) [size=64K]
        Memory at dfcf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

04:04.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs X-Fi XtremeMusic
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at cce0 [size=32]
        Memory at dfa00000 (64-bit, non-prefetchable) [size=2M]
        Memory at d8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: SB-XFi
        Kernel modules: snd-ctxfi

(END) 


```

---

### Post by boydude on 2010-10-16
gksudo ...NetworkManager.state

```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


```

---

### Post by boydude on 2010-10-16
I've got this working, but think this maybe some sort of bug.

I turned unticked 'Connect Automatically' in network manager and rebooted when I was back on desktop I clicked on **Auto Eth0** in the network dropdown list and it connected.

---

### Post by garvinrick4 on 2010-10-16
Mark as Solved please.
As long as your running that is what counts. Users who know a lot about Network connections are far and few between and I am not one of them. Just know how to look
at the obvious. So many cards and drivers out there. Glad you are up and running.

---

### Post by boydude on 2010-10-17
guess i spoke to early, 1 reboot later and it loss connection again, did what i did before but it doesnt work, keep getting that network disconnected message (arrghhhh)it's really driving me up the wall. its 6am now been up all night trying to fix this will try again later on.

---

### Post by boydude on 2010-10-17
bump

---

### Post by garvinrick4 on 2010-10-17
Have asked a user by the name of darkstaar to help out if she can.

---

### Post by darkstaar on 2010-10-17
I wish I *could* be of assistance but I haven't used an Ethernet connection in many years, the last time running Mandrake 8.0 or something like that. I ditched my last desktop machine after that and I've been using strictly laptops & WiFi ever since.

Sorry that I can't be of more help.

All the best.

---

### Post by garvinrick4 on 2010-10-17
boydude I found darkstaar by noticing on these forums who seems to
be able to help in certain fields, like networking, grub, installation and so on. Did not think about wired and wireless, so if you want to hurry it up look around and see who you can ask or wait patiently for someone with wired knowledge to see this. People are here to help so do not feel shy about asking.

---

### Post by boydude on 2010-10-17
thanks for trying garvinrick & Darkstar.

do you think i should remove the network manager applet and possibly try another?

---

### Post by garvinrick4 on 2010-10-17
> **boydude said:**
> thanks for trying garvinrick & Darkstar.

do you think i should remove the network manager applet and possibly try another?
It worked during one session you had, seems to be a setting somewhere.

---

### Post by btindie on 2010-10-17
Firstly start off by checking the physical network connection - check that the cable is connected correctly and the LED indicating a connection is on.

Install ethtool ```
sudo apt-get install ethtool
``` then run ```
sudo ethtool
``` what is the output? Does it say link detected at the bottom??

From the output of *ifconfig* you gave earlier it appears that your NIC is detected and that is not where the problem is.

You can bypass Network Manager and manually give it an IP address to test the connectivity so you can eliminate that. What's the IP address of your router? For the below I will assume it's 192.168.1.1, change that to the correct address. And I will give your computer an IP address of 192.168.1.100, you'll also need to change that if your router is using a different IP address. For example if your router is on 192.168.0.254 then use 192.168.0.x where 'x' is a number between 1 and 253.
```
sudo ip addr flush dev eth0
sudo ip link set eth0 up
sudo ip addr add 192.168.1.100/24 dev eth0
```Then test your setup with ```
ping 192.168.1.1
``` you should get a response (exit with Ctrl-C).

If that works then your physical network is fine. There may be a problem with Network Manager or your DHCP server if it's not getting an IP address from it. If you are using DHCP on your network you can test it with this. First clear the IP configuration ```
sudo ip addr flush dev eth0
``` Then try to obtain an IP address via DHCP ```
sudo dhclient eth0
``` does that obtain a lease? (Ctrl-C again if it takes to long) If that obtained an IP address you can test it with the ping command again if you like.

If that lot all works then try removing your profile from Network Manager and creating a new one.

---

### Post by boydude on 2010-10-17
[IMG]http://img832.imageshack.us/img832/4354/79354209.png[/IMG]

this computer is dual booting with windows 7.

i get successful pings when i'm applying changes to my router otherwise i get destination host unreachable

i forgot to mention, my router clones the mac of my PC NIC, could this be the problem?

---

### Post by btindie on 2010-10-17
> **boydude said:**
> 
i've done the above command and so far i can see any ip now when i type ifconfig.
I don't quite understand what you're trying to say there...

From the screen capture I can see that you've got DHCP enabled for your LAN, when you run dhclient does it get an IP address?

Were you able to ping the router when you manually gave it an IP address?

Please provide the output from the commands you run if you've still got a problem.

---

### Post by btindie on 2010-10-17
Please post a new message and don't edit your current one as it makes it hard to keep track!

> **boydude said:**
> 
i get successful pings when i'm applying changes to my router otherwise i get destination host unreachable

i forgot to mention, my router clones the mac of my PC NIC, could this be the problem?
What changes have you made to your router? I didn't say anything about making any changes to it...

Also, what do you mean by your router is cloning the MAC of your computers NIC?? - Is that to do with the DHCP configuration.

---

### Post by boydude on 2010-10-17
sorry didnt mean to confuse you, in regards to the router stuff, i was just trying to give as much information as possible in case it maybe a setting on there which it doesnt like.

i cant install ethtool as i have no connect on the linux machine.

below is the commands you gave me:
```

viper@viper:~$ sudo ip addr flush dev eth0
viper@viper:~$ sudo ip link set eth0 up
viper@viper:~$ sudo ip addr add 192.168.1.106/24 dev eth0
viper@viper:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.106 icmp_seq=1 Destination Host Unreachable
From 192.168.1.106 icmp_seq=2 Destination Host Unreachable
From 192.168.1.106 icmp_seq=3 Destination Host Unreachable
From 192.168.1.106 icmp_seq=5 Destination Host Unreachable
From 192.168.1.106 icmp_seq=6 Destination Host Unreachable
From 192.168.1.106 icmp_seq=7 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_req=12 ttl=64 time=0.580 ms
64 bytes from 192.168.1.1: icmp_req=33 ttl=64 time=1001 ms
64 bytes from 192.168.1.1: icmp_req=40 ttl=64 time=0.513 ms
64 bytes from 192.168.1.1: icmp_req=48 ttl=64 time=0.506 ms
From 192.168.1.106 icmp_seq=83 Destination Host Unreachable
From 192.168.1.106 icmp_seq=84 Destination Host Unreachable
From 192.168.1.106 icmp_seq=85 Destination Host Unreachable
From 192.168.1.106 icmp_seq=86 Destination Host Unreachable
From 192.168.1.106 icmp_seq=87 Destination Host Unreachable
From 192.168.1.106 icmp_seq=88 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_req=89 ttl=64 time=2010 ms
64 bytes from 192.168.1.1: icmp_req=90 ttl=64 time=1010 ms
64 bytes from 192.168.1.1: icmp_req=91 ttl=64 time=11.0 ms
64 bytes from 192.168.1.1: icmp_req=92 ttl=64 time=0.513 ms
From 192.168.1.106 icmp_seq=127 Destination Host Unreachable
From 192.168.1.106 icmp_seq=128 Destination Host Unreachable
From 192.168.1.106 icmp_seq=129 Destination Host Unreachable
From 192.168.1.106 icmp_seq=130 Destination Host Unreachable
From 192.168.1.106 icmp_seq=131 Destination Host Unreachable
From 192.168.1.106 icmp_seq=132 Destination Host Unreachable
From 192.168.1.106 icmp_seq=134 Destination Host Unreachable
From 192.168.1.106 icmp_seq=135 Destination Host Unreachable
From 192.168.1.106 icmp_seq=136 Destination Host Unreachable
From 192.168.1.106 icmp_seq=137 Destination Host Unreachable
From 192.168.1.106 icmp_seq=138 Destination Host Unreachable
From 192.168.1.106 icmp_seq=139 Destination Host Unreachable
From 192.168.1.106 icmp_seq=141 Destination Host Unreachable
From 192.168.1.106 icmp_seq=142 Destination Host Unreachable
From 192.168.1.106 icmp_seq=143 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
145 packets transmitted, 8 received, +27 errors, 94% packet loss, time 144077ms
rtt min/avg/max/mdev = 0.506/504.543/2010.665/709.883 ms, pipe 4
viper@viper:~$ sudo ip addr flush dev eth0
viper@viper:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:19:d1:80:c6:08
Sending on   LPF/eth0/00:19:d1:80:c6:08
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
viper@viper:~$ 




```

---

### Post by btindie on 2010-10-17
OK, so when you manually configure it it gets intermittent connectivity. That would explain why it's unable to get an IP address via DHCP. Does it work fine in Windows? / Do you have another ethernet lead you could try? What about if you connect it to another port in your router??

Have you got a firewall running on it?? ```
sudo iptables -L
```

What is the MAC cloning you were talking about? - Why are you using it/what does it do??

If you make any changes then repeat the previous commands, if they return a positive result then all should be well.

---

### Post by boydude on 2010-10-17
MAC address cloning, as i'm on cable connection its assigned via mac address and in order to retain the same ip, i'd clone the nic cards ip.

in windows it runs fine. 
```
viper@viper:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


```

i'll try another rj45 now.

---

### Post by boydude on 2010-10-17
firewall deactivated on router, have tried another cable in another port on the router still the same problem.

---

### Post by btindie on 2010-10-17
> **boydude said:**
> MAC address cloning, as i'm on cable connection its assigned via mac address and in order to retain the same ip, i'd clone the nic cards ip.

in windows it runs fine. 
```
viper@viper:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


```i'll try another rj45 now.
I just found that about the MAC cloning, thought that might be the case, I had to do that when I was using cable. That however won't be the cause of your problem and it's not any firewall rules either.

As it runs fine in Windows then I can only think it may be the driver for your NIC. Which version of Ubuntu are you running? I can only think that it may be a problem with the kernel module for your NIC. What's the output of ```
dmesg | grep eth0
```

---

### Post by boydude on 2010-10-17
i had 10.04 prior to 10.10 and it was running perfect.
output
```

[ 1276.782938] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1277.300296] e1000e: eth0 NIC Link is Down
[ 1278.882896] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1278.882900] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1280.192015] e1000e: eth0 NIC Link is Down
[ 1281.780872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1281.780877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1284.620125] e1000e: eth0 NIC Link is Down
[ 1285.590007] eth0: no IPv6 routers present
[ 1286.220869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1286.220871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1287.772006] e1000e: eth0 NIC Link is Down
[ 1289.370872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1289.370875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1366.900129] e1000e: eth0 NIC Link is Down
[ 1368.722121] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1368.722125] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1383.900129] e1000e: eth0 NIC Link is Down
[ 1385.620873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1385.620877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1385.900127] e1000e: eth0 NIC Link is Down
[ 1387.590871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1387.590874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1388.900128] e1000e: eth0 NIC Link is Down
[ 1390.550868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1390.550872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1394.900127] e1000e: eth0 NIC Link is Down
[ 1396.770870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1396.770874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1396.900127] e1000e: eth0 NIC Link is Down
[ 1398.560868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1398.560871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1404.900127] e1000e: eth0 NIC Link is Down
[ 1406.620868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1406.620872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1414.900127] e1000e: eth0 NIC Link is Down
[ 1416.500879] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1416.500882] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1422.900128] e1000e: eth0 NIC Link is Down
[ 1424.560868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1424.560872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1424.910125] e1000e: eth0 NIC Link is Down
[ 1426.600870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1426.600874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1427.910126] e1000e: eth0 NIC Link is Down
[ 1429.600872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1429.600876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1431.920125] e1000e: eth0 NIC Link is Down
[ 1433.760873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1433.760876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1434.920126] e1000e: eth0 NIC Link is Down
[ 1436.760869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1436.760872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1440.920126] e1000e: eth0 NIC Link is Down
[ 1442.660870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1442.660873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1442.920127] e1000e: eth0 NIC Link is Down
[ 1444.590868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1444.590871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1445.180125] e1000e: eth0 NIC Link is Down
[ 1446.880869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1446.880872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1454.920126] e1000e: eth0 NIC Link is Down
[ 1456.610868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1456.610871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1456.920126] e1000e: eth0 NIC Link is Down
[ 1458.590869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1458.590872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1464.650126] e1000e: eth0 NIC Link is Down
[ 1466.340869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1466.340872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1466.920127] e1000e: eth0 NIC Link is Down
[ 1468.540885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1468.540888] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1480.920126] e1000e: eth0 NIC Link is Down
[ 1482.570868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1482.570871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1482.920139] e1000e: eth0 NIC Link is Down
[ 1482.920145] e1000e 0000:00:19.0: eth0: Reset adapter
[ 1484.610869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1484.610873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1498.920127] e1000e: eth0 NIC Link is Down
[ 1500.640869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1500.640873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1500.920126] e1000e: eth0 NIC Link is Down
[ 1502.610868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1502.610871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1527.920129] e1000e: eth0 NIC Link is Down
[ 1529.610873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1529.610877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1532.920126] e1000e: eth0 NIC Link is Down
[ 1534.580879] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1534.580882] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1545.940125] e1000e: eth0 NIC Link is Down
[ 1547.560870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1547.560873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1558.960129] e1000e: eth0 NIC Link is Down
[ 1560.610868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1560.610872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1572.970126] e1000e: eth0 NIC Link is Down
[ 1574.560869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1574.560872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1575.970142] e1000e: eth0 NIC Link is Down
[ 1577.570869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1577.570872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1578.970127] e1000e: eth0 NIC Link is Down
[ 1580.590868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1580.590871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1580.970142] e1000e: eth0 NIC Link is Down
[ 1582.810868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1582.810871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1582.970126] e1000e: eth0 NIC Link is Down
[ 1584.640869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1584.640872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1588.970126] e1000e: eth0 NIC Link is Down
[ 1590.550869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1590.550872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1597.970127] e1000e: eth0 NIC Link is Down
[ 1599.740872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1599.740875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1615.970141] e1000e: eth0 NIC Link is Down
[ 1617.540876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1617.540879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1621.970127] e1000e: eth0 NIC Link is Down
[ 1623.590869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1623.590873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1683.370128] e1000e: eth0 NIC Link is Down
[ 1695.330870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1695.330874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1713.100126] e1000e: eth0 NIC Link is Down
[ 1714.720870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1714.720873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1724.290126] e1000e: eth0 NIC Link is Down
[ 1725.870870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1725.870873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1726.100126] e1000e: eth0 NIC Link is Down
[ 1727.690870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1727.690873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1754.130127] e1000e: eth0 NIC Link is Down
[ 1755.840871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1755.840874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1758.130127] e1000e: eth0 NIC Link is Down
[ 1759.790871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1759.790874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1774.140126] e1000e: eth0 NIC Link is Down
[ 1775.800870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1775.800874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1779.150125] e1000e: eth0 NIC Link is Down
[ 1780.770870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1780.770873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1781.150126] e1000e: eth0 NIC Link is Down
[ 1782.730871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1782.730874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1904.520750] e1000e: eth0 NIC Link is Down
[ 1906.220876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1906.220880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1925.550129] e1000e: eth0 NIC Link is Down
[ 1927.190872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1927.190876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1928.570125] e1000e: eth0 NIC Link is Down
[ 1930.220872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1930.220875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1955.190127] e1000e: eth0 NIC Link is Down
[ 1956.840870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1956.840874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1957.400764] e1000e: eth0 NIC Link is Down
[ 1959.120872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1959.120875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1965.290127] e1000e: eth0 NIC Link is Down
[ 1966.860871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1966.860875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1985.770127] e1000e: eth0 NIC Link is Down
[ 1987.480872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1987.480876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1987.481629] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1988.070127] e1000e: eth0 NIC Link is Down
[ 1989.720872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1989.720875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1990.840129] e1000e: eth0 NIC Link is Down
[ 1992.433148] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1992.433152] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1996.800127] e1000e: eth0 NIC Link is Down
[ 1998.080022] eth0: no IPv6 routers present
[ 1998.443220] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 1998.443223] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1998.812005] e1000e: eth0 NIC Link is Down
[ 2000.462918] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2000.462926] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2000.810126] e1000e: eth0 NIC Link is Down
[ 2002.472731] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2002.472734] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2007.820127] e1000e: eth0 NIC Link is Down
[ 2009.580871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2009.580875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2015.840128] e1000e: eth0 NIC Link is Down
[ 2017.450874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2017.450878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2028.870127] e1000e: eth0 NIC Link is Down
[ 2030.530869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2030.530872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2053.930128] e1000e: eth0 NIC Link is Down
[ 2055.590871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2055.590874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2122.700128] e1000e: eth0 NIC Link is Down
[ 2124.280876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2124.280880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2125.710127] e1000e: eth0 NIC Link is Down
[ 2127.340870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2127.340873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2574.190761] e1000e: eth0 NIC Link is Down
[ 2575.780872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2575.780876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2575.781628] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2575.810770] e1000e: eth0 NIC Link is Down
[ 2579.040873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2579.040877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2584.200137] e1000e: eth0 NIC Link is Down
[ 2585.860881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2585.860884] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2586.200126] e1000e: eth0 NIC Link is Down
[ 2586.310037] eth0: no IPv6 routers present
[ 2587.880870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2587.880873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2594.200126] e1000e: eth0 NIC Link is Down
[ 2595.830870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2595.830874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2596.200126] e1000e: eth0 NIC Link is Down
[ 2597.780869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2597.780872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2620.210127] e1000e: eth0 NIC Link is Down
[ 2621.920881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2621.920884] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2623.210126] e1000e: eth0 NIC Link is Down
[ 2624.860871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2624.860874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2636.210126] e1000e: eth0 NIC Link is Down
[ 2637.910871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2637.910874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2646.210126] e1000e: eth0 NIC Link is Down
[ 2647.860880] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2647.860883] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2651.220126] e1000e: eth0 NIC Link is Down
[ 2652.850879] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2652.850883] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2656.220125] e1000e: eth0 NIC Link is Down
[ 2657.820880] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2657.820883] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2678.220138] e1000e: eth0 NIC Link is Down
[ 2679.830872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2679.830875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2681.220137] e1000e: eth0 NIC Link is Down
[ 2682.850879] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2682.850883] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2687.220126] e1000e: eth0 NIC Link is Down
[ 2688.980881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2688.980884] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2694.160127] e1000e: eth0 NIC Link is Down
[ 2695.830871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2695.830875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2710.250126] e1000e: eth0 NIC Link is Down
[ 2711.860872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2711.860875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2763.390148] e1000e: eth0 NIC Link is Down
[ 2765.140873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2765.140878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2765.141872] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2765.690126] e1000e: eth0 NIC Link is Down
[ 2767.380876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2767.380879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2774.710126] e1000e: eth0 NIC Link is Down
[ 2775.700011] eth0: no IPv6 routers present
[ 2776.280873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2776.280876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2818.130127] e1000e: eth0 NIC Link is Down
[ 2819.820872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2819.820876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2822.432141] e1000e: eth0 NIC Link is Down
[ 2824.120873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2824.120877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3091.400137] e1000e: eth0 NIC Link is Down
[ 3093.070873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3093.070877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3350.390181] e1000e: eth0 NIC Link is Down
[ 3352.040878] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3352.040882] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3363.450129] e1000e: eth0 NIC Link is Down
[ 3365.110944] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3365.110947] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3366.390183] e1000e: eth0 NIC Link is Down
[ 3368.080879] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3368.080882] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3374.390826] e1000e: eth0 NIC Link is Down
[ 3376.240875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3376.240879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3389.410033] e1000e: eth0 NIC Link is Down
[ 3391.060876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3391.060880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3404.390170] e1000e: eth0 NIC Link is Down
[ 3406.281496] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3406.281500] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3470.390196] e1000e: eth0 NIC Link is Down
[ 3472.090873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3472.090876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3472.580140] e1000e: eth0 NIC Link is Down
[ 3474.230872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3474.230876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3475.392014] e1000e: eth0 NIC Link is Down
[ 3477.070876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3477.070880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3488.390221] e1000e: eth0 NIC Link is Down
[ 3490.110873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3490.110877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3512.390277] e1000e: eth0 NIC Link is Down
[ 3514.080875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3514.080879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3535.760129] e1000e: eth0 NIC Link is Down
[ 3537.410877] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3537.410880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3539.250138] e1000e: eth0 NIC Link is Down
[ 3540.900870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3540.900874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3623.440900] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3624.790886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3624.790890] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3624.791655] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3626.580129] e1000e: eth0 NIC Link is Down
[ 3628.280872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3628.280876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3628.680138] e1000e: eth0 NIC Link is Down
[ 3630.417733] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3630.417737] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3630.568474] e1000e: eth0 NIC Link is Down
[ 3632.240873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3632.240877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3635.560016] eth0: no IPv6 routers present
[ 3649.400128] e1000e: eth0 NIC Link is Down
[ 3651.040873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3651.040877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3690.720933] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3692.080871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3692.080875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3692.081657] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3693.590139] e1000e: eth0 NIC Link is Down
[ 3695.250876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3695.250880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3697.170140] e1000e: eth0 NIC Link is Down
[ 3698.810870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3698.810873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3701.630125] e1000e: eth0 NIC Link is Down
[ 3702.630016] eth0: no IPv6 routers present
[ 3703.330874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3703.330878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3722.390149] e1000e: eth0 NIC Link is Down
[ 3723.980871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3723.980874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3905.430753] e1000e: eth0 NIC Link is Down
[ 3907.100866] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3907.100870] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3919.690128] e1000e: eth0 NIC Link is Down
[ 3921.382131] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3921.382135] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3923.870131] e1000e: eth0 NIC Link is Down
[ 3925.540873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3925.540876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3977.390130] e1000e: eth0 NIC Link is Down
[ 3979.030875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 3979.030879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4069.390764] e1000e: eth0 NIC Link is Down
[ 4071.190873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4071.190876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4082.390141] e1000e: eth0 NIC Link is Down
[ 4084.060875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4084.060879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4107.961543] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4109.330874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4109.330878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4109.331649] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4110.390744] e1000e: eth0 NIC Link is Down
[ 4112.040868] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4112.040871] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4115.830128] e1000e: eth0 NIC Link is Down
[ 4117.550874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4117.550878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4119.250127] e1000e: eth0 NIC Link is Down
[ 4120.240009] eth0: no IPv6 routers present
[ 4120.850869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4120.850872] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4123.390137] e1000e: eth0 NIC Link is Down
[ 4125.050872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4125.050875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4129.390138] e1000e: eth0 NIC Link is Down
[ 4131.050863] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4131.050867] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4195.390772] e1000e: eth0 NIC Link is Down
[ 4197.210874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4197.210878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4297.874071] e1000e: eth0 NIC Link is Down
[ 4299.460873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4299.460877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4301.461382] e1000e: eth0 NIC Link is Down
[ 4303.170875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4303.170878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4322.900129] e1000e: eth0 NIC Link is Down
[ 4324.521435] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4324.521439] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4326.910126] e1000e: eth0 NIC Link is Down
[ 4328.550875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4328.550879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4328.910765] e1000e: eth0 NIC Link is Down
[ 4330.540872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4330.540876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4347.940124] e1000e: eth0 NIC Link is Down
[ 4349.570874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4349.570878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4361.940314] e1000e: eth0 NIC Link is Down
[ 4363.680875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4363.680879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4363.940208] e1000e: eth0 NIC Link is Down
[ 4365.510876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4365.510879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4366.950128] e1000e: eth0 NIC Link is Down
[ 4368.590874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4368.590878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4368.950129] e1000e: eth0 NIC Link is Down
[ 4370.650874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4370.650878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4439.390776] e1000e: eth0 NIC Link is Down
[ 4441.090876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4441.090879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4443.270905] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4445.190870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4445.190873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4445.191630] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4446.840120] e1000e: eth0 NIC Link is Down
[ 4448.501272] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4448.501276] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4455.370025] eth0: no IPv6 routers present
[ 4468.390132] e1000e: eth0 NIC Link is Down
[ 4469.980875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4469.980879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4485.060895] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4486.432209] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4486.432212] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4486.432985] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4487.391391] e1000e: eth0 NIC Link is Down
[ 4489.130876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4489.130880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4490.390762] e1000e: eth0 NIC Link is Down
[ 4492.120874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4492.120878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4495.620139] e1000e: eth0 NIC Link is Down
[ 4496.610014] eth0: no IPv6 routers present
[ 4497.240878] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4497.240882] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4528.401462] e1000e: eth0 NIC Link is Down
[ 4532.572130] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4532.572133] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4550.120129] e1000e: eth0 NIC Link is Down
[ 4551.810876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4551.810880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4556.421500] e1000e: eth0 NIC Link is Down
[ 4558.140874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4558.140878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4564.970145] e1000e: eth0 NIC Link is Down
[ 4566.572129] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4566.572133] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4804.400209] e1000e: eth0 NIC Link is Down
[ 4806.010886] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4806.010890] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4815.951388] e1000e: eth0 NIC Link is Down
[ 4817.570891] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4817.570894] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4817.940128] e1000e: eth0 NIC Link is Down
[ 4819.602132] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4819.602136] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4826.950129] e1000e: eth0 NIC Link is Down
[ 4828.562130] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4828.562134] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4841.390134] e1000e: eth0 NIC Link is Down
[ 4843.040876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4843.040880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4846.471471] e1000e: eth0 NIC Link is Down
[ 4848.110873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4848.110877] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4851.230139] e1000e: eth0 NIC Link is Down
[ 4852.910871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4852.910875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4960.281119] e1000e: eth0 NIC Link is Down
[ 4964.710870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4964.710873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 5057.450918] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5058.830885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 5058.830889] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 5058.831665] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5111.260908] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5112.630872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 5112.630876] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 5112.631653] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5112.668830] e1000e: eth0 NIC Link is Down
[ 5114.260871] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 5114.260875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 5114.660128] e1000e: eth0 NIC Link is Down
[ 5116.250875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 5116.250878] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 5117.710127] e1000e: eth0 NIC Link is Down
[ 5119.360870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 5119.360873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 5122.240127] e1000e: eth0 NIC Link is Down
[ 5123.230008] eth0: no IPv6 routers present
[ 5123.840870] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 5123.840873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
viper@viper:~$ 



```

---

### Post by btindie on 2010-10-17
> **boydude said:**
> i had 10.04 prior to 10.10 and it was running perfect.


Ok, so it's a problem with upgrading to 10.10.

What's the output of
```
lspci -nn | grep -i ethernet | sed 's/.*\[\(.*\)\].*/\1/' | xargs lspci -nnv -d
```and also
```
modinfo e1000e | egrep '^(version|vermagic)'
```I've found a few similar posts, one such one is [here]("http://ubuntuforums.org/showthread.php?t=1574477") and they managed to fix it by connecting using another method and performing an update.

Also try the following
```
sudo rmmod e1000e
sudo modprobe e1000e
dmesg | grep e1000e | tail -n 15
```
and post the output of dmesg.

---

### Post by boydude on 2010-10-17
btindie, i appreciate all your help, it's pretty early morning now gotta sleep got work later on. i'll give it a whirl after work.

thanks.

---

### Post by boydude on 2010-10-18
```
lspci -nn | grep -i ethernet | sed 's/.*\[\(.*\)\].*/\1/' | xargs lspci -nnv -d
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC Gigabit Network Connection [8086:104b] (rev 02)
	Subsystem: Dell Device [1028:01db]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at dffe0000 (32-bit, non-prefetchable) [size=128K]
	Memory at dffdb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ecc0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e


modinfo e1000e | egrep '^(version|vermagic)'
version:        1.0.2-k4
vermagic:       2.6.35-22-generic SMP mod_unload modversions 


dmesg | grep e1000e | tail -n 15
[  568.609812] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[  568.609814] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[  568.609847] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  568.609857] e1000e 0000:00:19.0: setting latency timer to 64
dmesg | grep e1000e | tail -n 15
[  568.609812] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[  568.609814] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[  568.609847] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  568.609857] e1000e 0000:00:19.0: setting latency timer to 64
[  568.610020] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[  569.072430] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:80:c6:08
[  569.072433] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[  569.072456] e1000e 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1021ff-0ff
[  569.400181] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[  569.460050] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[  570.800869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  570.800873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  570.830773] e1000e: eth0 NIC Link is Down
[  572.400876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  572.400879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  568.610020] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[  569.072430] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:80:c6:08
[  569.072433] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[  569.072456] e1000e 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1021ff-0ff
[  569.400181] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[  569.460050] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[  570.800869] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  570.800873] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  570.830773] e1000e: eth0 NIC Link is Down
[  572.400876] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  572.400879] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO




```

---

### Post by NewarkDevil5 on 2010-10-18
Not sure if this is the same problem or not, but I've got an issue as follows:

My one computer has Ubuntu 10.10 (dual boot with XP) on it. I just upgraded last week from 10.4, but that didn't cause this problem as I'm only now trying to set up the network and I didn't have it set up before anyhow. 

I want to share my cable modem (Motorola) connection through a NetGear ethernet router with two other computers (one with Windows XP and the other with Ubuntu 10.10). Right now I've got the wiring as follows:

Cable Modem -> Router Uplink jack
Router jack #1 -> Dual Boot Computer
Router jack #2 -> Windows XP Computer
Router jack #3 -> Ubuntu 10.10 Computer

The only computer that actually has internet access is the Dual Boot computer. I'm brand new to networking and really haven't had much success in it. 

I've seen where some people have managed to do this by using two ethernet cards on one of their computers, but each one of mine only has one and I really don't want to have to put in another if I can avoid it. The modem has a USB jack on it, but when I tried to hook it up to the dual boot using the USB cord, Ubuntu won't connect to the internet and as such there isn't any connection to share. All I want is to share the modem connection among those three computers and maybe if possible share files and printers.

I've tried looking at other solved questions and this one seems to be as close to the same problem I'm having as I've seen.

---

### Post by btindie on 2010-10-18
@[NewarkDevil5]("http://joeb454.ubuntuforums.org/member.php?u=574354"): I don't think your problem is at all related to the OP, it's sounds like a general network problem. Please start your own thread.
Edit: You can still follow the advice I gave to boydude earlier on how to troubleshoot network issues in post #16.

@[boydude]("http://joeb454.ubuntuforums.org/member.php?u=703418"):
I found another thread [here]("http://ubuntuforums.org/showthread.php?t=1593983") that describes a very similar problem. From that I found [this]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=5f3eed6fe0e36e4b56c8dd9160241a868ee0de2a") patch on kernel.org which is supposed to fix the problem you've got, it's for the same device id. I don't know if it's yet made it into the Ubuntu kernel but you could try updating your system if you haven't yet done so.

If you can, try using a wireless connection to connect to do a
```
sudo apt-get update
sudo apt-get upgrade
```If you can't connect to the internet using the current OS, then you can boot using a LiveCD and chroot into your current root partition. See [this]("http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html") guide for how to do so, even though it's for an older version the same still applies.

---

### Post by boydude on 2010-10-18
thanks, i'll try this when i get home.

i followed the earlier link you provided, is there any need to download any drivers from intels website?

---

### Post by btindie on 2010-10-18
> **boydude said:**
> i followed the earlier link you provided, is there any need to download any drivers from intels website?
The first link was just about someone in a similar situation resolving their problem by doing a system update. The other link is to a patch for the kernel, so unless it's already included in the Ubuntu updates the only option seems to apply the patch yourself or wait till a new kernel update is released - you could always file a bug report in Launchpad and get things speeded up... If you can't do a system update via wireless then you can do using a LiveCD and chroot'ing into your existing installation.

---

### Post by boydude on 2010-10-18
> **btindie said:**
> @[NewarkDevil5]("http://joeb454.ubuntuforums.org/member.php?u=574354"): I don't think your problem is at all related to the OP, it's sounds like a general network problem. Please start your own thread.
Edit: You can still follow the advice I gave to boydude earlier on how to troubleshoot network issues in post #16.

@[boydude]("http://joeb454.ubuntuforums.org/member.php?u=703418"):
I found another thread [here]("http://ubuntuforums.org/showthread.php?t=1593983") that describes a very similar problem. From that I found [this]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=5f3eed6fe0e36e4b56c8dd9160241a868ee0de2a") patch on kernel.org which is supposed to fix the problem you've got, it's for the same device id. I don't know if it's yet made it into the Ubuntu kernel but you could try updating your system if you haven't yet done so.

If you can, try using a wireless connection to connect to do a
```
sudo apt-get update
sudo apt-get upgrade
```If you can't connect to the internet using the current OS, then you can boot using a LiveCD and chroot into your current root partition. See [this]("http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html") guide for how to do so, even though it's for an older version the same still applies.

i have tried this, i've managed to chroot into the partition but when i run apt-get update it's trying to connect to the internet to download

```
root@ubuntu:/# apt-get update
Err http://gb.archive.ubuntu.com maverick Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com maverick Release.gpg
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com maverick Release
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com maverick/main Sources/DiffIndex
Err http://gb.archive.ubuntu.com maverick-updates Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com maverick/main amd64 Packages/DiffIndex
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com maverick/main Sources
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com maverick/main amd64 Packages
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com maverick/main Sources
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com maverick/main amd64 Packages
Err http://gb.archive.ubuntu.com maverick-security Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com maverick/main Sources
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com maverick/main amd64 Packages
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://gb.archive.ubuntu.com maverick Release
Ign http://gb.archive.ubuntu.com maverick-updates Release
Ign http://gb.archive.ubuntu.com maverick-security Release
Ign http://gb.archive.ubuntu.com maverick/main Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/restricted Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/universe Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/multiverse Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/main amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/restricted amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/universe amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/multiverse amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/main Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/restricted Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/universe Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/main Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/restricted Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/universe Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/multiverse Sources/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/main amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/multiverse amd64 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/main Sources
Ign http://gb.archive.ubuntu.com maverick/restricted Sources
Ign http://gb.archive.ubuntu.com maverick/universe Sources
Ign http://gb.archive.ubuntu.com maverick/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick/main amd64 Packages
Ign http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Ign http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Ign http://gb.archive.ubuntu.com maverick/multiverse amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/main Sources
Ign http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://gb.archive.ubuntu.com maverick-updates/universe Sources
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-security/main Sources
Ign http://gb.archive.ubuntu.com maverick-security/restricted Sources
Ign http://gb.archive.ubuntu.com maverick-security/universe Sources
Ign http://gb.archive.ubuntu.com maverick-security/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-security/multiverse amd64 Packages
Ign http://gb.archive.ubuntu.com maverick/main Sources
Ign http://gb.archive.ubuntu.com maverick/restricted Sources
Ign http://gb.archive.ubuntu.com maverick/universe Sources
Ign http://gb.archive.ubuntu.com maverick/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick/main amd64 Packages
Ign http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Ign http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Ign http://gb.archive.ubuntu.com maverick/multiverse amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/main Sources
Ign http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://gb.archive.ubuntu.com maverick-updates/universe Sources
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-security/main Sources
Ign http://gb.archive.ubuntu.com maverick-security/restricted Sources
Ign http://gb.archive.ubuntu.com maverick-security/universe Sources
Ign http://gb.archive.ubuntu.com maverick-security/multiverse Sources
Ign http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
Ign http://gb.archive.ubuntu.com maverick-security/multiverse amd64 Packages
Err http://gb.archive.ubuntu.com maverick/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-updates/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-updates/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-updates/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-security/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-security/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-security/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-security/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://gb.archive.ubuntu.com maverick-security/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_GB.bz2  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/# 

```

---

### Post by boydude on 2010-10-18
i think i'll have to go to windows until the fix can be done.

---

### Post by btindie on 2010-10-19
Did you copy resolv.conf to the chroot environment?
```
sudo cp /etc/resolv.conf /media/feisty/etc/resolv.conf
```
You need to do that before you chroot.

---

### Post by boydude on 2010-10-19
> **btindie said:**
> Did you copy resolv.conf to the chroot environment?
```
sudo cp /etc/resolv.conf /media/feisty/etc/resolv.conf
```
You need to do that before you chroot.

lol i thought that was after the reboot, i'll give it a try after work.

---

### Post by one_equals_two on 2010-10-19
I just tried updating to the latest kernel and it seems like it's still broke.

---

### Post by boydude on 2010-10-19
soemwhere something went wrong,  it says [B]1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.[/B]

```
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
^CFailed to create initrd image.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# apt-get clean
root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg                         
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en         
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Hit http://extras.ubuntu.com maverick Release
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-security Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick-security Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com maverick-security/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-security/universe Sources
Hit http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
Reading package lists... Done
root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://extras.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Hit http://extras.ubuntu.com maverick/main Sources
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-security Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick-security Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com maverick-security/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-security/universe Sources
Hit http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
Reading package lists... Done
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# clear

root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Hit http://extras.ubuntu.com maverick Release
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-security Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick-security Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com maverick-security/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-security/universe Sources
91% [Waiting for headers]^C
root@ubuntu:/# ^C
root@ubuntu:/# clear

root@ubuntu:/# clear























root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://extras.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-security Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick-security Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com maverick-security/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-security/universe Sources
Hit http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
Reading package lists... Done
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# clear

root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Hit http://extras.ubuntu.com maverick Release
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-security Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick-security Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com maverick-security/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-security/universe Sources
Hit http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
Reading package lists... Done
root@ubuntu:/# 

```

```
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# clear

root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Hit http://extras.ubuntu.com maverick Release
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-security Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick-security Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com maverick-security/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-security/universe Sources
91% [Waiting for headers]^C
root@ubuntu:/# ^C
root@ubuntu:/# clear

root@ubuntu:/# clear























root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://extras.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-security Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick-security Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com maverick-security/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-security/universe Sources
Hit http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
Reading package lists... Done
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# clear

root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg
Hit http://extras.ubuntu.com maverick Release
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Hit http://extras.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick-security Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick-security Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/main Sources
Hit http://gb.archive.ubuntu.com maverick-security/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-security/universe Sources
Hit http://gb.archive.ubuntu.com maverick-security/main amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com maverick-security/universe amd64 Packages
Reading package lists... Done
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
^CFailed to create initrd image.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# clear

root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 

```

```
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
pcilib: Cannot open /proc/bus/pci
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 

```

---

### Post by boydude on 2010-10-19
> **one_equals_two said:**
> I just tried updating to the latest kernel and it seems like it's still broke.

have you updated to the latest drivers from intels support site?

---

### Post by one_equals_two on 2010-10-19
> **boydude said:**
> have you updated to the latest drivers from intels support site?

Just tried the drivers from Intel's site (version 8.0.23) and still no change.  I'll try a vanilla kernel in a bit and see if it works there.

---

### Post by boydude on 2010-10-20
> **one_equals_two said:**
> Just tried the drivers from Intel's site (version 8.0.23) and still no change.  I'll try a vanilla kernel in a bit and see if it works there.

let me know if it works.

---

### Post by one_equals_two on 2010-10-20
The latest mainline kernel works ( 2.6.36-rc8 ).  There's even nice pre-built ubuntu versions so you don't have to spend time mucking about in the kernel config.

[https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

Above is the link to read up on how to install the mainline kernels.  You can download the needed debs from the site using a live cd.  Then reboot and install the files.  Reboot when you're finished and select the new rc8 kernel from the grub menu.  Enjoy network access again.

These kernels do drop some ubuntu specific stuff, the site mentions certain restricted drivers, so make sure everything is working okay when you're done.  I imagine it's mostly wireless drivers that will be an issue, and if you're reading this, then that doesn't apply to you ;)  Nvidia and virtualbox drivers still worked fine for me, so my system is 100% now.

---

### Post by boydude on 2010-10-20
i'm not much of a sys admin, is it hard to install?

---

### Post by one_equals_two on 2010-10-20
> **boydude said:**
> i'm not much of a sys admin, is it hard to install?

It's all really easy.  Here are step by step instructions, they differ a little depending on if you are running 32 bit or 64 bit.  If you don't remember if you're 32 or 64, type "uname -a" into a command prompt and look at the word right before GNU/Linux, if it says i686 you are 32bit, if it says x86_64, you are 64bit.

_**Instructions**_
[LIST]
[*]With internet access, go to the download area for either  [[COLOR="Blue"]32 bit[/COLOR]]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/") or the [[COLOR="blue"]64 bit[/COLOR]]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/") kernel
[*]Download the file that ends in all
[*]For 32 bit, download the files that end in i386, for 64bit download the files that end in amd64.  You should have 3 files total when you're done with this and the last step.
[*]Save these files somewhere that you can get at them in your 10.10 install (a spot on your hard drive, USB drive, etc.)
[*]Reboot into 10.10
[*]Copy those 3 files into your home directory
[*]Open terminal (Application -> Accessories -> Terminal)
[*]Run the following command: sudo dpkg -i linux*.deb
[*]After it finishes (~5 minutes), reboot.  You should have network access now.
[/LIST]

---

### Post by boydude on 2010-10-20
> **one_equals_two said:**
> It's all really easy.  Here are step by step instructions, they differ a little depending on if you are running 32 bit or 64 bit.  If you don't remember if you're 32 or 64, type "uname -a" into a command prompt and look at the word right before GNU/Linux, if it says i686 you are 32bit, if it says x86_64, you are 64bit.

_**Instructions**_
[LIST]
[*]With internet access, go to the download area for either  [[COLOR="Blue"]32 bit[/COLOR]]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/") or the [[COLOR="blue"]64 bit[/COLOR]]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/") kernel
[*]Download the file that ends in all
[*]For 32 bit, download the files that end in i386, for 64bit download the files that end in amd64.  You should have 3 files total when you're done with this and the last step.
[*]Save these files somewhere that you can get at them in your 10.10 install (a spot on your hard drive, USB drive, etc.)
[*]Reboot into 10.10
[*]Copy those 3 files into your home directory
[*]Open terminal (Application -> Accessories -> Terminal)
[*]Run the following command: sudo dpkg -i linux*.deb
[*]After it finishes (~5 minutes), reboot.  You should have network access now.
[/LIST]

thanks fingers crossed it'll work later tonight when i get home, am sick and tired spending till early hours trying to fix this.

---

### Post by boydude on 2010-10-20
I cannot believe it, i'm actually posting this through my wired connection. thanks alot for your help, i really appreciate it.

do i need to get rid of the .22 kernel or just leave it as it is?

---

### Post by one_equals_two on 2010-10-20
> **boydude said:**
> I cannot believe it, i'm actually posting this through my wired connection. thanks alot for your help, i really appreciate it.

do i need to get rid of the .22 kernel or just leave it as it is?

Glad it's working for you!  You can remove the old kernels you no longer use, but it doesn't hurt anything to leave them there either.

---

### Post by potlurisardhi on 2012-05-28
Hi,
I am facing similar issue on lenovo t420 with intel 82579LM card.
when i connect to high speed port it throws msg in dmegs "Detected Hardware Unit Hang" and network connection restarts every time (for every 10 sec time).

[ 3021.767332] e1000e 0000:00:19.0: eth0: Detected Hardware Unit Hang:
[ 3021.767336]   TDH                  <fa>
[ 3021.767338]   TDT                  <e7>
[ 3021.767340]   next_to_use          <e7>
[ 3021.767343]   next_to_clean        <f9>
[ 3021.767344] buffer_info[next_to_clean]:
[ 3021.767346]   time_stamp           <a55fb>
[ 3021.767348]   next_to_watch        <fa>
[ 3021.767350]   jiffies              <a6330>
[ 3021.767352]   next_to_watch.status <0>
[ 3021.767354] MAC Status             <80042>
[ 3021.767355] PHY Status             <796d>
[ 3021.767357] PHY 1000BASE-T Status  <0>
[ 3021.767359] PHY Extended Status    <3000>
[ 3021.767361] PCI Status             <10>
[ 3023.766506] e1000e 0000:00:19.0: eth0: Detected Hardware Unit Hang:
[ 3023.766510]   TDH                  <fa>
[ 3023.766512]   TDT                  <e7>
[ 3023.766514]   next_to_use          <e7>
[ 3023.766516]   next_to_clean        <f9>
[ 3023.766518] buffer_info[next_to_clean]:
[ 3023.766519]   time_stamp           <a55fb>
[ 3023.766521]   next_to_watch        <fa>
[ 3023.766523]   jiffies              <a6523>
[ 3023.766525]   next_to_watch.status <0>
[ 3023.766527] MAC Status             <80042>
[ 3023.766529] PHY Status             <796d>
[ 3023.766531] PHY 1000BASE-T Status  <0>
[ 3023.766533] PHY Extended Status    <3000>
[ 3023.766535] PCI Status             <10>
[ 3024.774353] e1000e 0000:00:19.0: eth0: Reset adapter
[ 3027.133320] e1000e: eth0 NIC Link is Up 100 Mbps Half Duplex, Flow Control: Rx/Tx
[ 3027.133336] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3029.021575] FIREWALL: IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:0221:ccff:fe62:dd01 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=92 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=52

---

### Post by mmesantos1 on 2012-05-28
Thank you for the info on this.

---

