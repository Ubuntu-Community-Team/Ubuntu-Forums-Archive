---
title: "2 routers, Can it be done?"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by 45-70 on 2010-04-26
I use 2 wireless routers to access all of my house.  My router connected to the modem is in the basement and I hard-wired a second router off of the first router to service upstairs a good distance from the basement.  With my windows machines I can walk anywhere in my house and connect to the network/internet.  

With my laptop running 9.10 I can only access the network/internet in the basement closest to the primary router.  If I go upstairs it shows connected(with good signal) but I am unable to get to the internet.  The second router is an old D-Link DI-524 with the latest firmware upgrade(2006).  If I swap the primary with the D-Link router I am unable to connect with 9.10.

Is there something I missed in the setup of the D-Link router, because my windows laptops sure don't care.

this is my first time playing around with Linux(Ubuntu) and everything worked great out of the box except when I went to take the computer upstairs.

Ryan

---

### Post by limey_rick on 2010-04-27
From what you describe you should be able to connect; I have the same setup at home. Upstairs the router is actually a wireless G, while downstairs, its wireless N. I don't seem to have any problems connecting to either. I have a DLINK 655 and Linksys WRTG65. The only difference I have is that the second router off the first upstairs connected as a wireless access point, not a router. 

Check to see if yours is setup as an access point, rather than a router as this may be the quick fix.

This would also explain (possibly) while this does not work when you sawp them as the other router should also be setup as a wireless access point. Most of the time the router documentation will tell you how to do this.

---

### Post by 45-70 on 2010-04-27
Thanks for the reply.  I am not sure why this laptop is not able to access to network/internet while my windows laptops have no problem.  Is the configuration as an access point different for ubuntu vs windows?

I am sitting here typing in the home office on a wireless connection from the primary router, which is a netgear router.  I am not super educated on network setup but have set on up every place I have lived in the last 7 yrs.  I would think that if it can connect as an access point with the windows machines then it should be set up for this machine.  

Side not the router is no longer supported by D-Link beyond archived material.

Ryan

---

### Post by limey_rick on 2010-04-27
Have you tried a wired connection with the upstairs router and Ubuntu laptop? 

What does ifconfig display of you type this into a command line?

---

### Post by 45-70 on 2010-04-27
Results:

eth0      Link encap:Ethernet  HWaddr 00:0e:7b:b2:23:03  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7bff:feb2:2303/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9416 (9.4 KB)  TX bytes:6186 (6.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:0e:35:33:38:86  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe33:3886/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100735 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:195008402 (195.0 MB)  TX bytes:9892051 (9.8 MB)
          Interrupt:11 Base address:0xe000 Memory:c2004000-c2004fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2531 (2.5 KB)  TX bytes:2531 (2.5 KB)


I did not have success with the hardwire either and I just checked my Windows Vista machine and it has no problems connecting to the internet via that router.

Ryan

---

### Post by limey_rick on 2010-04-27
So I am not a networking expert, but I have a connection called WLAN0 which is my wireless adapter:

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:3b:6e:c5  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5cff:fe3b:6ec5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16950627 (16.9 MB)  TX bytes:2606212 (2.6 MB)

Your output implies you have two hardwired adapters. Do you see the wireless icon in the top right of the display? If you right click, what connection information does it show? Sorry if this is an obvious question, but is Enable Wireless checked? Is there a wireless connection here you can edit. 

If you type lspci what output does it have for Networks? You may get a lot of output so 

lspci | grep -i net

I can see that Ubuntu sees my wireless adapter from the cut output below:

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by 45-70 on 2010-04-27
I am typing all this from a wireless connection and the ubuntu computer.  The problem is I have to stay close to the primary router.  If I go out of the range and get picked up by the D-Link router that is when I have problems.  If I stay downstairs I can do all the wireless I want.  If I go upstairs then it is a problem.  

The wireless works on the laptop as I am using it now I just can't get it to work with the D-Link DI-524 router when I go up stairs.  That screen shot is when I hooked up to the D-Link via a wire.  I am not sure if there is a compatibility issue with older routers or if I need to set something up in the laptop or router to get them to work.

Ryan

below is the results of lspci / ifconfig while typing on this wireless network:

ryan@Toshiba-laptop:~$ lspci | grep -i net
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)

ryan@Toshiba-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:7b:b2:23:03  
          inet6 addr: fe80::20e:7bff:feb2:2303/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9476 (9.4 KB)  TX bytes:6228 (6.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:0e:35:33:38:86  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe33:3886/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106841 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205660561 (205.6 MB)  TX bytes:10742242 (10.7 MB)
          Interrupt:11 Base address:0xe000 Memory:c2004000-c2004fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2531 (2.5 KB)  TX bytes:2531 (2.5 KB)

---

### Post by 45-70 on 2010-04-27
limey-rick  thanks for the help as it is getting late here on the east coast so I will play with the router some more tomorrow.  See if I can do some config that allows it to work.

Ryan

---

