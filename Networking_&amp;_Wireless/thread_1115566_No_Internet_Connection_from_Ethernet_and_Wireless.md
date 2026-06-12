---
title: "No Internet Connection from Ethernet and Wireless"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by oddji on 2009-04-03
OK. I've been spending a whole lot of time on reading forums and goolging and couldn't find any solution. I installed ubuntu 8.10 and there are no internet connection both ethernet and wireless. I went to System > Administration > Hardware Drivers which has Broadcom B43 Wireless Driver and ATI/AMD proprietary FGLRX graphics driver. However neither of them can be activated. I tried countless times but they both take forever to activate and didn't even activate at the end. Then I went to System > Adminstration > Network tools. Under Devices tab, Network device: Loopback Interface (lo) has 2 things under IP information.
IPv4, (IP Address) 127.0.0.1, (Netmask/Prefix) 255.0.0.0
IPv6, ::1, 128, (Scope) Host

kham@Kham:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
kham@Kham:~$ 
kham@Kham:~$ lsusb
Bus 003 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

kham@Kham:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:41:ab:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:e8:65:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 0e:68:fb:e6:af:e4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

kham@Kham:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:41:ab:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

kham@Kham:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

kham@Kham:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

kham@Kham:~$ sudo dhclient eth0
[sudo] password for kham: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:16:d4:41:ab:82
Sending on   LPF/eth0/00:16:d4:41:ab:82
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Melk79 on 2009-04-04
That is very frustrating.  I can't say I have the answer, but I do have sympathy from past experiences.  If you have the means/another computer, until someone smarter than me can answer, try downloading the LTS version 8.04 Hardy Heron.  Boot into that Live CD and see if you can get connected while on the LiveCD.  Even try the Intrepid Live CD and see if you can connect.  I've always ended up with better installations if I connect first and then install.

---

### Post by 4ebees on 2009-04-04
> **oddji said:**
> OK. I've been spending a whole lot of time on reading forums and goolging and couldn't find any solution. I installed ubuntu 8.10 and there are no internet connection both ethernet and wireless. I went to System > Administration > Hardware Drivers which has Broadcom B43 Wireless Driver and ATI/AMD proprietary FGLRX graphics driver. However neither of them can be activated. I tried countless times but they both take forever to activate and didn't even activate at the end. Then I went to System > Adminstration > Network tools. Under Devices tab, Network device: Loopback Interface (lo) has 2 things under IP information.
IPv4, (IP Address) 127.0.0.1, (Netmask/Prefix) 255.0.0.0
IPv6, ::1, 128, (Scope) Host

- SNIP-
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Now that is weird.

I have exactly the same ethernet controller:

> 05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

and have no problems.

1. You're connecting to an Ethernet modem, hub or router yes?
2. Make sure you have settings similar to mine (see attached image) in that you have your machine to accept DHCP (which should be delivered by your modem)

I'd also take Melk79's suggestion and try it with a live CD. If that works, then there's something going on with your settings that you need to change.

Let us know how you go.

---

### Post by oddji on 2009-04-10
> **4ebees said:**
> Now that is weird.

I have exactly the same ethernet controller:



and have no problems.

1. You're connecting to an Ethernet modem, hub or router yes?
2. Make sure you have settings similar to mine (see attached image) in that you have your machine to accept DHCP (which should be delivered by your modem)

I'd also take Melk79's suggestion and try it with a live CD. If that works, then there's something going on with your settings that you need to change.

Let us know how you go.

I don't know how to get to where you are in that image. Are you using an older version of ubuntu? I'm using 8.10. Can you list the steps to the image? I tried to activate my Broadcom B43 wireless driver but it won't let me activiate it.

---

### Post by 4ebees on 2009-04-10
> **oddji said:**
> I don't know how to get to where you are in that image. Are you using an older version of ubuntu? I'm using 8.10. Can you list the steps to the image? I tried to activate my Broadcom B43 wireless driver but it won't let me activiate it.

Okay, let's see if this helps. On the basis that I use KDE and this may be similar in Gnome.

