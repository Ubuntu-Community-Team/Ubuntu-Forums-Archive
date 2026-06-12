---
title: "Can't connect to internet"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by Eirinjas on 2010-01-18
I decided last night it was finally time I look at Linux.  I've wanted to for a very long time, but was not keen on the learning curve.  Anyway, I did a dual-boot with XP, which had it's own issues, but which I figured out with some info I found in these forums.  Now my problem is I can't access the internet from within Ubuntu.  It's finding the hardware, I think.  Below is data gained from lspci, nm-tool, ifconfig, and lshw.  Any help is appreciated.  Thanks.


jason@jason-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation E7505 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation E7505/E7205 PCI-to-AGP Bridge (rev 03)
00:02.0 PCI bridge: Intel Corporation E7505 Hub Interface B PCI-to-PCI Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc R360 NJ [Radeon 9800 XT]
01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)
02:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04)
02:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04)
02:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04)
02:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04)
03:0e.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
04:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:0d.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
04:0e.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 07)
05:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0e.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (rev 01)
jason@jason-desktop:~$

jason@jason-desktop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        00:0D:56:BD:34:66

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


jason@jason-desktop:~$



jason@jason-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:bd:34:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jason@jason-desktop:~$


jason@jason-desktop:~$ sudo lshw -c network
[sudo] password for jason: 
  *-network               
       description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: e
       bus info: pci@0000:03:0e.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:bd:34:66
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:24 memory:ff6e0000-ff6fffff ioport:dcc0(size=64)
jason@jason-desktop:~$

---

### Post by never say never on 2010-01-18
It appears that you did not configure your NIC (Network Interface Card) during the install process.
 
You can configure it via CLI (Command Line Interface) by following [these instructions]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html").
 
If in doubt follow the DHCP instructions.
 
Good Luck.

---

### Post by Eirinjas on 2010-01-18
Okay, so I was able to edit the interfaces file and added:

auto eth0
iface eth0 inet dhcp

Then I ran this command:

sudo /etc/init.d/networking restart

Which made it look for DHCP offers, whereas before it did nothing.  This is what it gave me:

jason@jason-desktop:~$ sudo gedit /etc/network/interfaces
jason@jason-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0d:56:bd:34:66
Sending on   LPF/eth0/00:0d:56:bd:34:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]
jason@jason-desktop:~$

---

### Post by Eirinjas on 2010-01-18
Ok,.. tried some other stuff, but still no connection.  Not sure what I did, but now the Network Manager has Eth0 as:   ifupdown(eth0) 

...and it won't allow me to edit or delete it.  *sigh*

This is Ubuntu 9.10, BTW.

---

### Post by Loosewheel on 2010-01-18
> **Eirinjas said:**
> Ok,.. tried some other stuff, but still no connection.  Not sure what I did, but now the Network Manager has Eth0 as:   ifupdown(eth0) 

...and it won't allow me to edit or delete it.  *sigh*

This is Ubuntu 9.10, BTW.

NetworkManager will not mess with anything in the '/etc/interfaces' file.
Comment out the  'auto eth0' and 'iface eth0 inet dhcp' lines and reboot.
See if it brings up eth0...If not right click the 'NM Icon' and see if the 'Enable Networking' box is checked, and/or click 'Edit Connections'.
You may have to add the connection and set it up DHCP.

---

### Post by Eirinjas on 2010-01-18
I'm gonna do what you suggested, Loosewheel, but I did check for the 'Enable Networking' checkbox and every time I did it was checked.  Also, when I installed XP on this machine it had issues with no network connection.  I corrected that by manually setting the rate to 100mbps, instead of auto or 1000mbps.  Also, I checked Intel's website and they do have a driver for this particular adapter for Linux, but I am completely green here when it comes to Linux and how to install drivers, or do much else for that matter :P

---

### Post by Loosewheel on 2010-01-18
> **Eirinjas said:**
> I'm gonna do what you suggested, Loosewheel, but I did check for the 'Enable Networking' checkbox and every time I did it was checked.  Also, when I installed XP on this machine it had issues with no network connection.  I corrected that by manually setting the rate to 100mbps, instead of auto or 1000mbps.  Also, I checked Intel's website and they do have a driver for this particular adapter for Linux, but I am completely green here when it comes to Linux and how to install drivers, or do much else for that matter :P

Looks like nm-tools and lshw -C network indicate you are using the linux 'e1000' driver. I believe that should work.

---

### Post by Eirinjas on 2010-01-18
Okay, it didn't help any.  The support seems there, it's finding the hardware, ...why isn't it seeing the network?  This is really frustrating.

---

### Post by Loosewheel on 2010-01-18
> **Eirinjas said:**
> Okay, it didn't help any.  The support seems there, it's finding the hardware, ...why isn't it seeing the network?  This is really frustrating.

Have you checked the ethernet cable....swap it out? Are you plugged into a
dsl modem router or switch......other working systems on this network??

---

