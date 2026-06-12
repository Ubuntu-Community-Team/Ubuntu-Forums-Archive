---
title: "Wired connection no longer working"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Zeikcied on 2009-08-03
My computer is wired to the router (as is this second computer that I'm on right now).  The router seemed to stop working earlier (turns out the plug just went bad), and I ended up plugging my computer directly into the DSL modem.  I used pppoeconf to connect, and it did.  But after hooking my router back up (with a new plug) and connecting my computer back up to it, Kubuntu Jaunty is no longer recognizing the router.

I don't know if it's an issue with the pppoeconf use or what.  My router is working, and the light for my Ethernet cable is lit (and it turns off when I unplug the cable), but Kubuntu isn't seeing the router.  I can only assume that it's still expecting the modem.

But I used poff to turn off pppoe, I deleted the /etc/ppp folder, and I commented out the lines added to /etc/network/interfaces by pppoeconf.  I also followed some steps from a wireless DHCP thread (commenting out a line in /etc/dhcp3/dhclient.conf), to no avail.

What should I do?

---

### Post by HavocXphere on 2009-08-03
Confusing problem description :neutral: ...but I'll give it a shot.

The lights on the router that show whether a cable is connected mean very very little. If a port on the router dies due to a surge or whatever then the light can still work 100%.

> I ended up plugging my computer directly into the DSL modem.

So if it is *now* connected directly then it wasn't before. So there was another hub/switch inbetween or maybe internet sharing or...

Unless you by directly you mean via usb which is also possible with some routers.

> The router seemed to stop working earlier (turns out the plug just went bad)
By plug do you mean power plug or ethernet cable connector? Or maybe a wall socket?

Ethernet cables generally don't just die without cause. Power plugs w/ transformers however do.

> What should I do? 
Try a liveCD to figure out whether its a software/hardware issue.

> but Kubuntu isn't seeing the router.
Can it ping the router IP? Can you connect to the router config page?

Also, try "sudo dhclient eth0"...solved problems for me in the past.

It would really help if you gave a description of the physical layout of the network and which parts failed and what was replaced. And the output of ifconfig would also help.

---

### Post by Zeikcied on 2009-08-03
> **HavocXphere said:**
> Confusing problem description :neutral: ...but I'll give it a shot.
Sorry.  I tend to ramble, and I try to explain everything.  But it usually comes out a tad confusing.

> By plug do you mean power plug or ethernet cable connector? Or maybe a wall socket?
Yes, I mean the power plug.  I think it's an AC Adapter.

> Can it ping the router IP? Can you connect to the router config page?

Also, try "sudo dhclient eth0"...solved problems for me in the past.
Ping says that the network is down, as does dhclient.

> It would really help if you gave a description of the physical layout of the network and which parts failed and what was replaced. And the output of ifconfig would also help.
Okay.  I have a router to which both computers are wired.  The router then goes to an Ethernet ADSL modem.  Both computers were perfectly fine with the router before.  The router appeared to die earlier this afternoon.  So I plugged the Ethernet cable from my primary computer to the modem, and ran pppoeconf to establish a connection.  Later I tried swapping a different AC adapter to the router, which fixed the problem.  So I went back to my original configuration.  Now my primary computer doesn't properly set up the network.

I tried plugging it in to Port 4 on the router, and that didn't work.  My router isn't showing the computer in the list of active connections.  I'm almost certain this has something to do with my hooking up to the modem and using pppoeconf, and then switching back to the router, but I have no idea how to fix it.

As for ifconfig, I can run it on this computer.

```
eth0      Link encap:Ethernet  HWaddr 00:02:a5:30:7b:e5
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fe30:7be5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12212511 (11.6 MB)  TX bytes:2631333 (2.5 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:32100 (31.3 KB)  TX bytes:32100 (31.3 KB)
```

I should note that running ifconfig on the affected computer doesn't give an eth0 result.

---

### Post by Iowan on 2009-08-03
> **Zeikcied said:**
>  I also followed some steps from a wireless DHCP thread (commenting out a line in /etc/dhcp3/dhclient.conf), to no avail.
If the line concerns rfc3442, then you probably need to edit out the "rfc3442-classless-static-routes" portion of the "request" line as well as the "option rfc3442" line. (Maybe you already did).

---

### Post by Zeikcied on 2009-08-03
> **Iowan said:**
> If the line concerns rfc3442, then you probably need to edit out the "rfc3442-classless-static-routes" portion of the "request" line as well as the "option rfc3442" line. (Maybe you already did).

Yeah, I did that, and it didn't help.

I'm still pretty sure that it was the pppoeconf program that caused this issue.  I just wish I knew how to fix it.  The computer I'm on now is my mom's computer, and I'd really like to get back to using my own.

---

### Post by HavocXphere on 2009-08-03
Much clearer.:D

PPPoE = Point to Point Protocol **over Ethernet**. So until the underlying ethernet works you can forget about pppoe connections.

Sounds like you got some hardware damage from a power surge. Keep swopping out cables & ports & computers until you isolate the problem. Probably the network card on the kubuntu PC. Maybe use one of the system info tools to check if ubuntu can even see the network card.

Also, power surges can "jump" through ethernet equipment. e.g. A motherboard that gets fried on one PC can fry the network card on a second via the ethernet cable.

Ethernet ports are fairly sensitive. Its quite common to see a few fried ports on network equipment.. Half the ports on my residential gateway are dead already (Either completely or just the light)...

> I should note that running ifconfig on the affected computer doesn't give an eth0 result.
Even if connected directly to the modem?

I don't think the box you are describing as a router is actually router. I'm guessing its switch or hub. Not that it really matters.;)

