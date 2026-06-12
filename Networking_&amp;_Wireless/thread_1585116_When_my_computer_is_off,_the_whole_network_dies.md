---
title: "When my computer is off, the whole network dies"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by jamessimo on 2010-09-30
I am on an Ubuntu 10.04 computer, I dont have any problems with internet access or anything. However when this computer is left plugged into the network hub (WIFI ROUTER) all the computers on the network (Wired and Wireless) loses connection to the internet. 

For now I simply leave my PC un-plugged from the network when I turn it off but I want it so It can be left in. I know Ubuntu is the problem because I duel boot a win7 system and when I power down in that the network is fine. 

Router: D-Link (Factory firmware, no mods)
OS: Ubuntu 10.04
Connections: 3 Wired, 2 or less wireless. 


Thank you and I hope theres a easy solution!

---

### Post by kreggz on 2010-09-30
Are you receiving your IP Address via DHCP or did you hardcode it?

---

### Post by grahammechanical on 2010-09-30
Hi

May I quote from the User Guide that came with my motherboard which has wireless built in (called WiFi-AP Solo)?

_Access Point Mode (AP Mode)_

If you wish to share the Internet access with wireless stations in your environment, you can configure the WiFi-AP Solo in an access point mode (AP Mode). In this mode, the WiFi-AP Solo becomes the wireless access point that provides local area network and Internet access for your wireless stations.

_Infrastructure mode_

An Infrastructure wireless network is centered on a wireless access point (AP) that provides Internet access and LAN communication for wireless stations. In Infrastructure mode, the wireless LAN stations communicate with each other via the wireless AP. In this mode, your WiFi-AP Solo acts as a wireless adapter. It communicates with the LAN computers and accesses Internet through the wireless AP.

_Ad-hoc mode_

In Ad-hoc mode, the WiFi-AP Solo acts as a wireless card and connects directly to other wireless device within its operating range. In Ad-hoc mode, your computer communicate with other wireless stations without an access point (AP)

Speaking from my inexperience I suggest that your computer must be set up in some way as the wireless Access Point (AP). Is it in AP mode? You want the modem/router to be the wireless Access Point. So your computer needs to be set up in either Infrastructure mode or Ad-hoc mode. All the other computers are getting their wireless access through your computer. This is what I would look at, anyway.

regards

---

### Post by jamessimo on 2010-09-30
> **kreggz said:**
> Are you receiving your IP Address via DHCP or did you hardcode it?

No, automatic DHCP.

---

### Post by kreggz on 2010-09-30
Try plugging in the Ubuntu machine and then pinging the default gateway on your other machine and see what happens.

Usually it is something like 192.168.0.1 or 192.168.1.1 but you will need to issue a ipconfig to confirm

---

### Post by Iowan on 2010-10-01
Something seems weird...
If you power down the machine from Windows, all is good... but if you power down the same machine from Ubuntu, the network hangs? :confused:

---

### Post by randomsrvapps on 2010-10-01
a few things which might be helpful;
-going to the dchp hosts list in your router configuration and see if the computers disappear when you use ubuntu  
-type "ifconfig" in terminal and reply with your LAN ip not your WAN ip not a good idea to post that here

also what router are you using? ive had problems myself running servers and do you have a dchp server installed on the ubuntu comp?

---

### Post by jamessimo on 2010-10-01
> **Iowan said:**
> Something seems weird...
If you power down the machine from Windows, all is good... but if you power down the same machine from Ubuntu, the network hangs? :confused:
Yep, weird ent it?

> **randomsrvapps said:**
> a few things which might be helpful;
-going to the dchp hosts list in your router configuration and see if the computers disappear when you use ubuntu  
-type "ifconfig" in terminal and reply with your LAN ip not your WAN ip not a good idea to post that here

also what router are you using? ive had problems myself running servers and do you have a dchp server installed on the ubuntu comp?
Im using a current gen D-Link Model - DIR-615

Ill find out how to check the dchp 
 on my router and post results.

---

### Post by jamessimo on 2010-10-19
Hey guys, sorry for the late reply. I have tryied allot of methods and to no avail. 

What I think I can confirm is that this is a case of ubuntu thinking its a DCHP server.  Does anyone know how to stop this?

---

### Post by mickwombat on 2010-10-20
Try doing ```
ps aux | grep dhcp
``` to see if the process is running.  If it is, then remove the package using Synaptic.

Change the dhcp scope on the router to something non-default, like 192.168.99.x.  On the windows machines do a ```
ipconfig /renew
``` and see what ip address they get.  If it is something other than 192.168.99.x, then they are getting their address from elsewhere, probably the Ubuntu box.

:)

---

### Post by jamessimo on 2010-10-20
> **mickwombat said:**
> Try doing ```
ps aux | grep dhcp
``` to see if the process is running.  If it is, then remove the package using Synaptic.

Change the dhcp scope on the router to something non-default, like 192.168.99.x.  On the windows machines do a ```
ipconfig /renew
``` and see what ip address they get.  If it is something other than 192.168.99.x, then they are getting their address from elsewhere, probably the Ubuntu box.

