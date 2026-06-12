---
title: "Ethernet Connection help needed...please"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by hcbmbr on 2009-04-06
[This is the second time I have posted this; the first time I got no replies, but I'm not sure why. If someone could at least tell me what information I can post so that I can pique the forum members' interest to actually address this, I'd appreciate it. I have a business depending on this so I need to get it handled. Thank you very much.]

I am trying to setup Ubuntu on my IBM Thinkpad T40. But, I am unable to get the DSL ethernet connection up and running.

I have looked through MANY threads trying to solve the problem, but have been unable. Here is where I stand:

The ethernet card is an Intel 82801DB Pro/100 VE (MOB). I entered all the correct IP addresses into the Network Configuration "Wired" windows, listed under the "IPv4" settings.

When I get to the main desktop of Ubuntu a window pops up telling me that I am connected via eth0, but when I open up Firefox no URLs respond. 

When I run "sudo pppoeconf" I get 4 ethernet ports, but the tests come up nil on all of them.

Below are copies of commands I entered to gather information; these were taken from other threads, but I have no idea what any of this means.

Any help you could give would be GREATLY appreciated. Thank you.



hcb@ubuntu:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0d:60:5e:af:ee  
          inet addr:12.148.234.235  Bcast:12.148.235.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3109 (3.1 KB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16000 (16.0 KB)  TX bytes:16000 (16.0 KB)

pan0      Link encap:Ethernet  HWaddr fa:18:a6:32:75:62  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


hcb@ubuntu:~$ sudo dhclient

[sudo] password for hcb: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/fa:18:a6:32:75:62
Sending on   LPF/pan0/fa:18:a6:32:75:62
Listening on LPF/eth0/00:0d:60:5e:af:ee
Sending on   LPF/eth0/00:0d:60:5e:af:ee
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


hcb@ubuntu:~$ dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 5928
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

---

### Post by bcom on 2009-04-06
Just curious, why do you need to enter the IP addresses manually?   The properties option of the connection in Network settings you can put a check in Enable Roaming and Ubunutu should configure the connection for you.

Also, do you need to access the Internet through a proxy server?  If yes, did you configure that? If a Proxy Server is involved, open up Firefox, go to Edit, select Preferences, click on the Advance tab, and then click on Settings.  You can configure the use of a Proxy Server here or perhaps try Auto Detect or Use System Proxy to see if that helps. 

Can you ping the ip address of your ISP?  If you can ping your ISP or other computers on the Internet then the problem probably involves configuring Firefox as mentioned above.

It doesn't look like you are connecting through a router, but, if you are, did you configure that properly?

---

### Post by superprash2003 on 2009-04-06
are you connected to a routeR?? is the 12.x.x.x ip a static ip set by you?

---

### Post by hcbmbr on 2009-04-06
Thank you for your help bcom.

I am connecting through a router. I think it is configured as it should be as I am able to get on via Windows XP (Firefox).

I did as you suggested: I "pinged" the ISP, and all packets returned successfully; I set Firefox setting to auto-detect proxy server; but could not find "roaming" option in network settings.

I also set auto-detect (dhcp) in "wired" network settings.

None of that solved the problem completely. 

Any thoughts?

---

### Post by bcom on 2009-04-07
Ok, here are some additional thoughts.

Apparently At&T (which I assume you are using) requires that you configure your router with static IP information.  So, normally, this means that the router is configured with the static information, provided by the ISP, e.g, the IP Address, the subnet mask, and gateway address.

Once the router is configured, your router will hand out IP addresses to the computers on your network via a protocol known as DHCP (Dynamic Host Control Protocol).  The IP addresses handed out by the router (known as private IP addresses) are within one of the following ranges:

10.0.0.0 through 10.255.255.255
169.254.0.0 through 169.254.255.255 (APIPA only)
172.16.0.0 through 172.31.255.255
192.168.0.0 through 192.168.255.255.

Your IP address as indicated by the output of ifconfig -a is 12.148.234.235.  This is not an address handed out by the router as it is not within the proper range used for computers "behind" a router.  This address is the IP Address that should be configured in your router, not within Firefox.  (It probably is already in your router or else your Windows computer could not connect to the Internet.)

Try this: Click on the Network Manager icon on your Ubuntu computer (it looks like a computer monitor and is found next to the date) to open up the Network Settings applet.  Once the Network Settings Applet is open, click on the Connections tab, select the Wired Connection (ethO) and click on properties.  The etho tab should give you a place to put a check in Enable Roaming.  

By enabling roaming, you are making it possible for the computer to automatically pick up one of the private IP addresses handed out by the router.  With a Windows computer, you would need to reboot the computer for the change to take place.  I don't think this is the case with Ubuntu but you should reboot just to be sure.


Boot the machine and try to connect to the Internet. 

To see DHCP and a private IP address in action on a Windows computer, go to a command prompt and type ipconfig /all.  You will see an IP address in one of the ranges listed above.

---

