---
title: "Unencrypted wireless works, WEP doesn't"
date: 2005-03-16
forum: Networking &amp; Wireless
---

### Post by BaffledMollusc on 2005-03-16
I have a Netcomm 542 wireless adapter (TI ACX 111 chipset) and a Netcomm NB5580W router/ADSL gateway. When I installed Hoary, the wireless network was recognized and configured. I could use Firefox as soon as I booted into Ubuntu. Next I tried to enable WEP. This failed miserably, as I lost all internet access. I have tried entering the WEP key both using the GUI and editing the /etc/network/interfaces file with no luck. Someone else on this forum seemed to solve a similar problem by changing the access mode from "Shared" to "Open" on the wireless AP, so I tried this too. Still no luck.
When  I change the WEP key in the GUI I get a 'Activating "wlan0"' message and a bar that moves back and forth for a looong time. Then it stops. When I close the config screen it pauses for a long time again. Then when I try to logout it pauses for the same long time before complying. It's like at each of these times it spends ages trying to communicate with the network and failing.
I have appended the output of ifconfig and iwconfig as well as my interfaces file to the end of this post. 
I'd be very grateful if anyone has any suggestions. Even if you can't solve my problem I'd like to know the answers to any or all of the following questions:
1) Some people talk about making changes to their /etc/wlan/wancfg-MyESSID file. I don't have one of these; in fact I don't even have an /etc/wlan directory. Do I need this file?
2) Some people talk about the linux-wlan-ng package. This is not installed (an doesn't even appear in the synaptic package manager). Given that wireless worked out of the box without WEP, do I need to install this package?
Please help! If you need any further diagnostic tests, just let me know. Any suggestions accepted; they've got to be better than mine at this point!
mtj@ubuntu:/etc/network$ ifconfig
lo        Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:1065 errors:0 dropped:0 overruns:0 frame:0
TX packets:1065 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:95634 (93.3 KiB)  TX bytes:95634 (93.3 KiB)
wlan0     Link encap:Ethernet  HWaddr 00:40:F4:B9:F3:D4
inet6 addr: fe80::240:f4ff:feb9:f3d4/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:2430 (2.3 KiB)
Interrupt:17 Base address:0x4000
mtj@ubuntu:/etc/network$ iwconfig
lo        no wireless extensions.
wlan0     IEEE 802.11g/b+  ESSID:"happy_mollusc"  Nickname:"acx100 v0.2.0pre8"
Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:36:09:5E:3A
Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
Retry min limit:7   RTS thr:off
Power Management:off
Link Quality=50/100  Signal level=30/100  Noise level=0/100
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
eth0      no wireless extensions.
sit0      no wireless extensions.
/etc/network/interfaces file:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0
# The primary network interface
iface wlan0 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless-mode managed
wireless-essid happy_mollusc
wireless_essid happy_mollusc
wireless_key 84670B28E4
auto wlan0

---

### Post by BaffledMollusc on 2005-03-16
Further diagnostic info to the above, in case it helps.

mtj@ubuntu:/etc/network$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:40:f4:b9:f3:d4
Sending on   LPF/wlan0/00:40:f4:b9:f3:d4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

mtj@ubuntu:/etc/network$ iwlist key
lo        no encryption keys information.

wlan0     3 key sizes : 40, 104, 232bits
          4 keys available :
SIOCGIWENCODE: Operation not permitted
SIOCGIWENCODE: Operation not permitted
eth0      no encryption keys information.

---

### Post by az on 2005-03-16
I am pretty sure that the acx111 driver can not do wep.  Look on the project homepage.  

You can use the windows driver with ndiswrapper, though.  Install ndiswrapper-utils if you do not already have it.  You will have to blacklist the driver module that is being loaded now, though.  Then reboot.

sudo ndiswrapper -i <drivername.INF>
sudo modprobe ndiswrapper
ndiswrapper -l

Then, acticvate your connection.

---

### Post by BaffledMollusc on 2005-03-16
[QUOTE=azz]I am pretty sure that the acx111 driver can not do wep.  Look on the project homepage.  

You can use the windows driver with ndiswrapper, though.  Install ndiswrapper-utils if you do not already have it.  You will have to blacklist the driver module that is being loaded now, though.  Then reboot.

sudo ndiswrapper -i <drivername.INF>
sudo modprobe ndiswrapper
ndiswrapper -l

Then, acticvate your connection.[/QUOTE]

Cool, thanks for that. I'm about to go to bed, but I'll check it out tomorrow. I'll let you  know what happens.

---

### Post by BaffledMollusc on 2005-03-17
The kernel driver for the acx111 does indeed not support WEP. ndiswrapper worked like a charm, however, so thanks again for your advice. 

A couple of minor points, though, in case someone searches for this thread. Because I set my router to open key rather than shared, I had to manually edit my /etc/network/interfaces file and change the line

wireless_key XXXXXXXXXX

to 

wireless_key open XXXXXXXXXX.

Also, if you want the ndiswrapper driver to load up each time on boot, use the command "ndiswrapper -m".

---

### Post by odix on 2005-04-14
ACX111 now supports WEP, since 7th of April or so, but you have to manually patch your kernel, or will be there , hopefully,  :smile: a kernel modules update from the ubuntu people ?

regards

---

### Post by acidvertigo on 2005-04-17
[QUOTE=odix]ACX111 now supports WEP, since 7th of April or so, but you have to manually patch your kernel, or will be there , hopefully,  :smile: a kernel modules update from the ubuntu people ?

regards[/QUOTE]

I have the same problem with a Dlink DWL520+. Now the latest ACX_100  drivers have WEP support for ACX 111, but if manually patch the kernel with make or "make driver" i receive a lot of errors. I had try "make inject" command, it says all ok but after this?

  
Anyone can give me a tutorial? "I'm using AMD64 kernel with UBUNTU latest release.

p.s. Ubuntu is the only dists that make my  video card (Asus 5200FX) and my wireless card fully functional!!!!!!!! Thanks Ubuntu!

---

### Post by acidvertigo on 2005-04-18
Now i have compiled the acx100 driver on ubuntu AMD64 but i have this:

[SIZE=4][COLOR=DarkGreen] ld: Relocatable linking with relocations from format elf32-i386 (/...../..../*********.o) to format elf64-x86-64 (/root/.../..../*****.o) is not supported[/COLOR][/SIZE]
 ](*,) 

sorry for the **** but now i'am at work and can't remember the crrect files (acx_pci.o?)

This error indicates that the driver is not 64bit compatible, but it's not possible because the acx100 driver released with ubuntu amd64 works fine.

I need some libraries to compile it?

---

### Post by globalspace on 2005-05-27
[QUOTE=BaffledMollusc]The kernel driver for the acx111 does indeed not support WEP. ndiswrapper worked like a charm, however, so thanks again for your advice. 

A couple of minor points, though, in case someone searches for this thread. Because I set my router to open key rather than shared, I had to manually edit my /etc/network/interfaces file and change the line

wireless_key XXXXXXXXXX

to 

wireless_key open XXXXXXXXXX.

Also, if you want the ndiswrapper driver to load up each time on boot, use the command "ndiswrapper -m".[/QUOTE]


you've save my wi-fi life !!!!!!  :grin: 

this tip saved my life :

> wireless_key open XXXXXXXXXX. 

**THANKS !**

---

### Post by mxreader on 2005-06-04
Yeh I got a DWL-G520+ that works out of the box with Hoary but have to disable the WEP.  I would also be interested in how I can fix this.  I dont know how to patch the kernel.... still stuck with WIndowsXP grrr.   I would like WEP at least to minimise unknown neighbours taking usage with my account.

I had a read of houseofcraig info and tried to follow the instructions, but failed or got lost (its been a real time waster trying to get it to work).

I know this is an old thead but maybe someone will come along with a tutorial.

---

### Post by funkydan2 on 2005-07-18
I'm not sure if you're still looking at this thread, but I've got a record of my experiences getting WEP to work at [my blog](http://saunders.90megs.com/blog/index.php?entry=entry050705-073812).

It's reasonably easy to get working - though I have been using Linux for a while.

---

