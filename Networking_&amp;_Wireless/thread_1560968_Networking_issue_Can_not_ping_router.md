---
title: "Networking issue: Can not ping router"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by JamesHayek on 2010-08-25
Hello, I have a networking issue in which I can not resolve from other posts read from Google.

I installed Ubuntu and everything seemed fine except for the networking devices. My wireless card's (Linksys WPC11 Ver3)  lights are lit up however I can not connect to my open network. (I can't even connect hardwired)

I would like this computer to connect automatically to any network in the future.



I added a line to /etc/network/interfaces under #Primary interface


```
auto lo
iface lo inet loopback

#Primary interface
auto eth1
iface eth1 inet dhcp
```


This is the /etc/resolv.conf file: (The nameservers I took from my router at home)


```
nameserver 167.206.245.129
nameserver 167.206.245.130
```


ifconfig yields: 


```
venise@venise-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:02:9d:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30978 (30.2 KB)  TX bytes:10226 (9.9 KB)
          Interrupt:11 Base address:0x6c00 

eth1      Link encap:Ethernet  HWaddr 00:06:25:30:91:47  
          inet6 addr: fe80::206:25ff:fe30:9147/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:12025 (11.7 KB)
          Interrupt:3 Base address:0xe100 

eth1:avahi Link encap:Ethernet  HWaddr 00:06:25:30:91:47  
          inet addr:169.254.4.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90920 (88.7 KB)  TX bytes:90920 (88.7 KB)
```



I entered sudo ifconfig eth1 up

and

sudo /etc/init.d/networking restart

but to my dismay I can not access the internet. I am not sure what to do to get a connection. I can not ping my router at 192.168.1.1

Any suggestions?

---

### Post by Iowan on 2010-08-25
Something went wrong with DHCP - **avahi** stepped in and generously provided an address that's useless for you...
Is eth1 wired or wireless?

---

### Post by JamesHayek on 2010-08-25
> Something went wrong with DHCP

Is there a way to run a ```
sysinstall
``` and re-config the way the ethernet works?

eth1 is wireless, eth0 was my wired connection. 

I also tried using the install CD to run the OS from the CD itself. (To see if a reinstall would work) Even then I could not get internet neither wired or wireless... (Although I was able to see the SSID but I was also able to do this with the current installation)

---

### Post by JamesHayek on 2010-08-26
I originally tried a "sysinstall" similar to FreeBSD to try to reconfig the ethernet. However, since this was a fresh install and I did not know the Ubuntu equivelent, I reinstalled the OS with out the card in the PCI slot. Everything now works and I am online using the installed copy of Ubuntu. I assume there was an errer during instalation.

---

### Post by BkkBonanza on 2010-08-26
Make sure DHCP is enabled and working on your wifi router. Usually what happens is when you restart networking it will try using dhclient to talk to your wifi router and get an address assigned by DHCP. If that fails then avahi will try setting up a peer-peer connection, which isn't much use but indicates that either dhclient isn't trying DHCP or it failed to get an assignment from your router.

If you find that your /etc/network/interfaces file gets altered (not by you) then likely Network Manager is active and trying to control things. That's the little applet on the desktop that tries to find and manage networking. Unfortunately it can mess things up if you also make manual changes. I don't use Network Manager any more so I don't recall now if it has an option for "Attempt Peer Connections" but if you see an option like that then disable it. Or just get kill off Network Manager (if it's even running) and then try manually again. Your settings above and what you tried appear to be ok.

When it's working right the ifconfig output should have an IP indicated for eth1 and no lines with eth1:avahi showing.

---

### Post by JamesHayek on 2010-08-26
Thanks for the help. 

Yes, I checked the router and it is assigning DHCP (I also knew this with out checking because I have other devices connected wirelessly).

Since I reinstalled Ubuntu internet and networking was working as expected. However, this morning when I booted up the computer it was no longer able to connect wirelessly. The network connection icon tried to automatically connect to the last SSID (Which is expected) However, it could not connect anymore.

I tried disabling network manager and retrying to connect manually but got the same error.

After it worked last night, it doesn't work anymore...

What could be causing this? How can I config dhclient to always acquire an address each time the computer starts?





Btw, I thought about trying to reassign the DHCP lease so I Looked for the equivalent command to ipconfig /release (and renew) and found the appropriate command. However, this did not work. Here is the output:


```
venise@venise-laptop:~$ sudo dhclient -r
There is already a pid file /var/run/dhclient.pid with pid 6979
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:06:25:30:91:47
Sending on   LPF/eth1/00:06:25:30:91:47
Listening on LPF/eth0/00:08:74:02:9d:a4
Sending on   LPF/eth0/00:08:74:02:9d:a4
Sending on   Socket/fallback
venise@venise-laptop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:06:25:30:91:47
Sending on   LPF/eth1/00:06:25:30:91:47
Listening on LPF/eth0/00:08:74:02:9d:a4
Sending on   LPF/eth0/00:08:74:02:9d:a4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by JamesHayek on 2010-08-26
Hmm, something is temperamental and I am not sure what... 

I ran the above command then unplugged my router. After waiting 15 seconds I re-plugged the router and it was assigning the lease like it should. It now works once again.



I bought an old laptop, refurbished it and installed Ubuntu for my mother. I wonder if she will go though the same issues as she uses it. Looks like I'll be spending alot more quality time with my mother if this is persistent lol (Hopefully it was just my router though...)

---

### Post by BkkBonanza on 2010-08-26
It sounds like something got bunged up on the router then. Hopefully that won't recur too much. Some routers are more solid than others though. With my Linksys WRT54GL it could runs for endless months with never a problem but it's not uncommon to hear other users complaining about their routers and having to reboot them regularly.

Some routers have a setting for "max leases". You may want to make sure that it wasn't set to a low value that told the router not to assign any more leases.

---

### Post by JamesHayek on 2010-08-26
> You may want to make sure that it wasn't set to a low value that told the router not to assign any more leases.

Yea, I checked that, It wasn't it. I am not sure what the problem was but I am glad it works now. I brought the laptop to my mothers and connected to her router no problem. Hopefully it stays that way.

Yes, some routers are better then others. I went cheap a while back and got a mid level D-Link. That could of been the second issue of mine (especially since it was a DHCP problem after the re-install). I am glad it is working now.

Thank you, and thank you all for the help and input. Thank God for communities!! :D

---