:)

I did have Grep DHCP installed, I removed it, changed the router to 99. Ipconfig showes it connected with the ubuntu box off but still falles over after about 10 mins. Cannot /renew after that.

---

### Post by CharlesA on 2010-10-20
Does the same thing happen if you boot from a livecd?

If it does, I'd reset the router to factory defaults and see if the same thing happens.

---

### Post by jamessimo on 2010-10-20
> **CharlesA said:**
> Does the same thing happen if you boot from a livecd?

If it does, I'd reset the router to factory defaults and see if the same thing happens.

I have already rest the router and I doubt it would happen if I booted it from a live cd and turned it off. 


I have avahi-autoipd installed. It seems optional and has something to do with DCHP. Can I delete this?

---

### Post by CharlesA on 2010-10-20
avahi gives you an APIPA ip address if it cannot contact a DHCP server, you can remove it or disable it if you want.

It doesn't make any sense that the network goes down when you shut off the machine and that it doesn't happen in Windows.

Unless the router isn't acting as a DHCP server and the machine you are powering off has that service installed and is acting as the main DHCP server, will you have that problem.

EDIT: Just reread the thread and something is definitely screwy.

What I would suggest doing is this:

Power off this one machine and try to ping the router and something like google.com from another machine and see what it says.

```
ping 192.168.0.1
```
```
ping www.google.com
```

If google isn't responding, try pinging this ip:
```
ping 209.85.225.106
```

That will see if name resolution is working correctly, or if there is another problem going on.

---

### Post by jamessimo on 2010-10-20
> **CharlesA said:**
> avahi gives you an APIPA ip address if it cannot contact a DHCP server, you can remove it or disable it if you want.

It doesn't make any sense that the network goes down when you shut off the machine and that it doesn't happen in Windows.

Does the same thing happen if you disconnect the machine from the network and then shut it off?

Unless the router isn't acting as a DHCP server and the machine you are powering off has that service installed and is acting as the main DHCP server, will you have that problem.

no, if i Disconnect my computer then turn off the network stays up. The router is also a DHCP server, because when I power down and unplug it takes over. 


Im gonna restart the router now, then turn off. hopefully maby the routers DHCP will take over and ubuntu will stop being a server .ill post results l8er.

---

### Post by CharlesA on 2010-10-20
> **jamessimo said:**
> no, if i Disconnect my computer then turn off the network stays up. The router is also a DHCP server, because when I power down and unplug it takes over. 

So the machine you are powering off has the DHCP server running on it?

---

### Post by jamessimo on 2010-10-20
ok, the machine is now down, currently still on net with webbook, pinging both router and google succesfully.

---

### Post by jamessimo on 2010-10-20
The internet fell over, after a while it blerted out

 ```
From 86.18.14.184 icmp_seq=280 Destination Host Unreachable
```

I could ping the router the whole time. 

I just unplugged the ubuntu and internet access was almost instant. 
 
I noticed that my machines port on the router was flashing like mad, like it was downloading a file or somthing. 

Grrrrr.

---

### Post by CharlesA on 2010-10-20
Yeah, it looks like it's not getting out of the network.

Can you post these commands from the machine that you are getting that error on:

```
ifconfig
```

```
route -n
```

---

### Post by jamessimo on 2010-10-20
I cannot believe this, I re-plugged in my OFF ubuntu and the network died again. 

Does this mean my hardware is taking somthing?

---

### Post by CharlesA on 2010-10-20
I kinda think that the router is freaking out, if it's not happening when not plugged in.

Can you post the output of the commands in my last post from a machine that can't get online?

---

### Post by jamessimo on 2010-10-20
```
jamessimo@jamessimo-laptop ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:12:1d:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9532 (9.5 KB)  TX bytes:9532 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:15:96:66  
          inet addr:192.168.99.82  Bcast:192.168.99.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe15:9666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28423734 (28.4 MB)  TX bytes:7590699 (7.5 MB)

jamessimo@jamessimo-laptop ~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.99.0    0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         192.168.99.1    0.0.0.0         UG    0      0        0 wlan0
jamessimo@jamessimo-laptop ~ $ 

```

---

### Post by CharlesA on 2010-10-20
That looks right. Is that machine able to ping google.com?

---

### Post by jamessimo on 2010-10-20
```
jamessimo@jamessimo-laptop ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:12:1d:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9532 (9.5 KB)  TX bytes:9532 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:15:96:66  
          inet addr:192.168.99.82  Bcast:192.168.99.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe15:9666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28423734 (28.4 MB)  TX bytes:7590699 (7.5 MB)

jamessimo@jamessimo-laptop ~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.99.0    0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         192.168.99.1    0.0.0.0         UG    0      0        0 wlan0
jamessimo@jamessimo-laptop ~ $ 

```

---

### Post by CharlesA on 2010-10-20
Looks fine, Try doing this:

