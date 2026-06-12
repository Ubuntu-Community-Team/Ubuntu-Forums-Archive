---
title: "Internet connectivity problem"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by swap10287 on 2010-03-09
HI,
I am using WINDOWS 7, in which i connect to the internet through broadband connection dialer wich requires username and password,aslo i have another connection wich is used to connect to LAN.
I hav recently installed ubuntu 9.10..
Now my WIRED connection is showing established..with eth1
and following are the outputs of some coomands which might help u to identify the problem..

*****************************************************
ifconfig :
   eth0      Link encap:Ethernet  HWaddr 00:19:d1:85:84:e4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:78:7c:96:4c  
          inet addr:114.79.164.177  Bcast:114.79.164.177  Mask:255.255.255.255
          inet6 addr: fe80::214:78ff:fe7c:964c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139864 (139.8 KB)  TX bytes:39914 (39.9 KB)
          Interrupt:17 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5208 (5.2 KB)  TX bytes:5208 (5.2 KB)




swap@ubuntu:/media/BEB0A3A1AA2E3F51$** lspci**
  00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
  00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
  00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
  00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
  00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
  00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
  00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
  00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
  00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
  00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
  00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
  00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
  00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
  00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
  00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
  00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
  00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
  03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
  06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
  


**route -n **

Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
  169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1


also i have attached screenshot of my connection details.
  
***********************************************

i have very basic knowledge of ubuntu.
Kindly please help me out connecting to my internet.

Thank u.[IMG]file:///E:/Screenshot.jpg[/IMG]

---

### Post by denver on 2010-03-09
If i understand this right, you have 2 connections:

eth0 - broadband (with username and password)
eth1 - LAN

If you have a DSL connection with username and password, just right click on nm-applet (the plug in the upper right corner) and go to "Edit connections". Click on the DSL tab and then on "Add". Fill in your login information and then click on the "Wired" tab. If you have more then one network card, fill in the MAC address (HWaddr in ifconfig output) of the network interface to which your broadband is connected.

If the GUI fails, there is always the terminal version:

```
sudo pppoeconf
```

:)

Hope this helps a bit. Good luck!

---

### Post by Iowan on 2010-03-09
Though I've had occasions where my (Jaunty) laptop connects to wired and wireless simultaneously, ordinarily, NM only manages one interface at a time - or it did. Of course, you used to be able to configure the "other" interface via */etc/network/interfaces* and have them both work.

---

### Post by swap10287 on 2010-03-10
@denver :

Thanx a lot for ur reply..

Ya u r right i am having two lan cards(one on motherboard n odr seaprate card )
But i use only one ethernet connection to connect to the internet OR lan...
i have tried doin the DSL configuration thing but wen it starts processing DSL connection it disconnects from eth1...
Dont know wat to do for this.. ??

can u pls help me out ???

---

### Post by denver on 2010-03-10
Which DSL configuration thing: GUI (nm-applet) or pppoeconf ?

If all else fails, just go with the terminal version:

```
sudo pppoeconf
```

It will look for pppoe concentrators on all network interfaces and if it finds one, it will start a wizzard asking you for login credentials. If you do not know what to choose when the wizzard asks you, just go with defaults. By default it will start your DSL connection on startup.

Always worked for me in the past when nm-applet failed.

Just remember to undo any configuration you made in nm-applet in regards to your DSL connection.

Best of luck!

EDIT: After you run the wizzard and connect, your connection will apear as ppp0 in ifconfig:

```
ifconfig
```

---

### Post by swap10287 on 2010-03-10
Hey Denver

Its working dude...
thnx a lot man...u rock...

ya one more thing i want to ask..can i configure the other connection for my LAN connectivity ???

---

### Post by denver on 2010-03-10
Your LAN should be working great with nm-applet, if you have a router or a DHCP server to give you an IP automaticaly (on the LAN network).

If not, you can manually enter an IP and netmask (for LAN connectivity it should be enough). You don't necesarily need a broadcast address, as most kernels can compute that from the IP+netmask.

Find out what network you need to be on to connect to other computers in your LAN and just enter that information. On most LAN's it's usually an IP ranging from 192.168.x.1 to 192.168.x.255 (where x can be replaced with a number from 0 to 255).

Carefull you don't enter a default gateway on this connection, as it may mess up your internet connectivity.

Best of luck!

---

### Post by swap10287 on 2010-03-10
Thnx..

i mak use of STRONG DC++ to connect to the hub..
will d settings u provided me above will help me to connect through DC TO HUB...

can u please tell me abt the installation of strong DC on UBUNTU ???

---

### Post by denver on 2010-03-10
I don't think there is StrongDC++ for linux. You do however have linuxdcpp. Just navigate to "Applications-->Ubuntu Software Center" and search for "linuxdcpp".

If the hub you are trying to connect is on the internet you should have no problems. Stay away from warez an piracy though. film makers, software writers and artists in general need to make a living too ;).

---

