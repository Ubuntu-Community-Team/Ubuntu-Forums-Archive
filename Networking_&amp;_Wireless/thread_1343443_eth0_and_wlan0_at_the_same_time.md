---
title: "eth0 and wlan0 at the same time ?"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by _mikec_ on 2009-12-01
How can i enable both wireless and ethernet at the same time in Karmic ? I have tried adding few lines in /etc/network/interfaces since some have successfully done it that way. reboot. I still have the same problem, so, i need to know how to enable both connections at the same. I am using WICD v1.6.1, wireless is my default connection.

/etc/network/interfaces
> auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
 address 192.168.1.3
 netmask 255.255.255.0
 gateway 192.168.1.1current settings:

> [~]$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:cf:b0:0b  
          inet6 addr: fe80::208:74ff:fecf:b00b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7016 (7.0 KB)  TX bytes:7619 (7.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr 00:12:0e:b3:b9:89  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:eff:feb3:b989/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 

help is needed, thanks

---

### Post by teward on 2009-12-01
do this for me:

go into terminal.  use command ```
lspci
``` and post the output.  This is to see if you even have a wifi card, and to see (if you have one) whether Linux detects it or not.  This is my first request.

---

### Post by _mikec_ on 2009-12-01
lspci output:

> [~]$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev 10)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
[~]$ 

---

### Post by teward on 2009-12-01
Okay, I checked through your lspci output.  There is no wireless card being detected by Linux.  If there were, you'd be able to use the wireless.

Now for the tech person in me, and PLEASE answer as many of the questions as you can.

(1) Laptop or Desktop?  (I'm assuming a laptop, possibly a netbook, am I right?)

(2) Company that made it, the model name, and number (if known).

(3) When you bought the computer, did it say that it came with a wireless card installed?

(4) If this is a computer where you over-wrote or are dual-booting with a Windows installation, was it working with Windows?

(5) Was the wireless ever working previously (before you posted)?

Oh, and the best part is I'll be asking more questions depending on the answers to these ones (sorry, but its what trained techs are trained to do :P)

---

### Post by _mikec_ on 2009-12-10
Wireless card not being detected is weird since i am able to connect, It's a ralink usb wireless adapter (blacklist rt2800usb)

1) Desktop
2) eMachines H3065, 2002 (if i remember correctly), no wireless.
3)  no wireless 
4) wireless is working on windows and linux
5) wireless is always working, i just want to enable both eth0 and ra0 at the same time.

thank you TrekCaptainUSA for your support

