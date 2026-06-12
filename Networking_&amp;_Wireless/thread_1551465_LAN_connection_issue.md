---
title: "LAN connection issue"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by Krissi on 2010-08-12
Just installed 10.04 on a Toshiba Portege laptop. Everything works fine except the LAN connection. Just doesn't connect. Based on what I know everything is on and enabled but no luck. The wireless works fin but can't connect to the network in my office through the standard cable. Installed the same operating system on a newer Toshiba (the second is my but the older one is a friends) and no issues at all. Wondering if it is a driver issue but can't figure it out. Am relatively new to Ubuntu but so far have found it easy to troubleshoot just reading posts and just trying out **** until it works. But this I've hit a brick wall.

Also ran in to a similar issue my work pc, except I had been working with it fine with 10.04 until I did a security update and puff... no more network.

Any ideas on where to start?

The eth1 connection is enabled and set to automatic but just can't connect to it. Sorry if I'm not providing enough info, just tell me if there is anything you need to know first and I'll post it.

thanks guys

---

### Post by Kerubu on 2010-08-12
> **Krissi said:**
> Just installed 10.04 on a Toshiba Portege laptop. Everything works fine except the LAN connection. Just doesn't connect. Based on what I know everything is on and enabled but no luck. The wireless works fin but can't connect to the network in my office through the standard cable. Installed the same operating system on a newer Toshiba (the second is my but the older one is a friends) and no issues at all. Wondering if it is a driver issue but can't figure it out. Am relatively new to Ubuntu but so far have found it easy to troubleshoot just reading posts and just trying out **** until it works. But this I've hit a brick wall.

Also ran in to a similar issue my work pc, except I had been working with it fine with 10.04 until I did a security update and puff... no more network.

Any ideas on where to start?

The eth1 connection is enabled and set to automatic but just can't connect to it. Sorry if I'm not providing enough info, just tell me if there is anything you need to know first and I'll post it.

thanks guys

First thing, make sure your wired ethernet is recognised. Issue the following command :

ifconfig

And post the results here. You should get something like this (this is the result on my machine) :

> eth0      Link encap:Ethernet  HWaddr <** REMOVED BY ME **>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr <** REMOVED BY ME **>  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: <** REMOVED **> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8324374 (8.3 MB)  TX bytes:2099410 (2.0 MB)


Note : I have removed my hardware addresses from the above output

---

### Post by Krissi on 2010-08-17
laptop:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:1c:7e:72:d2:22   
           inet6 addr: fe80::21c:7eff:fe72:d222/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:480 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:9 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:10  
           RX bytes:50258 (50.2 KB)  TX bytes:1494 (1.4 KB)  
           Memory:ff9e0000-ffa00000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:28 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:28 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:2016 (2.0 KB)  TX bytes:2016 (2.0 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:9d:15:c7   
           inet6 addr: fe80::21d:e0ff:fe9d:15c7/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:11 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:3754 (3.7 KB)  TX bytes:2376 (2.3 KB) 



Sorry for the late reply, didn't get the laptop back till today. this is the message, connection is there but doesn't allow me to connect. Really, this is strange, just loaded Ubunto on to a 5 year old laptop, no bloody problems what so ever.


What would be the next step? By they way, your help won't be in vane, I'm putting ubunto on to all the pc's here at work and getting more and more people on it every week so any troubleshooting I can learn will just make it easier for me to "spread the word" of the holy ubuntu gospel ;)

---

### Post by grahammechanical on 2010-08-17
I am no expert. My only experience with networks is the connection to the router/modem by wire and wireless for the internet.

It does seem that some updates to 10.4 disable networking. Right click the network manager and see if networking is enabled. If not click on "Enable networking."

I have little knowledge of networks such as the one being used in your place of work but it seems to me that it is very poor security to allow anyone to plug a portable computer into the network with a ethernet cable and give them access to files on the company's computers. I doubt very much if you need drivers for ethernet. Wireless may be. Remember that Linux starts off as a very secure operating system. You may need to set up a VPN connection. This means (I think) a Virtual Private Network. How to do it and what it is, I do not know. I am guessing that the built-in security features of Ubuntu-Linux will not let you just connect to a network by plugging in a cable.

The good news is that by the time you figure all this out and get things working at your place of employment, you will be some kind of expert on this stuff. I just hope your employer appreciates you.

Regards.

---

### Post by Krissi on 2010-08-17
Well, the company is small, 10 employees and I'm one of the partners and the only one with any notion of IT. I'm a quick learner though and can usually feel my way through (been running our network for 7 years on windows systems as well as actually wiring it my self) but sometimes I do hit a brick wall and this is one of them and the funny thing is that I've had little or no issues with most of the ubuntu operating systems i've loaded and plugged in to our network. Depending on the pc or laptop it deals with it differently so I'm sure its just the hardware makeup reacting differently. The network is enabled, the idiot stuff I've done, but still no cigar. It does connect to home wireless networks though.

I guess I'd like to be able to figure this one out because I'm positive I'll run in to it in the future. Don't want to waist anyones time though so please don't let me if you feel I'm not providing enough info to solve the issue. I do think between the previous version (9.40 I think) and 10.04 there were some fundamental changes that cause problems in older hardware but not all. But that is just a gut feeling and lets face it, my guts have **** for brains. Appreciate the help so far and if anyone has any further suggestions I'm all ears.

thanks

---

