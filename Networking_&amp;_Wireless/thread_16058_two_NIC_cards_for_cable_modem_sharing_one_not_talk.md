---
title: "two NIC cards for cable modem sharing one not talking"
date: 2005-02-18
forum: Networking &amp; Wireless
---

### Post by wglamm on 2005-02-18
Ok... I have two wired network cards.. 

eth0 is to my cable modem and is doing fine

eth1 is to the switch so I can set up routing and internet sharing with all the Window machines in the house and it is not talking

 this is what I get from lspci -vvv 

0000:00:09.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 64 (2000ns min, 14000ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at ea101000 (32-bit, prefetchable) [size=e8000000]
        Region 1: I/O ports at e400 [size=32]
        Region 2: Memory at ea000000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at 00100000 [disabled]

 this is what I get from ifconfig -a


eth1      Link encap:Ethernet  HWaddr 00:A0:C9:2D:6B:C9
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

 this is what I get from ifdown eth1

ifdown: interface eth1 not configured


 this is what I get from ifup eth1

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Operation not supported.
SIOCSIFFLAGS: Resource temporarily unavailable
SIOCSIFFLAGS: Resource temporarily unavailable
Failed to bring up eth1.

the Hub is a 10/100 netgear that was talking to the eth0 card back before the cable modem when we were doing shared dial up on a WindowsME (the windowsME box has the dial up connection)

the eth1 card is out of a stock pile and I have not tried to get it to work by itself or anything intelegent like that...

the eth1 card is lighting up the hub at 10M 

thats were my knowing runs out everything past this point starts to get blury and make my palms sweat  :?

---

### Post by grj on 2005-02-19
eth0 is missing from your ifconfig -a. Did you post the full ouput? Try switching the cables to see if that helps.

---

### Post by az on 2005-02-19
sudo apt-get install etherconf

It will detect and try to configure your cards for you.  You can always rerun the configuration by doing

sudo dpkg-reconfigure etherconf

This is the first step.

---

### Post by wglamm on 2005-02-19
here is what I get when I run apt-get install etherconf
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  dhcp-client libconfhelper-perl liblogfile-rotate-perl
Suggested packages:
  configlet-frontends
The following packages will be REMOVED:
  dhcp3-client ubuntu-base
The following NEW packages will be installed:
  dhcp-client etherconf libconfhelper-perl liblogfile-rotate-perl
0 upgraded, 4 newly installed, 2 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 165kB of archives.
After unpacking 225kB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe dhcp-client 2.0pl5-19 [102kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe liblogfile-rotate-perl 1.04-1.2 [18.7kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe libconfhelper-perl 0.12.5 [9682B]Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe etherconf 1.17 [34.1kB]
Fetched 165kB in 1s (95.5kB/s)

Preconfiguring packages ...
(Reading database ... 64406 files and directories currently installed.)
Removing ubuntu-base ...
Removing dhcp3-client ...
Selecting previously deselected package dhcp-client.
(Reading database ... 64373 files and directories currently installed.)
Unpacking dhcp-client (from .../dhcp-client_2.0pl5-19_i386.deb) ...
Selecting previously deselected package liblogfile-rotate-perl.
Unpacking liblogfile-rotate-perl (from .../liblogfile-rotate-perl_1.04-1.2_all.deb) ...
Selecting previously deselected package libconfhelper-perl.
Unpacking libconfhelper-perl (from .../libconfhelper-perl_0.12.5_all.deb) ...
Selecting previously deselected package etherconf.
Unpacking etherconf (from .../etherconf_1.17_all.deb) ...
Setting up samba (3.0.7-1ubuntu6.3) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of webmin-samba:
 webmin-samba depends on samba; however:
  Package samba is not configured yet.
dpkg: error processing webmin-samba (--configure):
 dependency problems - leaving unconfigured
Setting up dhcp-client (2.0pl5-19) ...

Setting up liblogfile-rotate-perl (1.04-1.2) ...
Setting up libconfhelper-perl (0.12.5) ...
Setting up etherconf (1.17) ...
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Operation not supported.
Internet Software Consortium DHCP Client 2.0pl5
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:a0:cc:e7:ba:f7
Sending on   LPF/eth0/00:a0:cc:e7:ba:f7
Sending on   Socket/fallback/fallback-net
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.169.32.1
bound to 67.162.15.193 -- renewal in 172800 seconds.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Operation not supported.
SIOCSIFFLAGS: Resource temporarily unavailable
SIOCSIFFLAGS: Resource temporarily unavailable

Errors were encountered while processing:
 samba
 webmin-samba
E: Sub-process /usr/bin/dpkg returned an error code (1)



The only thing I didnt enter in the install was the router IP address because eth1 is connecting to my home network hub and I think this machine is the router, well is going to be the router  :|  


Thanks for all the help.. I love a good puzzle but this is a lot to absorb...

---

### Post by az on 2005-02-20
"update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba"

This is a known bug.

The last entry in bugzila about it was to ask if it still occurred in Hoary.

Please check it out:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=2492](https://bugzilla.ubuntu.com/show_bug.cgi?id=2492)

I would think it is quite rare.  DId you try to install a usb wireless device, like in the bugzilla description?

Anyway, when you correct the symlinks and do
sudo apt-get -f install
you will have a nice place to start fixing your ehternet problem.


"The only thing I didnt enter in the install was the router IP address because eth1 is connecting to my home network hub and I think this machine is the router, well is going to be the router"

What do you mean by this?  Did you get the option of configuring your other card?

---

### Post by wapowell on 2005-02-20
> "The only thing I didnt enter in the install was the router IP address because eth1 is connecting to my home network hub and I think this machine is the router, well is going to be the router"

What do you mean by this?  Did you get the option of configuring your other card?

Just to clarify, are you trying to make your ubuntu box a router?
It sounds to me like you have a dual homed ubuntu box.  One nic gets an IP from your ISP, and the other nick you want to connect to a hub so other machines in the house can connect and get on the internet (which would mean those machines need to get a RFC 1918 address from your second nic in the ubuntu box).  Do I understand this post correctly?

Internet--- **{**_eth0_ (in your case 67.162.15.193) **UBUNTU BOX** _eth1_ **}** --- hub --- other machines in the house

If this is the case, then the Ubuntu box would be acting as your router. The hub is not a router.  In your first post you said it was a switch.  Either way it is a L1 or L2 device (don't know what hardware you have exactly) and not a router.  Your Ubuntu box would need to be configured to act as a router, which would mean that it needs to answer for dhcp requests that come from machines attached to your hub (which from your description would be attached to eth1).

I guess before I go any further with that thought, please let me know if I correctly understand your scenario.

Also,... clearly eth0 can negotiate an IP.  However in your first post you state that eth1 is out of a stockpile and you have not tried to get it to work on its own yet.  Just to rule out the obvious have you swapped the cables to make eth1 connect to your ISP just to see if it is working properly?  You already established that the connection to the internet is good via eth0, maybe connecting eth1 to the ISP instead of eth0 will tell you if the card itself is ok.


-Bill

---

### Post by wglamm on 2005-02-21
azz... 

I will look into the bug thing, no I am not installing a usb wireless device

I believe that eth1 is a sick card, I did try connecting it to the cable modem and it did not connect... so I am trying to get another card to see if that trouble shoot checks out.. 

unless you think the bug is an issue but that looks like samba trying to find files?? (please dont asume I know much, thats just intuition) 

I will let you post more info when I get a known good NIC card in place of my current eth1

wapowell...

yes routing is going to be my next hurdle, but the more I dig the more I think you are right that the physical NIC card is the current problem


I am connected to the cable modem with eth0 and I want to set up an in house network that gets internet through this box, well probably through an other box so I can have the full attention of my box to play Gnometris   8-[ 

g-night everybody... thanks for the info I truly appreciate the support, see you on the next question

---

### Post by az on 2005-02-21
Your system will continue to spit out errors until you remove the symlinks by hand and then do:
sudo apt-get -f install

---

### Post by wglamm on 2005-02-24
I solved my problem.                   \\:D/
I took out the bad NIC,

went to buy two new NICs and found I could get a combo wired and wireless router from D-Link for $25 after rebate @ Office Max

so I am skipping the linux box as router thang and learning how to set up print sharing through my router  :shock: 

Thanks for all the help, all the same

---

