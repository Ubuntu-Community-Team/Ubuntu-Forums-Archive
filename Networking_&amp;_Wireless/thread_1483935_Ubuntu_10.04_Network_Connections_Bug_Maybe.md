---
title: "Ubuntu 10.04 Network Connections Bug Maybe?"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by songbreaker on 2010-05-15
Hey all,
I installed the latest Ubuntu distro and it was an amazing experience for me. Last time I installed a Ubuntu was 7+, which was years ago.

However, I found out there is maybe bug in the network connections. If I used static IP setup the connection works but if I use dynamic IP , it goes haywire. The network manager that comes with the distro takes a very long time to connect and end up fails.  This applied to both wired and wireless connection. 

Switching network manager to WCID shows you what exactly happens. It is not because of the system fails to authenticate with the wireless WEP/WPA , instead it takes horrible amount of time for it to obtain IP address and ends up timeout. If you happen to have this type difficulties, try to install WCID and get the connection running. You will see that it ends up at "Obtaining IP" phase.

And no, the router is not broken. I tested it out using my WIndows systems and it works just fine.

I m not sure if this issue being raised, but it worth to mention it here in case if someone runs into. Do not panic, your networking hardware is fine. Maybe it is something with the latest Linux kernel or drivers in the distro.

Just my 2cents, and of course if you have the solution post it here!

---

### Post by Darktrax on 2010-05-31
> **songbreaker said:**
> 
However, I found out there is maybe bug in the network connections. If I used static IP setup the connection works but if I use dynamic IP , it goes haywire.

No - you are not imagining things

This older installation (9.10) has a working internet connection.

The attempt to install 10.04 (Lucid) in the "Ubuntu Studio" distribution on another partition results in a new Lucid desktop with no idea of the router, and a 3-tab tool that offers no way of actually configuring it to work - no mention of DHCP .. just a way to set aliases, and the "help" document describes a 4-tab tool of different abilities. Even that is basically a list of qualitative titles that do not state **exactly** the actions required with examples.

So try again for 10.04 on a laptop using the regular Ubuntu 10.04 install.

Again - no way to get the network running..

Its not as if I have not managed to do it before. I have been running various flavours of Linux for years. This time, I have hit a frustrating block. Why is it so tough to set the thing up if my if my NetGear modem router offers DHCP and is known to whatever connects to it as the 192.168.0.1 gateway? Even the LiveCDs can find their way there without help.

So far - its a deal-breaker. No network .. no distro!

---

### Post by necromonger on 2010-05-31
> **Darktrax said:**
> No - you are not imagining things

This older installation (9.10) has a working internet connection.

The attempt to install 10.04 (Lucid) in the "Ubuntu Studio" distribution on another partition results in a new Lucid desktop with no idea of the router, and a 3-tab tool that offers no way of actually configuring it to work - no mention of DHCP .. just a way to set aliases, and the "help" document describes a 4-tab tool of different abilities. Even that is basically a list of qualitative titles that do not state **exactly** the actions required with examples.

So try again for 10.04 on a laptop using the regular Ubuntu 10.04 install.

Again - no way to get the network running..

Its not as if I have not managed to do it before. I have been running various flavours of Linux for years. This time, I have hit a frustrating block. Why is it so tough to set the thing up if my if my NetGear modem router offers DHCP and is known to whatever connects to it as the 192.168.0.1 gateway? Even the LiveCDs can find their way there without help.

So far - its a deal-breaker. No network .. no distro!

What version Is your router?

---

### Post by Darktrax on 2010-05-31
> **necromonger said:**
> What version Is your router?
Its a NetGear RangeMax ADSL Wireless Modem Router, and the PC is using one of the cabled connections.
..but thats not the point. We know it works fine with this KARMIC 9.10 !

I think the best plan is to write down the setup on this version, and try to enter it into the LUCID 10.04. The LUCID net setup tool seems to be a "dumbed down" variant with fewer tabs and configuration choice options, and is somewhat IPV6 centered.

The "Network Tools" administration tool provides information - not configuration (unless my explorations somehow missed an opportunity!)

I was trying hard to find anything that would give me options to try and change something. I would have tried anything that gave a response of any sort. It asks for the authorization password often enough - but no clues as to what specifically to do, or how.

Opening a terminal, then "***sudo su***" followed by password to get a #root terminal, then try "***ifconfig***" delivers **much** more information.

Then "***#ping -c 2 192.168.0.1 ***" will tell if the network **can** see the router at all

The DNS server addresses are easy, and almost any would do, though there seems no easy way to set that the 192.168.0.1 is supposed to be the gateway. One has to remember that all these opearations have to be done on a non-communicating PC. Looking up help requires re-boot to the older working version.

What I don't get is that the older 9.10 (this KARMIC) did it all by itself, using the DHCP access that all the others use, without problems.
If there is somewhere the command or tool to do the automatic setup from scratch, I should like to find it.

---

