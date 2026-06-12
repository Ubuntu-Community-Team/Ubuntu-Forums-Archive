---
title: "Linksys WRT54GC Wired Connection to 8.04"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by jjtstan on 2009-08-07
We moved houses two days ago and the Linux machine has now stopped working with our Linksys router.

Equipment:
Dell Inspiron 530 running Hardy Heron 8.04 (upgraded from Gutsy)
Windows XP notebook.  
China Telecom Home Access HA510 ADSL modem.
Linksys WRT54GC wireless router.  

The China Telecom modem requires a username and password.  At our old house, I had the modem wired into the router wired into the Dell linux box.  The Windows notebook would run off the router's wireless signal.  This setup worked just fine, albeit with a different model China Telecom modem (ZTE?) and a different username & password for said modem.   

We just moved houses, which is when the problems started. 

At the new house, we had the new modem hooked directly to the Dell (linux machine), and it worked fine, although took a bit of doing - pppoeconf and possibly some other terminal commands.  I didn't actually do that part.

I then disconnected the modem from the Linux box and connected it to a Windows laptop (which I am using to write this), and it still worked fine.  I then hooked the Linksys router up in between the Windows laptop & the modem (wired connections on both sides), & used Firefox to change the username & password the router would send to the modem.  Everything still fine.

I then pulled the router's ethernet cable out of the Windows machine, plugged it into the Linux box, and everything went to hell.  I've tried turning off and re-starting everything, with no effect. 

The Windows laptop can still use the wireless signal from the router to get on the internet just fine.  

The Linux box does not recognize the Linksys router anymore (it used to at the old house).  The Network Manager applet in the upper right only offers manual network configuration.  The "Connection Information" option is greyed out and unavailable.  Likewise System > Administration > Network Settings produces a dialog box that is entirely grayed out.  

I have tried the following, not because I understand any of it, but because this information was requested for a similar problem on another thread:

lspci -nn:
> 
john@dell-desktop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02) 
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02) 
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02) 
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02) 
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IR (ICH9R) LPC Interface Controller [8086:2916] (rev 02) 
00:1f.2 IDE interface [0101]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller [8086:2920] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02) 
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller [8086:2926] (rev 02) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8300 GS [10de:0423] (rev a1) 
john@dell-desktop:~$  


sudo ppoeconf:

> Sorry, I scanned 1 interface, but the Access             &#9474;  
          &#9474; Concentrator of your provider did not respond. Please    &#9474;  
          &#9474; check your network and modem cables. Another reason      &#9474;  
          &#9474; for the scan failure may also be another running pppoe   &#9474;  
          &#9474; process which controls the modem. 



ping 192.168.1.1 (the router's IP address):

> john@dell-desktop:~$ ping 192.168.1.1 
connect: Network is unreachable 


lshw -C Network:> 

john@dell-desktop:~$ sudo lshw -C Network 
[sudo] password for john:  
  *-network                
       description: Ethernet interface 
       product: 82562V-2 10/100 Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 02 
       serial: 00:1d:09:8b:21:9b 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.2.0 duplex=full firmware=1.1-2 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s 
john@dell-desktop:~$  

dmesg | grep eth:
> 
john@dell-desktop:~$ dmesg | grep eth 
[   22.266732] Driver 'sd' needs updating - please use bus_type methods 
[   22.266927]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[   30.223083] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1d:09:8b:21:9b 
[   30.223087] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection 
[   30.223112] 0000:00:19.0: eth0: MAC: 5, PHY: 7, PBA No: ffffff-0ff 
[   32.976792] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   34.310158] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX 
[   34.310161] 0000:00:19.0: eth0: 10/100 speed: disabling TSO 
[   34.312114] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[   44.819820] eth0: no IPv6 routers present 
[ 1775.380530] 0000:00:19.0: eth0: Link is Down 
[ 1788.401313] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX 
[ 1788.401320] 0000:00:19.0: eth0: 10/100 speed: disabling TSO 
[ 1944.360113] 0000:00:19.0: eth0: Link is Down 
[ 1955.841781] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX 
[ 1955.841788] 0000:00:19.0: eth0: 10/100 speed: disabling TSO 
[ 1960.878693] 0000:00:19.0: eth0: Link is Down 
[ 1962.509973] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX 
[ 1962.509980] 0000:00:19.0: eth0: 10/100 speed: disabling TSO 
[ 2020.824485] 0000:00:19.0: eth0: Link is Down 
[ 2052.702513] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX 
[ 2052.702521] 0000:00:19.0: eth0: 10/100 speed: disabling TSO 
[ 2053.885618] 0000:00:19.0: eth0: Link is Down 
[ 2055.544892] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX 
[ 2055.544899] 0000:00:19.0: eth0: 10/100 speed: disabling TSO 
[ 2184.738960] 0000:00:19.0: eth0: Link is Down 
[ 2296.619342] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX 
[ 2296.619349] 0000:00:19.0: eth0: 10/100 speed: disabling TSO 
[ 2297.814440] 0000:00:19.0: eth0: Link is Down 
[ 2299.469713] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX 
[ 2299.469720] 0000:00:19.0: eth0: 10/100 speed: disabling TSO 
john@dell-desktop:~$  