here is the output of 'lsusb'
> emachines@emachines:~$ lsusb
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05dc:a531 Lexar Media, Inc. JumpDrive Secure II
Bus 001 Device 004: ID 125f:0000 A-DATA Technology Co., Ltd. 
**Bus 001 Device 002: ID 07b8:3071 D-Link Corp.  **[COLOR=Red]<--- my wireless card[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
emachines@emachines:~$ From the list at [http://cateee.net/lkddb/web-lkddb/RT2X00.html](http://cateee.net/lkddb/web-lkddb/RT2X00.html) this is the wireless usb i have:
[B]vendor: 07b8 ("*D-Link Corp.*"), product: 3071 ("*802.11n/b/g Mini Wireless LAN USB2.0 Adapter*")

[/B]> emachines@emachines:~$ ifconfig
**eth0**      Link encap:Ethernet  HWaddr xxxxxxxxxxxxxxxxx  
          inet6 addr: xxxxxxxxxxxxxxxxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10422 (10.4 KB)  TX bytes:6285 (6.2 KB)
          Interrupt:22 Base address:0x6000 

**lo**        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

**ra0**       Link encap:Ethernet  HWaddr xxxxxxxxxxxxxxxxx 
          inet addr: xxx.xxx.xxx.xxx  Bcast: xxx.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: xxxxxxxxxxxxxxxxxxxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23058070 (23.0 MB)  TX bytes:1105048 (1.1 MB)

emachines@emachines:~$ 

---

### Post by teward on 2009-12-14
Okay, I've seen things like this on Dell computers where when ethernet is connected, it disables wireless interfaces.

Have you tried doing these commands:

```
sudo ifconfig eth0 up
sudo ifconfig ra0 up
```

That might turn both on at once.  The bad news is you'll have to configure both manually.

The fact that its not allowing both to be on at the same time is interesting indeed, though.  But if I may ask, are you trying to use both of the connections to get better speed on your internet?  That won't work, because data will only move through one pathway into the internet, and you can get packet/data corruption when using 2 internet connections at once.

---

### Post by _mikec_ on 2009-12-16
If i activate both connections, none work after. 
I am getting my internet access through a wireless point and i have a server which i am connected on through a router. I have my data/pictures/music..etc on the server and i am using the wireless connection to access the internet. I am hoping there is a way to have both of them working at the same time. 

The first thing i tried of course is to activate both connection but i found out i wasn't able to connect to the internet or the server to my surprise, so i am trying to see if it can be done or not.

cheers

---

### Post by fibercode on 2009-12-16
> **_mikec_ said:**
> I am getting my internet access through a wireless point and i have a server which i am connected on through a router.

Can you elaborate a little more on what you are trying to do. Can you explain if and how your wireless point is different than your router?

If they are different, are they on separate networks. If you give specific IP addresses for both it would be very helpful.

Also, after you enable both interfaces, please post the results of the following commands:

route

ifconfig

---

### Post by _mikec_ on 2009-12-16
i am upstairs and so is the server(closet) and the router...., the wireless point modem is downstairs.
my pc connects to the server through ethernet to the router...., i use my wireless usb adapter to connect to the wireless point modem downstairs.,, since i am 2 different modems, it's on 2 different networks.
> emachines@emachines:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 ra0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 ra0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
emachines@emachines:~$ 

wireless network is 192.168.2.xxx
ethernet network is 192.168.1.xxx

what i want to do is upload/save files on my server without having to disconnect from wireless and connect to ethernet ...and when i want to use wireless to access the internet (like right now) i have to disconnect from ethernet and connect to wireless... any way to have both connections working at the same time ?

---

### Post by Iowan on 2009-12-16
Johnnie-come-lately...
You did reboot after setting up */etc/network/interfaces*?
It *looks* like it should work...

---

### Post by fibercode on 2009-12-16
> **_mikec_ said:**
> 

Looking at your routing table I see that all the traffic for the 192.168.2.* network will correctly go out through your wireless interface and all the traffic for the 192.168.1.* will go correctly out through your ethernet interface.

BUT anything that you try to connect to that is not part of these 2 networks will be forwarded to your default gateway, which in your case is 192.168.1.1 through the ethernet and will end up at your router upstairs which is not connected to the internet.

Edit: Just to illustrate this a little better: For example if you wanted to connect to google.com your computer will first resolve the domain name to an IP by asking your configured DNS server (you can find which is your DNS server by looking at the contents of the /etc/resolv.conf file). Lets say that the resolved IP address for google is 74.125.157.106, which is neither part of the 192.168.1.* nor the 192.168.2.* networks. So the packet will be sent to your default gateway of 192.168.1.1 which is the router and therefore will end up nowhere.

What you should have is a default route of 192.168.2.1 (I am assuming that this is the ip of your wireless access point) going through your wireless NIC. So you should have:

default 192.168.2.1 0.0.0.0 UG 0 0 0 ra0

instead of 

default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

You can make the changes by going to System -> Preferences -> Network Connections. You need to give both interfaces static IP (instead of DHCP). Then take out the default gateway for eth0 and put 192.168.2.1 for the ra0 interface.

Let me know if you need more detailed instructions.

---

### Post by _mikec_ on 2009-12-17
It's working now, both connections are up, i can connect to my server and to the internet at the same time. I edited the eth0 configurations and added a route and check marked the "Use this connection only for resources on its network" setting which disable the use of the eth0 connection to be used as default connection. I didn't had to manually edit /etc/resolv.conf, i set both connections manually instead of DHCP.

> emachines@emachines:~$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 ra0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 ra0
default         mymodem         0.0.0.0         UG    0      0        0 ra0
emachines@emachines:~$ 

**nano /etc/resolv.conf**
> # Generated by NetworkManager
nameserver 192.168.2.1
nameserver 192.168.1.1

Best thanks ! and happy holidays!

edit: when i click on some links on the server (apache2), firefox wants to download the php files... i guess this is a problem with my SEO settings in htaccess..

---

### Post by Iowan on 2009-12-17
Give it a day or so, and if it stays fixed, mark thread [SOLVED]. (under Thread Tools)

---

### Post by Dofustofy on 2009-12-17
> **fibercode said:**
> Looking at your routing table I see that all the traffic for the 192.168.2.* network will correctly go out through your wireless interface and all the traffic for the 192.168.1.* will go correctly out through your ethernet interface.

BUT anything that you try to connect to that is not part of these 2 networks will be forwarded to your default gateway, which in your case is 192.168.1.1 through the ethernet and will end up at your router upstairs which is not connected to the internet.

Edit: Just to illustrate this a little better: For example if you wanted to connect to google.com your computer will first resolve the domain name to an IP by asking your configured DNS server (you can find which is your DNS server by looking at the contents of the /etc/resolv.conf file). Lets say that the resolved IP address for google is 74.125.157.106, which is neither part of the 192.168.1.* nor the 192.168.2.* networks. So the packet will be sent to your default gateway of 192.168.1.1 which is the router and therefore will end up nowhere.

What you should have is a default route of 192.168.2.1 (I am assuming that this is the ip of your wireless access point) going through your wireless NIC. So you should have:

default 192.168.2.1 0.0.0.0 UG 0 0 0 ra0

instead of 

default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

You can make the changes by going to System -> Preferences -> Network Connections. You need to give both interfaces static IP (instead of DHCP). Then take out the default gateway for eth0 and put 192.168.2.1 for the ra0 interface.

Let me know if you need more detailed instructions.
Hello,

Yes i could use a bit of help getting both of my adapters up and running at the same time and a shared internet connection. I recently upgraded my workstation from ubuntu 8.10 to Ubuntu 9.10 - the Karmic Koala - and i am using the wireless adapter airlink101 AWLH6080 configured to access the wireless router. The problem is i can not seem to connect both devices at the same time statically. The wireless card is statically fixed to access the wireless router but whenever i try to connect the eth0 embedded nic card it shuts down the wireless card and i have to  reconnect.I am using a netgear switch to forward  all the other workstations to share the wireless connection. Please advise on how to share this connection. Thank you -dofustofy

---

### Post by fibercode on 2009-12-18
> **Dofustofy said:**
> and i am using the wireless adapter airlink101 AWLH6080 configured to access the wireless router. The problem is i can not seem to connect both devices at the same time statically. The wireless card is statically fixed to access the wireless router but whenever i try to connect the eth0 embedded nic card it shuts down the wireless card and i have to  reconnect.I am using a netgear switch to forward  all the other workstations to share the wireless connection. Please advise on how to share this connection. Thank you -dofustofy

Dofustofy,

Can you elaborate a little more on what you are trying to do. From your post it seems that you are trying to get a number of computers that are connected to your ethernet (through a switch) to the internet by going through the wireless interface on your computer.

It probably looks like this:

computers -> switch -> wired ethernet -> wireless NIC -> router

Is this what you are trying to accomplish?

---