### Post by Darktrax on 2010-05-31
OK - It would seem that the Network Manager tool is somewhat bugged.
I am not the only one to discover that manual configuration of IP address etc. just doesn't work.
*ref:* [http://www.groupsrv.com/linux/post-926164.html]("http://www.groupsrv.com/linux/post-926164.html")

Enter what you like - it goes nowhere, or makes a mess.

When you can ping the router, and still Firefox is setting to "offline", you know things are not right.

**Edit:**  I had to give this one up. The move from having the network set-up in a configuration file, to making it happen by executable scripts and symlinks is now a thing of such complexity that if the default is broken, your average application user is unlikely to fix it with the limited functions in  tools offered. There comes a point where one has to acknowledge this already very low probability is still getting smaller.

---

### Post by arunarun4 on 2010-06-03
Hi all..
May be this can help you connect to Internet through ethernet.

[COLOR=Red]*ifconfig -a | grep eth*[/COLOR]
This will give you the ethernet details. Be sure to check the number after "eth"; ie "eth0". "eth1". And that is your ethernet port. This is applicable to all further commands.

[COLOR=Red]*sudo ifconfig eth0 10.0.0.100 netmask 255.255.255.0*[/COLOR]
This will create a temporary ip. 
[I]
[COLOR=Red]ifconfig eth0[/COLOR][/I]
Use this to verify the configuration. 

[COLOR=Red]*sudo route add default gw 10.0.0.1 eth0*[/COLOR]
This will create a default gateway.

[COLOR=Red]*sudo gedit /etc/network/interfaces*[/COLOR]
This will open the interfaces file
Add the following to the end of the file. Be sure to add your port number (eth?)
[COLOR=Red][I]auto eth0
iface eth0 inet dhcp[/I][/COLOR]

[COLOR=Red]*sudo ifup eth0*[/COLOR]
This will enable the settings

This is a small information I got from the help and support in Ubuntu 10.04. I was able to connect to Internet with the help of these commands. Please try it . I'm sorry if this doesn't solve your problem. I'm a newbie to ubuntu 10.04.

Thank you all :)

---

### Post by Darktrax on 2010-06-06
arunarun4,

Thanks much for your input.
As it happens, my PC has two network sockets. I found that to get it going, it had to be eth1, which I did with..
*[COLOR="Red"]ifconfig eth1 up[/COLOR]*

To edit /etc/network/interfaces, one hopes, is the way to get it to come up correctly after a re-boot. That will be what I try next.
I am also looking for tutorial examples on what is good to put into that file.

As far as the provided tools are concerned, they are a dead loss.
Compare what the Help Manual shows..with what you actually get!
It seems dumbed down into non-functionality. It needs an "Apply" button. It needs a way to invoke an automatic setup ***that tests itself!***. It needs ***feedback*** to the user that something worked. Simply clicking "***Close***" can also mean "Let's stop doing this!"

To have stumbles over getting going in this area, creates unfortunate impressions out of all proportion to to the actual problem, and blights the rest of what may be a fantastic distro release ... is what I think.

---

### Post by felixq78 on 2010-07-12
I haven't had this problem at all with my main Dual Core Pentium PC. BUT I just installed Ubuntu 10.04 into a Compaq Presario SR1040AN that I Found in the street and everything works fine except the Auto Etho just wont pick it up automatically like the dual core does.
Could it be the PC? I've noticed that it has an inbuilt dial-up modem, could that be confusing the situation or is it just broken?

---

### Post by nigeldodd on 2010-09-28
There seems to be inconsistency between the system/preferences/"network connections" tool and what is in the  /etc/network/interfaces file. Until recently my /etc/network/interfaces file only had the loopback information in it but the network connections tool had the correct fixed IP information for my card. Yesterday my ethernet suddenly stopped working. I could not correct it using the tool but I succeeded using the interfaces file. Now the tool shows no information about the configuration.

Surely the tool should edit the file and the two should be consistent?

---

### Post by nighthawk77 on 2010-10-01
> **arunarun4 said:**
> Hi all..
May be this can help you connect to Internet through ethernet.

[COLOR=Red]*ifconfig -a | grep eth*[/COLOR]
This will give you the ethernet details. Be sure to check the number after "eth"; ie "eth0". "eth1". And that is your ethernet port. This is applicable to all further commands.

[COLOR=Red]*sudo ifconfig eth0 10.0.0.100 netmask 255.255.255.0*[/COLOR]
This will create a temporary ip. 
[I]
[COLOR=Red]ifconfig eth0[/COLOR][/I]
Use this to verify the configuration. 

[COLOR=Red]*sudo route add default gw 10.0.0.1 eth0*[/COLOR]
This will create a default gateway.

[COLOR=Red]*sudo gedit /etc/network/interfaces*[/COLOR]
This will open the interfaces file
Add the following to the end of the file. Be sure to add your port number (eth?)
[COLOR=Red][I]auto eth0
iface eth0 inet dhcp[/I][/COLOR]

[COLOR=Red]*sudo ifup eth0*[/COLOR]
This will enable the settings

This is a small information I got from the help and support in Ubuntu 10.04. I was able to connect to Internet with the help of these commands. Please try it . I'm sorry if this doesn't solve your problem. I'm a newbie to ubuntu 10.04.

Thank you all :)

Thxs!
I was able to get internet working with this commands. Now it's working fine again after I changed some hardware:guitar:

---

### Post by dineshs on 2010-10-01
> **nigeldodd said:**
> There seems to be inconsistency between the system/preferences/"network connections" tool and what is in the  /etc/network/interfaces file. Until recently my /etc/network/interfaces file only had the loopback information in it but the network connections tool had the correct fixed IP information for my card. Yesterday my ethernet suddenly stopped working. I could not correct it using the tool but I succeeded using the interfaces file. Now the tool shows no information about the configuration.

Surely the tool should edit the file and the two should be consistent?
Network manager(the tool used to configure network devices in new linux distros) stores the details in a textfile  in /etc/NetworkManager/system-connections
Network-admin(the tool used to configure network in older linux distros)stores the details in /etc/network/interfaces
If you edit /etc/network/interfaces by hand Network manager will not manage your devices.In otherwords for NM to manage your devices /etc/network/interfaces should only contain```
auto lo
iface lo inet loopback
```

---

### Post by Iowan on 2010-10-01
[Here]("http://ubuntuforums.org/showthread.php?t=1028541") is a thread that *might* help.

---

