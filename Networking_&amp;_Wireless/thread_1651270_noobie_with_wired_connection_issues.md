---
title: "noobie with wired connection issues"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by wsky tngo on 2010-12-22
Hello, I am a new user to Ubuntu.  I started out using linux Mint a year ago and have since migrated to Ubuntu 10.04.  I have found it very fun to use, have learned alot about linux and computers in general just from using this distro.  I currently am running a wired dsl connection with no router in between.  I would how ever like to use a router in my setup and so far am not successful.  I have installed the router and can access the setup of the router by typing 192.168.0.1 (the router is a D-link DI-624) in the address bar.  I have setup the router and can ping websites successfully but am not able to browse the internet on my desktop.  I am sure that I am missing some vital step, but for the life of me I cannot get it figured out.  I have tried editing the hosts file, and some others too.  Still no dice.

---

### Post by pytheas22 on 2010-12-22
Are you using dynamic IP addresses served via dhcp, or static IPs?  If the latter, are you sure you set up all of the routing configuration properly?  For connecting to websites, it's not enough just to tell Ubuntu the IP address of the router; you also need to set the gateway and netmask properly (without these you would still be able to ping the router itself and access its configuration page from a Web browser, but you wouldn't be able to reach external websites).

It could also be a DNS issue.  Do you have a valid DNS server configured in your /etc/resolv.conf file, and are you sure you can ping that server from your Ubuntu computer?

The problem could also lie on your router's end, rather than Ubuntu's.  I would try plugging a Windows computer into the router to see if it can reach external websites.  If it also fails, I'd make sure the router is configured to route traffic properly, etc. (if you think it's a problem with the router, it would be helpful to know what kind it is and so on).

I can think of more questions to ask regarding what could be going wrong, but hopefully one of these will point you in the right direction.

---

### Post by nova47 on 2010-12-22
I have never tried this myself but intuition would tell me that if you are able to ping websites successfully you may try typing in their ip address into your web browser rather than their domain name. If you successfully get to the website you know you have a DNS issue and if you don't you still don't know what your issue is.

I've never used d-link routers myself but you may also try a sanity check on your network settings. Try opening up a command window (not sure how new you are so sorry if I'm about to insult your intelligence :-p) a command window is the little black box at the top of the screen. If you type ifconfig it should display all the information for your network adapters. You said you are using a wired connection so chances are the name of the connection you are looking for is something like eth0. Your ip address should be something like 192.168.0.XXX where the Xs are some random looking numbers. If you want go ahead and post the results of your ifconfig.

---

### Post by wsky tngo on 2010-12-23
Sorry guys I guess I should have mentioned that the connection is dynamic and not static.  I will post the results of ifconfig now.