```
ping -c 4 192.168.99.1
```
```
ping -c 4 google.com
```

---

### Post by jamessimo on 2010-10-20
> **CharlesA said:**
> Looks fine, Try doing this:

```
ping -c 4 192.168.99.1
```
```
ping -c 4 google.com
```


```
jamessimo@jamessimo-laptop ~ $ ping -c 4 google.com

ping: unknown host google.com

jamessimo@jamessimo-laptop ~ $ ping -c 4 192.168.99.1
PING 192.168.99.1 (192.168.99.1) 56(84) bytes of data.
64 bytes from 192.168.99.1: icmp_seq=1 ttl=64 time=1.07 ms
64 bytes from 192.168.99.1: icmp_seq=2 ttl=64 time=0.707 ms
64 bytes from 192.168.99.1: icmp_seq=3 ttl=64 time=0.804 ms
64 bytes from 192.168.99.1: icmp_seq=4 ttl=64 time=0.888 ms

--- 192.168.99.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 0.707/0.868/1.076/0.140 ms

```

---

### Post by CharlesA on 2010-10-20
Ok, it looks like it's not resolving the name.

Can you run this and then post the output:

```
ping -c 4 74.125.95.104
```

```
cat /etc/resolv.conf
```

---

### Post by jamessimo on 2010-10-20
> **CharlesA said:**
> Ok, it looks like it's not resolving the name.

Can you run this and then post the output:

```
ping -c 4 74.125.95.104
```

```
cat /etc/resolv.conf
```

```
jamessimo@jamessimo-laptop ~ $ ping -c 4 74.125.95.104
PING 74.125.95.104 (74.125.95.104) 56(84) bytes of data.
From 86.18.14.184 icmp_seq=3 Destination Host Unreachable
From 86.18.14.184 icmp_seq=4 Destination Host Unreachable

--- 74.125.95.104 ping statistics ---
4 packets transmitted, 0 received, +2 errors, 100% packet loss, time 3000ms



jamessimo@jamessimo-laptop ~ $ cat /etc/resolv.conf
# Generated by NetworkManager
domain cable.virginmedia.net
search cable.virginmedia.net
nameserver 192.168.99.1


```

Does the cat /ect/resolv need to be run when the network is down? that one was run when the network was up (got a house full of people who need the net up)

---

### Post by CharlesA on 2010-10-20
It looks like it's having problems again. resolv.conf looks ok, but I don't know what is causing the problem tbh.

You lose internet access when that machine is hooked up to the router, right?

Are you using MAC address cloning on the router by chance?

EDIT: resolv.conf shouldn't change, so it doesn't matter.

What I think is happening is this: When that machine is off and plugged in, there is some sort of conflict occurring so it's not letting you send traffic onto the internet.

Can you do an ```
arp -n
``` and see what it says?

---

### Post by jamessimo on 2010-10-20
> **CharlesA said:**
> It looks like it's having problems again. resolv.conf looks ok, but I don't know what is causing the problem tbh.

You lose internet access when that machine is hooked up to the router, right?

Are you using MAC address cloning on the router by chance?

EDIT: resolv.conf shouldn't change, so it doesn't matter.

What I think is happening is this: When that machine is off and plugged in, there is some sort of conflict occurring so it's not letting you send traffic onto the internet.

Can you do an ```
arp -n
``` and see what it says?


```
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.99.83            ether   70:1a:04:2a:89:7e   C                     wlan0
192.168.99.1             ether   1c:bd:b9:a6:ae:9c   C                     wlan0

```

I am not Mac cloning, my router does allow it but its not enabled. thanks btw for the support so far!
(this was done with internet accsess, room mates ask that it stays up for a sec, if needed I can crash it.)

---

### Post by CharlesA on 2010-10-20
That looks fine. It's so puzzling. When you get a chance, I would disconnect all the machines from the router, do a factory reset and power cycle both the router and the dsl or cable modem.

After that's done, Hook up each machine individually and see if they can access the internet. If they can, add them one at a time and see what happens.

It's so puzzling since this sort of thing isn't supposed to happen if you have one machine off. The router should be smart enough not to send any packets to the machine that is off.

I've got a Dlink DIR-615 and it worked fine for me.

EDIT: When you don't have internet access, you can try running this (you may need to install traceroute when you have internet access):

```
traceroute 74.125.95.104
```

See if it's going anywhere.

---

### Post by jamessimo on 2010-10-20
> **CharlesA said:**
> That looks fine. It's so puzzling. When you get a chance, I would disconnect all the machines from the router, do a factory reset and power cycle both the router and the dsl or cable modem.

After that's done, Hook up each machine individually and see if they can access the internet. If they can, add them one at a time and see what happens.

It's so puzzling since this sort of thing isn't supposed to happen if you have one machine off. The router should be smart enough not to send any packets to the machine that is off.

I've got a Dlink DIR-615 and it worked fine for me.

I think I will have to. this is sooo annoying! >_< ill also swap the cables just to make sure it isnt something stupid. thanks again.

---