uname -mr:
> 
john@dell-desktop:~$ uname -mr 
2.6.24-24-generic i686
john@dell-desktop:~$  

dhclient eth0:

> john@dell-desktop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:1d:09:8b:21:9b 
Sending on   LPF/eth0/00:1d:09:8b:21:9b 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPOFFER of 192.168.1.101 from 192.168.1.1 
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67 
DHCPACK of 192.168.1.101 from 192.168.1.1 
bound to 192.168.1.101 -- renewal in 34132 seconds. 
john@dell-desktop:~$  


I also now am unable to get the Linux machine to connect directly to the internet, even if I disconnect the router and hook the modem directly to the linux machine.  I get the following results (198.162.1.1 and 198.162.1.2 are the IP addresses for the modem):

> john@dell-desktop:~$ sudo pppoeconf 
[sudo] password for john:  
Plugin rp-pppoe.so loaded. 
john@dell-desktop:~$ plog 
Aug  8 01:41:08 dell-desktop pppd[8596]: Using interface ppp0 
Aug  8 01:41:08 dell-desktop pppd[8596]: Connect: ppp0 <--> eth0 
Aug  8 01:41:09 dell-desktop pppd[8596]: PAP authentication succeeded 
Aug  8 01:41:09 dell-desktop pppd[8596]: peer from calling number 00:90:1A:41:45:D5 authorized 
Aug  8 01:41:09 dell-desktop pppd[8596]: replacing old default route to eth0 [192.168.1.1] 
Aug  8 01:41:09 dell-desktop pppd[8596]: Cannot determine ethernet address for proxy ARP 
Aug  8 01:41:09 dell-desktop pppd[8596]: local  IP address 61.170.145.91 
Aug  8 01:41:09 dell-desktop pppd[8596]: remote IP address 218.1.60.228 
Aug  8 01:41:09 dell-desktop pppd[8596]: primary   DNS address 202.109.14.5 
Aug  8 01:41:09 dell-desktop pppd[8596]: secondary DNS address 124.74.213.68 
john@dell-desktop:~$ plog 
john@dell-desktop:~$ pon dsl-provider 
Plugin rp-pppoe.so loaded. 
john@dell-desktop:~$ ping 198.162.1.1 
PING 198.162.1.1 (198.162.1.1) 56(84) bytes of data. 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
 
--- 198.162.1.1 ping statistics --- 
9 packets transmitted, 0 received, 100% packet loss, time 8010ms 
 
john@dell-desktop:~$ ping 198.162.1.2 
PING 198.162.1.2 (198.162.1.2) 56(84) bytes of data. 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
ping: sendmsg: Operation not permitted 
 
--- 198.162.1.2 ping statistics --- 
8 packets transmitted, 0 received, 100% packet loss, time 7010ms 
 
john@dell-desktop:~$  

Any help would be greatly appreciated.  As you can probably tell from this message, I am pretty much a rookie, without many skills, so I will need pretty detailed instructions.

---

### Post by jjtstan on 2009-08-07
To reply to the responses I got in this thread:

[http://ubuntuforums.org/showthread.php?t=1233713](http://ubuntuforums.org/showthread.php?t=1233713)

and to explain the latest developments:

Sometime since I went to bed last night (right after the above post) and before my wife woke up this morning, we were visited by the Linux fairy, and now everything is working fine - Linux machine, Windows notebook, everything.

I left both machines, router, and modem on last night, and now everything works.  I don't know why or how, or if it will still work if I turn things off and back on again.  Any suggestions for packets I should be downloading/installing now that the Linux machine is connected would be appreciated.

Currently, plog gets no response:

> john@dell-desktop:~$ plog 
john@dell-desktop:~$  

Other issues:

China Telecom sent five people out to the house yesterday to let us know that they have never seen Linux before, don't know what it is, and can't help.  They're strictly a Windows-only operation, at least here in Shanghai.

Our landline call quality is very bad, with many disruptions if you try to make regular phone calls.  Yesterday, before I installed the router and before the Linux fairy's visit, my wife got the Linux machine online just using the ADSL modem, and then was disconnected, with an error message along the lines of "serial port is not responding."

---

### Post by jjtstan on 2009-08-10
The Linux fairy giveth and the Linux fairy taketh away, at least in conjunction with Hotspot Shield.  Someone has apparently downloaded Hotspot Shield to the Linux machine's desktop and tried to install it, resulting in total loss of internet access.  Any suggestions on what to do would be appreciated (Add/Remove programs function on menubar not working).

In other news, China Telecom advises me to purchase ADSL-filters for the phones in my house, to fix call quality & internet disruption issues.

---

### Post by jjtstan on 2009-08-10
The Linux Fairy helps those who help themselves.

sudo dhclient fixed the above problem.

---