whiskey@whiskey-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:06:bf:9a  
          inet6 addr: fe80::215:f2ff:fe06:bf9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64520732 (64.5 MB)  TX bytes:17959740 (17.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1168 (1.1 KB)  TX bytes:1168 (1.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:216.137.225.93  P-t-P:216.137.225.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:62048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62523 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:43816178 (43.8 MB)  TX bytes:10775500 (10.7 MB)

whiskey@whiskey-desktop:~$ 

I have been able to use a windows computer with the router successfully, so I think the problem may lie with not properly setting up the gateway and net mask.  If someone would mind helping me do so, I would be very appreciative.  Thank you for the quick reply on this too.

---

### Post by pytheas22 on 2010-12-23
Thanks for the information.  If the connection is dynamic, you should not need to set a gateway and netmask; dhcp (the program that fetches a dynamic IP address for you) will take care of this on its own.  So that doesn't seem likely to be the issue.

What does look strange from your output above, however, is that you have an address configured for the interface ppp0, but not for eth0.  It's hard to know for sure without knowing exactly how your network is set up, but in most cases, if you're behind a router, I'd expect eth0 to be receiving the IP address, not ppp0.  ppp0 would probably only be used if you're connecting the Ubuntu computer directly to the Internet, without a router in between.

So, I'd try deactivating the ppp0 interface, and then trying to get an IP address on eth0.  You should be able to do this using the graphical interface provided by the NetworkManager applet in the upper-right corner of your screen, or you can do it in the terminal by running:

```
sudo dhclient -r ppp0 # drop address assigned to ppp0, if it was set dynamically
sudo ifconfig ppp0 down # disable ppp0
sudo ifconfig eth0 up # put ppp0 up (it probably is already, but we do it again just to be safe)
sudo dhclient eth0 # request an IP via dhcp on eth0
```

If this works, you should get a message telling you that eth0 has been granted an IP address from your router, and you should then be able to browse normally.  Please let us know.  If this fails, please post the output of the commands above, along with that of:
```

route
ifconfig
ifconfig -a
```

---

### Post by wsky tngo on 2010-12-23
Well, I started having issues right off the bat with dhclient here is the results 

sudo dhclient -r ppp0
[sudo] password for whiskey: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

ppp0: unknown hardware address type 512
ppp0: unknown hardware address type 512
Listening on LPF/ppp0/
Sending on   LPF/ppp0/
Sending on   Socket/fallback
whiskey@whiskey-desktop:~$ sudo dhclient -r ppp0 216.137.225.93
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

ppp0: unknown hardware address type 512
ppp0: unknown hardware address type 512
Bind socket to interface: No such device
whiskey@whiskey-desktop:~$ 


As you can see initially I forgot to put in an address here so I redid it and it still did not yield good results.  Yes right now my computer is connected directly to the internet, but the connection I want to set up is where the computer is behind a router so that I can have the desktop as  a wired connection and also run a wireless setup for my laptop so that I can play with networks in Ubuntu and learn more.

---

### Post by wsky tngo on 2010-12-23
Also, I am not too sure I put in the right address in the dhclient command you gave me.  Sorry I am definately still in noob status here.

---

### Post by pytheas22 on 2010-12-24
You shouldn't actually need to specify an IP address when running "sudo dhclient -r ppp0", and it looks like the command ran as expected the first time.  (I am not sure why it complained about an "unknown hardware address," but it doesn't appear to have been a fatal error.)  Did you try running "sudo dhclient eth0", and if so did it fetch an IP address for you?  That's really the most important question.

Of course, in order to get an IP address on eth0, your computer needs to be plugged into the router, rather than directly connected to the Internet.  That is your goal, right?  Or am I misinterpreting what you're trying to do?  I ask only because I'm not sure why you still have the computer connected directly to the Internet, if your goal is to place it behind the router.

Just so it's clear: if your router is configured to serve addresses dynamically via dhcp (which it probably is if you just plugged your Windows computer in and it got connected on its own), then you shouldn't have to do anything on Ubuntu in order to get connected behind the router, other than plugging the Ubuntu computer into the router: it should be "plug and play," just like Windows.  Running the command "sudo dhclient eth0" will fetch you an address manually, but even this should not be necessary (I asked you to do it above only for testing purposes), as NetworkManager in Ubuntu should automatically run dhclient for your whenever it detects that you're plugged into the router.  Maybe this is the source of the confusion?

If Ubuntu doesn't get an IP address on eth0 after you plug the desktop into the router, or if it gets an address but you still can't browse websites, then something's wrong.  In that case, it would be good to see the output of these commands *after* you're plugged into the router, and have disabled your direct connection to the Internet:
```

ifconfig
ifconfig -a
ping -c 3 google.com
ping -c 3 72.14.204.104
```

---

### Post by wsky tngo on 2010-12-24
Ok, so I connected the router, ran the commands and this is what I got.  And yes you are correct that the goal is to have the desktop behind a router.  

whiskey@whiskey-desktop:~$ sudo dhclient -r ppp0 
[sudo] password for whiskey: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Bind socket to interface: No such device
whiskey@whiskey-desktop:~$ sudo ifconfig ppp0 down
ppp0: ERROR while getting interface flags: No such device
whiskey@whiskey-desktop:~$ sudo ifconfig eth0 up
whiskey@whiskey-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:15:f2:06:bf:9a
Sending on   LPF/eth0/00:15:f2:06:bf:9a
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.102 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.102 from 192.168.0.1
bound to 192.168.0.102 -- renewal in 292109 seconds.
whiskey@whiskey-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         whiskey-desktop 0.0.0.0         UG    0      0        0 eth0
whiskey@whiskey-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:06:bf:9a  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe06:bf9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81832128 (81.8 MB)  TX bytes:29876186 (29.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1168 (1.1 KB)  TX bytes:1168 (1.1 KB)

whiskey@whiskey-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:f2:06:bf:9a  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe06:bf9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81832128 (81.8 MB)  TX bytes:29876593 (29.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1168 (1.1 KB)  TX bytes:1168 (1.1 KB)

whiskey@whiskey-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:06:bf:9a  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe06:bf9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81834470 (81.8 MB)  TX bytes:29892272 (29.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10320 (10.3 KB)  TX bytes:10320 (10.3 KB)

whiskey@whiskey-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:f2:06:bf:9a  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe06:bf9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81834470 (81.8 MB)  TX bytes:29892848 (29.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10320 (10.3 KB)  TX bytes:10320 (10.3 KB)

whiskey@whiskey-desktop:~$ ping -c 3 google.com


ping: unknown host google.com
whiskey@whiskey-desktop:~$ 
whiskey@whiskey-desktop:~$ 
whiskey@whiskey-desktop:~$ ping -c 3 72.14.204.104
PING 72.14.204.104 (72.14.204.104) 56(84) bytes of data.

--- 72.14.204.104 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

whiskey@whiskey-desktop:~$

---

### Post by pytheas22 on 2010-12-26
Thanks again for the output, and sorry not to get back to you sooner.

From everything you posted, it looks like you're not having a problem getting an IP address from the router, nor do I see any other obvious reason why traffic to external websites is not going through.  The routing table looks alright to me, and it doesn't appear to be a DNS issue because pinging Google's IP address directly fails (as does pinging google.com).

Are you able to ping the router itself after plugging your Ubuntu computer into it and fetching an IP address with the "sudo dhclient eth0" command?  The command to ping your router would be:
```

ping -c 3 192.168.0.1
```

(This assumes that the router has IP address 192.168.0.1.)

If you can ping the router but not external websites, I'd take a closer look at the router configuration to be sure there's not a problem there.  Resetting it (usually there's a button on the router that you can press to do this) may also not hurt.

Also, when you plug the Ubuntu computer into the router, does a message appear for a few seconds in the upper-right corner of the screen telling you you're connected?  This should happen, because NetworkManager should auto-connect you whenever it detects a new connection available, but if that's not working, that could be something to check on further.

---

### Post by wsky tngo on 2010-12-31
> **pytheas22 said:**
> Thanks again for the output, and sorry not to get back to you sooner.

From everything you posted, it looks like you're not having a problem getting an IP address from the router, nor do I see any other obvious reason why traffic to external websites is not going through.  The routing table looks alright to me, and it doesn't appear to be a DNS issue because pinging Google's IP address directly fails (as does pinging google.com).

Are you able to ping the router itself after plugging your Ubuntu computer into it and fetching an IP address with the "sudo dhclient eth0" command?  The command to ping your router would be:
```

ping -c 3 192.168.0.1
```(This assumes that the router has IP address 192.168.0.1.)

If you can ping the router but not external websites, I'd take a closer look at the router configuration to be sure there's not a problem there.  Resetting it (usually there's a button on the router that you can press to do this) may also not hurt.

Also, when you plug the Ubuntu computer into the router, does a message appear for a few seconds in the upper-right corner of the screen telling you you're connected?  This should happen, because NetworkManager should auto-connect you whenever it detects a new connection available, but if that's not working, that could be something to check on further.

Very sorry for the later reply, the holiday season hit and I was not able to make any headway on this.  Ok so, I ran the sudo dhclient eth0 command and got an address of 192.168.0.102 and then I used the ping -c 3 192.168.0.102 command and it was successful.  When I plug into the router the manager attempts to connect to the wired connection automatically but fails.  If you want me to I can attempt to reset the router and go from there?

---

### Post by pytheas22 on 2011-01-05
So sorry to reply so late--your last response accidentally got marked as "read" in my subscribed threads list and I didn't realize till now that I'd failed to respond to it.

Since it does seem that you're able to pass traffic successfully between the Ubuntu computer and the router, I suspect that there's a configuration issue within the router itself that's preventing it from passing that traffic on to external websites.  I'd check the router configuration again; in particular, look for settings related to "NAT" and make sure it's enabled.  Resetting the router could also not hurt, as long as you know how to make any manual configurations to it that are necessary after resetting it (in most cases you shouldn't have to change anything, but on some routers you may have to enter information to tell it how to connect to your ISP, etc.)

You may also want to look, if you haven't already, at [this thread]("http://ubuntuforums.org/showthread.php?t=641466"), where someone has strange issues connecting via wire to the same router model as you.  There's no real solution there, unfortunately, although the suggestion of updating the firmware might be worth a try.

Another thing that could be helpful is to check the router logs.  I'm not sure where exactly these are, but you should be able to find them under the Web administration interface somewhere (you may need first to turn logging or, if it's disabled by default).  If you can read the log, see if it says anything that looks interesting, or feel free just to post it here.

---

