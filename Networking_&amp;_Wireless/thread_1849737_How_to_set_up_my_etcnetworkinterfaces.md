---
title: "How to set up my /etc/network/interfaces"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by laurieturpin on 2011-09-25
Hello

I am trying to set up a home network with a server and desktop pc.
The server ip address is 192.168.1.2 and the address of the desktop is 192.168.1.3 They are both connected to a router which is connected to my ISP to give me internet access. The ISP uses DHCP to give me my internet connection. 

The problem is that I seem to require both DHCP and a static interfaces The connection between the desktop and my home server needs to be static but not stop me connecting to the internet.

I'm not sure how to set up my interfaces file in /etc/network/interfaces

At the moment I have it as:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
      address 192.168.1.2
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255 

Is this correct?
If I change the word dhcp to static the internet connection stops working.

---

### Post by sanderj on 2011-09-25
What is the reason you are manually editing the config files?

I would do it this way:

Most routers allow to "fix" a certain IP address to a certain device (MAC address), still via DHCP. That's the best solution: your computers just use plain DHCP, and if you take your laptop to another network, it will still get and use a correct IP address via DHCP.

If your router doesn't offer that function, you can take care of it on your Ubuntu machine: start Network Connections, and under the IPv4 tab say that you want to manually specify your IP address.

---

### Post by praseodym on 2011-09-25
If the router is working with DHCP then your fixed IP should be out of the IP range of the router.

---

### Post by Bucky Ball on 2011-09-25
Yea, the ISP uses DHCP to serve your ***router ***a fresh IP whenever it logs on (the WAN, wide area network, side), but anything on the LAN (local area network) side is up to you. Your router needs to deal with communicating with the ISP on the WAN side, but can then serve your home network machines via DHCP independently of all that if that what you want. They're not connected, so to speak. 

Machines on your LAN side static. Easier that way (DHCP on the router off) and let the router and your ISP take care of connecting to the WAN. Your gateway out from your local machine is the fixed IP address of your router which you can change if you want. That is all you need worry about.

At home I have static IPs set on all local machines (not the router assigning them static IPs, it is just a conduit in this case) and the router's DHCP server on for visitors but serving outside the range of my static addresses.

Hope that gives you some ideas. The KIS principle is a must when doing this stuff (keep it simple). A piece of paper and pencil may seem quaintly old fashioned but very handy for mind-mapping/mud-mapping your setup before you dive in assigning IPs, etc ...

Basically, if you want to setup your interfaces the easy way, just right click the network icon and choose 'Edit Connections'. Do all your setup there. You are connected either by wireless or wired? Go to that interface and setup the static IP with the gateway as the IP of your router. You are going to need the IPs of the DNS servers of your ISP (they will give you that if they haven't already). Then you're away (as long as your modem is plugged in and saying it is online and your router is plugged into that). 

Make the desired setup on every machine then go for it. ;) 

Good luck.

ps: Bottom Line: you don't have to worry about the fact your ISP serves the router an IP to get online (WAN) via DHCP. That has nothing to do with what you are attempting as you are on the other side of the wall, so to speak (LAN).

---

### Post by laurieturpin on 2011-09-25
Thank you for your replys guys.

BuckyBalls you seem to have a home network similar to what I want. The /etc/network/interfaces file is on my server and desktop. The router does not have a way to set an ip addresses. It's really an adsl set top box with 4 ethernet ports for connecting up other desktops. So I can have up to 4 machines in all. But at the moment I am only using two machines. 

How should I set up the /etc/network/interfaces file?

How do you have yours?

---

### Post by chili555 on 2011-09-25
I suggest this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1 
```As praseodym says, the static addresses need to be outside the range used by the router for DHCP. For example, if the router (in your case, the DSL appliance supplied by your ISP) assigns DHCP addresses from 192.168.1.2 to 192.168.1.50, for example, use static addresses from x.51 on up.

If you have Network Manager installed, you will find the process difficult unless you Edit Connections in NM and set the details there. Please see attached.> What is the reason you are manually editing the config files?I think there are two reasons. If a server is running headless, without a desktop manager, there is no other way to do it. Running headless means no keyboard, monitor and mouse. It means the overhead imposed by a windowing manager is lifted and, best of all, you can stick the thing in a closet or garage.

Also, many of us prefer to do things our own way, not the regimented Unity/Gnome/KDE/etc. way.

---

### Post by Bucky Ball on 2011-09-25
Chilli555 says it all. ;)

All the info you need is there and chilli's provided the static setup for a wired connection as opposed to the wireless setup I PMed you. ;)

And the screen shot of chilli's network manager also explains what I was saying about doing things in network manager. That will write directly to your /etc/network/interfaces file. One thing. At the bottom of that screenshot, chilli555 has 'Available to all users' unchecked. For some of us that needs to be checked. You might try that, too, if you're pretty sure you have the rest set up right and still not working.

---

### Post by laurieturpin on 2011-09-26
Thank you guys for your time a patience.
I know now that the setup is considerably easier than I thought.
My dlink router sorts everything out for me. If I leave the domain name as dlink.com and set server1 and client1 to dhcp.
In other words if client1 and server1 and left in the setup the default to when ubuntu is installed every works.
My reason for not having a gui on the server is it is quite an old pc that I'm using as a server. 
Secondly by default when you install Ubuntu server it doesn't have a gui by default.
Thirdly once the server is up and running you can install webmin and administer the server via a web browser. client1 in duel boot with both unbuntu desktop and windows 7.

---