---

### Post by Zeikcied on 2009-08-03
> **HavocXphere said:**
> Much clearer.:D

PPPoE = Point to Point Protocol **over Ethernet**. So until the underlying ethernet works you can forget about pppoe connections.

Sounds like you got some hardware damage from a power surge. Keep swopping out cables & ports & computers until you isolate the problem. Probably the network card on the kubuntu PC. Maybe use one of the system info tools to check if ubuntu can even see the network card.

Also, power surges can "jump" through ethernet equipment. e.g. A motherboard that gets fried on one PC can fry the network card on a second via the ethernet cable.

Ethernet ports are fairly sensitive. Its quite common to see a few fried ports on network equipment.. Half the ports on my residential gateway are dead already (Either completely or just the light)...
Actually, I'm using the Kubuntu Jaunty LiveCD on the affected computer.  So it seems the hardware is just fine.  Same ethernet port and router.  All I did was reboot with the LiveCD.

> Even if connected directly to the modem?

I don't think the box you are describing as a router is actually router. I'm guessing its switch or hub. Not that it really matters.;)
I didn't try ifconfig when it's connected to the modem.

The fact that my Wii is connected to the wireless, the second computer works just fine with the typical setup (wired to the router), and the affected computer works with the LiveCD (also wired), leads me to believe that it's a configuration issue on the installed Kubuntu Jaunty.  The only thing I did to alter the configuration was connecting it to the modem and using pppoeconf.

---

### Post by Zeikcied on 2009-08-03
Ok, I went back to the affected Kubuntu install (sans LiveCD) and I did sudo ifconfig eth0 up, and that seemed to activate eth0.  But when I did sudo dhclient eth0, it complained that libncurses.so.5 couldn't be found.  I tried doing sudo apt-get install --reinstall ncurses, but it told me that while another package references it, ncurses can't be found.

EDIT: The libncurses5 package is installed correctly, and /lib/libncurses.so.5 does exist.  I don't know why dhclient is complaining about it.

I rebooted after opening eth0 with ifconfig, but it didn't stay open when Kubuntu booted back up.

I'm so lost. :(

EDIT 2: I hooked the Ethernet cable back up to the modem and tried using pppoeconf again.  It complains that the /etc/ppp folder is missing (because I deleted it) and it doesn't recreate it.  Also, that didn't seem to change anything.  eth0 still wasn't working.  So I hooked my computer back up to the router.

But I am again using the Kubuntu Jaunty LiveCD on the affected computer.  So I know for sure it isn't a hardware issue.  But I'm guessing I royally screwed my eth0 configuration somehow.