(I'm using 8.04 LTS)

Step one. 

See image one.

So, we have to open your "network settings"

Then, image two, shows you where you should end up.

Click on the Admin Mode button (I've highlighted it in yellow) and enter your sudo password.

Then you get:

image three.

Select 'Configure Interface' or merely double click the Interface you wish to configure. This will bring up the smaller dialogue box you can see hovering over the main windows

Select 'dhcp' and see if that solves anything.

By the way, when you say "it won't let you activate it" what exactly do you mean? What happens?

See how you go and get back to us.

---

### Post by oddji on 2009-04-11
> **4ebees said:**
> 
By the way, when you say "it won't let you activate it" what exactly do you mean? What happens?

Ok. I just tried plugging in the ethernet cable to the ethernet hole in my dorm room and the internet works, but very slow. The times I tried connecting the ethernet were in the computer lab. I don't know what is the difference. I guess now we have a new problem to tackle. I'm going to try plugging in the ethernet somewhere else and see if the net is faster. However the wireless still isn't working. Is there some updates, patches, or things I need to download? 
By "it won't let me activate it" I mean that when I clicked on the activate button, it'll show the updating bar for a few secs then the updating bar disappear. I tried clicking on the activate button again and again and get the same result. Same goes to the graphic card in the picture. I'm guessing I have to be on the net to activate it?

---

### Post by 4ebees on 2009-04-11
> **oddji said:**
> Ok. I just tried plugging in the ethernet cable to the ethernet hole in my dorm room and the internet works, but very slow. The times I tried connecting the ethernet were in the computer lab. I don't know what is the difference.

I would imagine that the Uni uses some form of filtering, maybe by MAC address. You should ask whether you're allowed to access the net directly from the lab. If so, you'll need to find out what the details are.


> I guess now we have a new problem to tackle. I'm going to try plugging in the ethernet somewhere else and see if the net is faster.

Good idea.

> However the wireless still isn't working. Is there some updates, patches, or things I need to download? By "it won't let me activate it" I mean that when I clicked on the activate button, it'll show the updating bar for a few secs then the updating bar disappear. I tried clicking on the activate button again and again and get the same result. Same goes to the graphic card in the picture. I'm guessing I have to be on the net to activate it?

Yes, you'll need a net connection. Ubuntu will automatically download the necessary software and install it. You will probably be prompted to restart the machine.

See how you go and get back to us.

---

### Post by oddji on 2009-04-11
> **4ebees said:**
> 

Yes, you'll need a net connection. Ubuntu will automatically download the necessary software and install it. You will probably be prompted to restart the machine.

See how you go and get back to us.

Ok the Update Manager found 287 updates but I cannot update them and keep getting these errors:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
How do I fix this problem? 

By the way, I successfully activated the Broadcom Wireless Driver, but my wireless still doesn't work.

---

### Post by 4ebees on 2009-04-11
> **oddji said:**
> Ok the Update Manager found 287 updates but I cannot update them and keep getting these errors:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
How do I fix this problem? 

Okay, on the basis that I don't know what you don't know :)

The GUI way (easy way? :)) Do this in a terminal (if using Gnome):

gksu Nautilus

(If using KDE, then type kdesu konqueror)

This will bring up a superuser version of Nautilus.

Now browse to:

/etc/apt/

and copy:

sources.list

Then paste a copy on your desktop. Just so we have a copy of your source.list file in a safe place :)

Alternatively you can paste a copy in the same directory and call it sources.list.orig or something similar so you know what it is.

The command line version would be 

sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig

You can change the directory to anything you want. It's up to you. I keep a directory called 'config_files' for such things. Just remember, if you're going to copy the file to somewhere in the root file system, you must use 'sudo' at the beginning. If you're going to copy a file to a user space, you don't need to.


Now, how are you trying to update? Are you using Synaptic or the Adept desktop updater (you'll see this as an icon in on the toolbar)?

In either instance you need to use one **or** the other. You should only have one open at a time as they will conflict with one another. You also need to enter the admin/sudoer password for either to be able to update the packages.

Run Adept by clicking on the toolbar icon (it will ask for the superuser password when you say you wish to install the updates). Run Synaptic by accessing it through the menu **or**by holding down the 'Alt' button and pressing 'F2'. You will then be prompted for the superuser password.

If you have two accounts on the machine one is **like** an admin or superuser account. So if you're logged into the 'user' and not the primary account, unless you have allowed the superuser password to be run within the user account then you will have to login as the primary account holder.

You should be able to update now.

If not, try out this in a terminal:

sudo dpkg --configure -a

If that doesn't work have a look here:

[http://www.linuxforums.org/forum/yoper-linux-help/18223-apt-get-problem.html](http://www.linuxforums.org/forum/yoper-linux-help/18223-apt-get-problem.html)

and here:

[https://answers.launchpad.net/ubuntu/+source/aptitude/+question/24497](https://answers.launchpad.net/ubuntu/+source/aptitude/+question/24497)


See how you go and get back to me.


> By the way, I successfully activated the Broadcom Wireless Driver, but my wireless still doesn't work.

What exactly happens when you try to use it?

---

