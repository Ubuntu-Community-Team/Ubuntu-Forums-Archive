---
title: "Please help setting up ethernet connection on my laptop under ubuntu 8.10"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by KAMENi on 2008-12-08
First of all, hi to everyone ):P

i'm totally new to ubuntu but i like it and i want to learn something about linux.

i've installed ubuntu on my laptop, and got almost everything working. i cant get the ethernet working
i've asked people in croatia on 2 forums, and noone can help me

after installing the ubuntu, i've installed HSOconnect so i can connect via web'n'walk. that works fine.
then, when i saw lots of updates i wanted to connect via ethernet and found out that it doesn't work

after some researching, i've tried editting network/interfaces, and i've changed it to:

interfaces:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
gateway 192.168.1.254
network 192.168.1.0
broadcast 192.168.1.255

#alternatively:
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#a#
#iface eth0 inet dhcp

i've been also asked to list these files:

ifconfig:
hso0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00 
          inet addr:87.252.141.236  P-t-P:87.252.141.236  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1486  Metric:1
          RX packets:2537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10
          RX bytes:2666980 (2.6 MB)  TX bytes:313780 (313.7 KB)

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)


lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

sudo lshw -C network
*-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:b4:35:79
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:e1:c9:26:19:b2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

lsmod | grep sis900
sis900                 27904  0
mii                    13440  1 sis900


after all, i've changed the interfaces back to 

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

i want to set it so i can connect on 2 different routers and ISPs (home & office). 
laptop is acer aspire 3000, and my home router is set to routing mode (i've been using it normaly when xp was on the laptop)

please help me :frown:

---

### Post by abhilashkumar on 2008-12-08
I have an Acer 4520 laptop. My ethernet has been working out of the box since ubuntu 7.10. Thats when I tried ubuntu for the first time.

So is your network not detected when you plug in the ethernet cable?

---

### Post by KAMENi on 2008-12-08
that's right

nothing worked automatically

---

### Post by abhilashkumar on 2008-12-08
Try the [posts here]("http://ubuntuforums.org/search.php?searchid=52829261").

---

### Post by KAMENi on 2008-12-08
very helpful link :confused:

i get it that i should search, but i don't think this is a typical problem

everything seems to work fine, but it doesnt

if anyone has good advice, or a useful link, i would be eternaly grateful

---

### Post by jonobr on 2008-12-08
Hi 


Somethings odd about your config (good work posting all your info though!!)


I notice you mentioned first you configured your eth0 to use a static IP address

> auto eth0
iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
gateway 192.168.1.254
network 192.168.1.0
broadcast 192.168.1.255

Then in your Ifconfig, the interface mentioned is different,
with an 87. xxx IP address, 
Am I reading the post incorrectly or the problem?


> 

hso0 Link encap:UNSPEC HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
inet addr:87.252.141.236 P-t-P:87.252.141.236 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1486 Metric:1
RX packets:2537 errors:0 dropped:0 overruns:0 frame:0
TX packets:2231 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:10
RX bytes:2666980 (2.6 MB) TX bytes:313780 (313.7 KB)

---

### Post by Iowan on 2008-12-08
[Here]("http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html") is a link for setting up static addresses.  There's also a Work-around on here somewhere for static addresses.

I also noticed that hso0 seems to have no MAC address (but I know very little about bridges, virtual devices, etc.)

---

### Post by KAMENi on 2008-12-10
finally i got time to try this

i went to your link (Iowan), and got to Step 6 : Now Back in your terminal type sudo /etc/init.d/networking restart.


it says 
 * Reconfiguring network interfaces...                                          SIOCDELRT: No such process
                                                                         [ OK ]


is it just me or this shouldn't appear?

please guys, help me out. i'm losing my will to mess with ubuntu

---

### Post by Iowan on 2008-12-11
Found [this]("http://lists.debian.org/debian-user/2004/08/msg03201.html") thread with similar problem - [this]("http://archive.linuxvirtualserver.org/html/lvs-users/2001-09/msg00028.html") seems to be best definition of error - has to do with deleting route.

---

### Post by KAMENi on 2008-12-12
thanks for your help but i give up on ubuntu

i had to actually use my pc, not spend most of my time messing around it to get it to work.
i went back to old & known platform, winXP

thanx again for your support
bye

---