I could just reinstall, but I'm hesitant.  I just went through a big fuss a few days ago to upgrade to the Karmic kernel as a workaround to the ext4 freezing bug in Jaunty (which was a much bigger hassle than I expected) and I don't want to have to deal with that again.  I really hope there's a solution that doesn't involve starting over. :(

---

### Post by Zeikcied on 2009-08-03
I just wanted to bump because I edited the previous post with some more info and stuff.

I really need help in fixing this.  Please? :(

---

### Post by Zeikcied on 2009-08-03
I copied the /etc/ppp folder off of the Jaunty disc onto my hard drive.  So now the pppoeconf works, when connected directly to the modem.

But I have a sinking suspicion that this is just starting the whole mess all over again.  As it is this exact setup that caused the problem to begin with.

Argh.

Since it was asked earlier for the ifconfig results while connected directly to the modem, here it is:

```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:e4:d6:a5
          inet6 addr: fe80::215:f2ff:fee4:d6a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:96 txqueuelen:1000
          RX bytes:12825010 (12.8 MB)  TX bytes:1251073 (1.2 MB)
          Interrupt:21 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:43184 (43.1 KB)  TX bytes:43184 (43.1 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:76.241.156.166  P-t-P:76.241.159.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:10788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8797 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:12584650 (12.5 MB)  TX bytes:1048107 (1.0 MB)
```

---

### Post by HavocXphere on 2009-08-04
> I rebooted after opening eth0 with ifconfig, but it didn't stay open when Kubuntu booted back up.

I think you can fix that by editing you /etc/network/interfaces.

```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
[B]
auto eth0
iface eth0 inet dhcp[/B]
```
I'm guessing you'll need to comment out the middle 3 lines since your pppoeconf is probably set up differently to mine. The last too lines should ensure that eth0 comes back up after a reboot.

I'm a bit out of my depth with the pppoeconf +ncurses thing. I'm guess that broke during the karmic upgrade.:confused:

Most modern modems allow you to put the adsl details into the modem itself so that you don't need the whole pppoe stuff.

---

### Post by Zeikcied on 2009-08-04
> **HavocXphere said:**
> I think you can fix that by editing you /etc/network/interfaces.

```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
[B]
auto eth0
iface eth0 inet dhcp[/B]
```
I'm guessing you'll need to comment out the middle 3 lines since your pppoeconf is probably set up differently to mine. The last too lines should ensure that eth0 comes back up after a reboot.

I'm a bit out of my depth with the pppoeconf +ncurses thing. I'm guess that broke during the karmic upgrade.:confused:

Most modern modems allow you to put the adsl details into the modem itself so that you don't need the whole pppoe stuff.

I did try commenting out those lines.  It didn't work.

For whatever reason, eth0 and networking works properly when connected to the modem.  Then I run poff, switch the cable to the router, and it's unable to connect.

Again, the LiveCD is perfectly capable of connecting to the router, so it isn't hardware.  But I just don't understand.  ifconfig will even show eth0 as active, but ping and dhclient tell me that the network is down when connected to the router.  I have no idea what happened. :(

EDIT: I know that libncurses.so.5 is on my system.  It's in /lib and /usr/lib.  I didn't fully upgrade to Karmic.  The workaround I followed involved adding a Pin to /etc/apt/preferences (which didn't exist prior to my doing this), which sets the Karmic packages to a priority of 50, thus making the Jaunty packages a higher priority.

---

### Post by Zeikcied on 2009-08-04
Okay.  I'm going to post some things in hopes that it will help solve this problem.

I once again tried hooking up to the router.  Still couldn't get it to work.

ifconfig after using poff, while connected to the router:
```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:e4:d6:a5  
          inet6 addr: fe80::215:f2ff:fee4:d6a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106653 errors:1 dropped:0 overruns:0 frame:0
          TX packets:97640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:973 txqueuelen:1000                          
          RX bytes:119851937 (119.8 MB)  TX bytes:11908798 (11.9 MB)
          Interrupt:21 Base address:0xdc00                          

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                              
          RX bytes:149960 (149.9 KB)  TX bytes:149960 (149.9 KB)
```

Running sudo dhclient eth0:
```
There is already a pid file /var/run/dhclient.pid with pid 16077
killed old client process, removed PID file                     
Internet Systems Consortium DHCP Client V3.1.1                  
Copyright 2004-2008 Internet Systems Consortium.                
All rights reserved.                                            
For info, please visit http://www.isc.org/sw/dhcp/              

/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory                                   
Listening on LPF/eth0/00:15:f2:e4:d6:a5                                        
Sending on   LPF/eth0/00:15:f2:e4:d6:a5                                        
Sending on   Socket/fallback                                                   
DHCPREQUEST of 192.168.0.139 on eth0 to 255.255.255.255 port 67                
DHCPACK of 192.168.0.139 from 192.168.0.1                                      
/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory                                   
bound to 192.168.0.139 -- renewal in 38297 seconds.
```

Then:
```
ping -c1 192.168.0.1                      
connect: Network is unreachable
```

Using sudo /etc/init.d/networking restart:
```
 * Reconfiguring network interfaces...                                         RTNETLINK answers: No such process                                             
There is already a pid file /var/run/dhclient.eth0.pid with pid 4733           
killed old client process, removed PID file                                    
Internet Systems Consortium DHCP Client V3.1.1                                 
Copyright 2004-2008 Internet Systems Consortium.                               
All rights reserved.                                                           
For info, please visit http://www.isc.org/sw/dhcp/                             

Listening on LPF/eth0/00:15:f2:e4:d6:a5
Sending on   LPF/eth0/00:15:f2:e4:d6:a5
Sending on   Socket/fallback           
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable       
send_packet: please consult README file regarding broadcast address.
/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory                                   
Internet Systems Consortium DHCP Client V3.1.1                                 
Copyright 2004-2008 Internet Systems Consortium.                               
All rights reserved.                                                           
For info, please visit http://www.isc.org/sw/dhcp/                             

/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory                                   
Listening on LPF/eth0/00:15:f2:e4:d6:a5                                        
Sending on   LPF/eth0/00:15:f2:e4:d6:a5                                        
Sending on   Socket/fallback                                                   
receive_packet failed on eth0: Network is down                                 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7                     
send_packet: Network is down                                                   
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10                    
send_packet: Network is down                                                   
^C
```
(the last part was me using ctrl+c to stop it)

I don't know if this helps or not.

---

### Post by Zeikcied on 2009-08-04
Is there anything I can do short of reinstalling?

---