### Post by Eirinjas on 2010-01-18
The ethernet cable is fine - I have an install of Windows XP on the same system, which is what I'm using to visit these forums.  I have a cable connection with a router that has 4 ports.  The router is set up for DHCP, the default gateway for the lan is 192.168.1.1, the subnet mask is 255.255.255.0, and it begins assigning IP's at 192.168.1.100.  There is one other XP system on the network.  It's IP is: 192.168.1.103    

This system I have the dual-boot on is located at 192.168.1.100

I tried adding 192.168.1.100 - 192.168.1.102, the subnet mask and default gateway info manually and it's still not working.

---

### Post by argosreality on 2010-01-18
> **Eirinjas said:**
> I'm gonna do what you suggested, Loosewheel, but I did check for the 'Enable Networking' checkbox and every time I did it was checked.  Also, when I installed XP on this machine it had issues with no network connection.  I corrected that by manually setting the rate to 100mbps, instead of auto or 1000mbps.  Also, I checked Intel's website and they do have a driver for this particular adapter for Linux, but I am completely green here when it comes to Linux and how to install drivers, or do much else for that matter :PMy indepth networking knowledge is a little rusty but I distinctly remember that if a router (or switch) thats supposed to support auto-negotiation of link speeds and the client which does as well both are having issues then you're looking at either a bad cable or bad switch port. 

As silly as it sounds, have you tried another cable or a different port on the switch? There's no reason you should have to auto-define a speed on a modern router/switch

---

### Post by Eirinjas on 2010-01-18
I selected the speed on the card in Windows XP, not the router, and that allowed a fresh install of Windows XP to connect.  As I said, I'm using the same computer that I can't access the internet with in Ubuntu, to access the internet with Windows XP.  Not a cable or a port issue.

---

### Post by Eirinjas on 2010-01-19
I had no luck with the onboard Intel ethernet, so I found an old Linksys NIC and put that in.  Still no network connection.  I've wasted so much time trying to fix this issue that I just feel like wiping Ubuntu off the hard drive and sticking with Windows.

---

### Post by Eirinjas on 2010-01-19
Still beating my head against a wall here.  I'm thinking, because neither network card worked, that perhaps it's either a router problem or a software problem.  The router works fine with both Windows systems on the network though, as well as with my son's DS and Wii systems which connect via wifi.  Does Linux require something of a network that Windows doesn't?

---

### Post by never say never on 2010-01-19
If you have to select the speed and duplex in Windows you will probably need to do it in linux too.  There is obviously something not right if it will not auto-negotiate, how far are you from the switch?  Is the cabling good??

Have you tried manually configuring speed and duplex?

You can do it with ethtool, something like:
ethtool -s eth0 speed 100 duplex full autoneg off

If full doesn't work might try half.

To set speed and duplex that will last a reboot, add the following to
your /etc/network/interfaces in the stanza for your network card:

pre-up ethtool -s eth0 speed 100 duplex full autoneg off

See if that gets things going.

---

### Post by Eirinjas on 2010-01-19
The cable is good.  Same system with Ubuntu runs Windows XP and connects just fine.  I'd guess there's 30 feet of cat5 cable between the system and the router.  Have tried Ethtool and I know I was able to change the autoneg setting - to no effect.  I will try what you've suggested though.

---

### Post by Eirinjas on 2010-01-19
Okay, so I tried that and it didn't work.  I did see the network manager icon spin, which I haven't seen, but still no internet connection.  I did notice that lshw would sometimes report the card as 32 bits wide, and other times as 64 bits wide.  Not sure if that's relevant.  There is a driver and the device is coming up as active.  I don't get it.

---

### Post by Eirinjas on 2010-01-19
Okay, after much frustration, I finally got it working.  My router allowed 50 DHCP clients, which I set down to 10.  I then tried running dhclient which gave me this:

Listening on LPF/eth0/00:0d:56:bd:34:66
Sending on   LPF/eth0/00:0d:56:bd:34:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.2 -- renewal in 35630 seconds.
jason@jason-desktop:~$ 

Still not showing an internet connection, so I tried restarting the network and running dhclient again, which gave me this:

jason@jason-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for jason: 
 * Reconfiguring network interfaces...                                   [ OK ] 
jason@jason-desktop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 1944
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0d:56:bd:34:66
Sending on   LPF/eth0/00:0d:56:bd:34:66
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 42071 seconds.
jason@jason-desktop:~$ 

Still, showing as disconnected.  The fact that the dhclient was getting an offer, made me hopeful, so I opened up Firefox - wham!  Internet connection.  So, I do have an internet connection now, but Network Manager doesn't know???  Weird.  

I so need a beer!!

---

### Post by Eirinjas on 2010-01-19
Okay, on reboot I lost internet connection again, but was able to get it back by running dhclient again.  Is there any way to make this permanent so I don't have to run it manually everytime I boot up the system?

---

### Post by Eirinjas on 2010-01-20
If anyone knows how to make the change mentioned before permanent, I'd be in your debt.  Also, thought it worth mentioning that I tried the Live CD of Fedora 12 to see if it could connect - it couldn't.  Same connection issues.

---

