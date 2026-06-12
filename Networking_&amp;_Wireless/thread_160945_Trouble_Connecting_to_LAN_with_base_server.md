---
title: "Trouble Connecting to LAN with base server"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by presentt on 2006-04-15
Hello all,

Firstly, thank you for bearing with me, and I apoligize for this post's length; I have done as much reading as I could before posting this thread, and thus have included as much information as I thought might be relevant.

I am having trouble getting my Ubuntu 5.10 base-server installation to connect to my LAN, and ultimately the internet.  I eventually would like to configure it as an FTP server, but that's later.

I have a Dell TrueMobile 2300 wireless router, but the computer I am using as the server (named "server") is connected to the router with a _wired_ connection.

I have begun following the "[Wired Ethernet Troubleshooting Process]("http://ubuntuforums.org/showthread.php?t=87643")," and hit a problem when I attempt to ping my router (who's IP is 192.168.2.1).

Up to that point, my results are as follows:
[FONT=Courier New]**presentt@server:~$ sudo mii-tool eth0**
eth0: negotiated 100baseTx-FD, link ok
[/FONT][FONT=Courier New]**presentt@server:~$ ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr: 00:00:86:35:44:39
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:15
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:388 (388.0 b)
          Interrupt:3 Base address:0x300
[/FONT][FONT=Courier New]**presentt@server:~$ route -n**
Kernel IP routing table
Destination     Gateway      Genmask       Flags Metric Ref  Use Iface
192.168.2.0     0.0.0.0      255.255.255.0 U     0      0      0 eth0
0.0.0.0         192.168.2.1  0.0.0.0       UG    0      0      0 eth0

[FONT=Verdana]However, when I attempt to ping my router (192.168.2.1, and I confirmed this as my router's IP by using the router diagnostics on another machine), I get this:
[/FONT][/FONT][FONT=Courier New]**presentt@server:~$ ping 192.168.2.1**
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data,
From 192.168.2.100 icmp_seq=2 Destination Host Unreachable
[/FONT][FONT=Courier New]From 192.168.2.100 icmp_seq=3 Destination Host Unreachable
[/FONT][FONT=Courier New]From 192.168.2.100 icmp_seq=4 Destination Host Unreachable
[/FONT][FONT=Courier New]From 192.168.2.100 icmp_seq=5 Destination Host Unreachable
[/FONT][FONT=Courier New]From 192.168.2.100 icmp_seq=6 Destination Host Unreachable
[/FONT][FONT=Courier New]From 192.168.2.100 icmp_seq=7 Destination Host Unreachable
[/FONT][FONT=Courier New]From 192.168.2.100 icmp_seq=8 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
10 packets transmitted, 0 recieved, +6 errors, 100% packet loss, time 9000ms, pipe 3

[/FONT][FONT=Courier New][FONT=Verdana][FONT=Courier New][FONT=Verdana]I also cannot ping any computer connected to the LAN, or any IP on the internet; I recieve the same results as above.[/FONT][/FONT][/FONT][/FONT]
[FONT=Courier New]
[FONT=Verdana]The contents of my "/etc/network/interfaces" file are as follows (I omitted the commented lines starting with #):
[FONT=Courier New]auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

auto eth0
iface eth0 inet static
        address 192.168.2.100
        netmask 255.255.255.0
        gateway 192.168.2.1
        network 192.168.2.0

iface dsl-provider inet ppp
provider dsl-provider

[/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana]Is the above file configured correctly?  I also tried commenting out the last two lines, and various values for "network" under "iface eth0 inet static.'

My "/etc/resolv.conf" file is as follows:
[FONT=Courier New]search Home
nameserver 192.168.2.1
nameserver 151.197.0.39
domain Home

[FONT=Verdana]The two namerservers above were found under "ipconfig -all" on a WinXP Pro machine connected (successfully, by the way) to the same LAN; the workgroup is "Home."

There are green lights on both my router and my ethernet card, confirming a solid connection.  However, this computer ("server") I am attempting to configure does not show up on my router's network overview.  Also, I cannot ping 192.168.2.100 from another computer on the LAN (WinXP's ping utility simply tells me "Request Timed Out").

I also configured all of the firewalls on my computers connected the the LAN to allow free access to and from 192.168.2.100 (server's IP).  The router is set to automatically assign computers that request an IP an address in the range of 192.168.2.2 - 192.168.2.99, so it should not interfere with server's IP.  Additionally, my router is set to forward ports 20 and 21 (FTP) to 192.168.2.100, but I'm not sure if this is relevant.  My router uses MAC address filtering, but I took the HWaddr value from "ifconfig eth0" and cleared it with my router.  I am confident my router is configured properly, as I have a number of other machines working without a problem on the network and online.

I have repeatedly tried restarting the network service by both rebooting and entering:
[/FONT][/FONT][/FONT][/FONT][FONT=Courier New]**presentt@server:~$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                   [ ok ]
[FONT=Verdana]
Could someone help me get server connected to my LAN and the internet?  I have tried everything I could--sifted through dozens of forum threads, Linux networking tutorials, server tutorials, JFGI, the man pages for "interfaces," even asked a friend who uses Linux, but all to no avail.  I apologize again for the length of the post; I hope I've included what I have to, but please let me know if I left something relevant out (as I don't really know what is relevant or not).  I hope I copied all of the terminal results correctly; I am typing them verbatim.

Thanks a lot,
     Ted Present
[/FONT][/FONT]

---

### Post by dermotti on 2006-04-16
dhcp work?

---

### Post by mips on 2006-04-16
Can you ping 192.168.2.100 ?

---

### Post by presentt on 2006-04-16
Hello,

No, DHCP does not work.  I tried to figure out how to set it up, but it looks like I need to download the package with apt-get, but I cannot do this without an internet connection.  However, do I need DHCP since I ultimately want a static IP?

I am successfully able to ping 192.168.2.100, with a .179ms average delay.
I am also successfully able to ping "localhost," 127.0.0.1, and "server," so I'm guessing (accurately, I hope) that there is *some* sort of DNS operation going on, at least on a local level.

Thanks a lot.

---

### Post by al108 on 2006-04-16
For your */etc/network/interfaces*
I would try adding 
```
broadcast 192.168.2.255
```

and maybe 
```
dns-nameservers 192.168.2.1
```

I would defenetly remove these unless you know what you're trying to do with it:
```
iface dsl-provider inet ppp
provider dsl-provider
```

```
mapping hotplug
script grep
map eth0
```

For your */etc/resolv.conf* I would try changing *search* to ```
search yourISP.com
``` substitute yourISP.com to whatever your actual ISP is.
Try also removing
```
domain Home
```

I don't know if all of it is 100% accurate but it works for me.
Alex

---

### Post by presentt on 2006-04-16
Hello,

I made the changes suggested above to my */etc/network/interfaces* and my */etc/resolv.conf* files, but I still have no success pinging any external machines.

Might someone also tell me what value I should have for "network" under eth0 in my */etc/network/interfaces* file?  I filled that in as 192.168.2.0, but I'm not sure what it should be.  Also, what is the "broadcast" value?

Thank you.

---

### Post by al108 on 2006-04-18
[QUOTE=presentt]Hello,



I am successfully able to ping 192.168.2.100, with a .179ms average delay 

Thanks a lot.[/QUOTE]

What station are you pinging it from? I assume you doning it from the server, if so getting  .179ms average could be too big. Mine is .05ms. 

Also green light on the router doesn't always meen the link is good. Did you try the obvious changing ports on the router or changing cable? Also when you're working on your configs I would suggest disabling all security features on your router including firewall and mac filtering - that helps you to troubleshoot it step by step. If you'r worried about somebody hacking in to your system while you're doing that, disconnect it from the Internet, and fix your local network first.

> Also, what is the "broadcast" value?

Broadcast value is the address that is refered to all the computers on your network, and used by ARP (Address Resolution Protocol) when it wants to find the Ethernet address corresponidng to a given IP address. It sends a datagram which is addressed to all the stations on the network simultaneously. The datagram contains a query for the IP address, all receiveing computers check it against its own IP and if it matches, returns an ARP reply to the inquiring host...

> Might someone also tell me what value I should have for "network" under eth0 in my /etc/network/interfaces file? I filled that in as 192.168.2.0,
This is the correct value for your network. The adress ending with 0 is a nework address and refers to a whole network rather than a single computer.

> I have tried everything I could--sifted through dozens of forum threads, Linux networking tutorials, server tutorials, JFGI, the man pages for "interfaces," even asked a friend who uses Linux, but all to no avail.
Those tutorials were probably very brief and assumed that you alredy know everything about networking. [Here's yet another one.]("http://www.aboutdebian.com/network.htm") It helped me a lot to refresh my networking knowlege. It will give you some general understanding of what's going on in the network. If you still want to know more you probably should read a couple of networking books.


          I don't know if you already tried that but a couple of thing you could try when you're in situation that it just doesn't work. Try connecting your server to the cable modem or another computer directly, bypassing the router (you may have to use a crossover cable to do that). Try installing a different Ethernet card and see what happens. Your config files look fine at this point, but there might be something else we're missing.

> No, DHCP does not work. I tried to figure out how to set it up, but it looks like I need to download the package

The package that needed for your DHCP client to work is installed by default during the installation, remember when you're installing it's asking whether you want to configure your network with DHCP or not, well even if your say "no" it'll still install the package. Checking if DHCP works will prove that your physical connections work (DHCP takes care fo all your configuration) if it's successful and there's something wrong with your config files. If DHCP doesn't work it could be a number of things including but not limited to a corrupt installation from the CD or a bad installation CD.

> However, do I need DHCP since I ultimately want a static IP?
Yes, you want static IP so that other computers on the network know that your server at a certain IP. However there's such a thing as a static DHCP if your router supports it. It'll assign same IP's to the computers all the time.



Summary
There's only so many places where it could go wrong.

1. Physical layer - cables, network cards and drivers - so swap those around and make sure it works.
2. Configuration - using DHCP should take care of that if it works you know you're messed up in your configs somewhere
3. Your router - try establishing network without it or all security disabled maybe even reset to factory defaults (back up your router config before doing that)
4. Corrupt installation - although rare you can't discount it. Check your CD and do a default install on a separate partition, that way you'll have a GUI to play with and you'll have comparison for your config files. If it works you know that either your install was bad or you messed up one of the config files.

Let us know how you fixed it in the end and what was wrong. Break it down to simple steps, take care of one thing at a time and you'll be successfull

Good luck
Alex

---

### Post by presentt on 2006-06-21
Wow, that took waaay too long to get back to this problem.  I'm just finished my junior year in high school, and the last two months were filled with SATIs, SATIIs, AP tests, term papers, presentations, culminating project essays, and finals; whew, I'm glad it's summer now.

Anyways, thanks for everyone's help.

[quote=al108]
Summary
There's only so many places where it could go wrong.

1. Physical layer - cables, network cards and drivers - so swap those around and make sure it works.
2. Configuration - using DHCP should take care of that if it works you know you're messed up in your configs somewhere
3. Your router - try establishing network without it or all security disabled maybe even reset to factory defaults (back up your router config before doing that)
4. Corrupt installation - although rare you can't discount it. Check your CD and do a default install on a separate partition, that way you'll have a GUI to play with and you'll have comparison for your config files. If it works you know that either your install was bad or you messed up one of the config files.[/quote] 
I read through the networking tutorial you linked, it was highly informative, but nothing I found seemed to solve the problem.  I looked at every possible point of breakage I could think of.  I think the problem is at the network card level--the thing is *ancient*.  I'm still not real sure about the configurations, but after reading the tutorial, it all looks okay.  I tried redownloading the iso and reinstalling--same problems.  My router, as far as I know, is configured correctly.  That leaves the physical layer, and my uber-old network card.

At this time, I don't want to invest in a new card.  The whole system is old, and I may as well get a new one if I were to put money into it.

> Let us know how you fixed it in the end and what was wrong. Break it down to simple steps, take care of one thing at a time and you'll be successfull 
At this point, I'll try using the Dapper installation, and if that doesn't work, revert to the Hoary server install; I know Hoary works because it's what I had on the box before.  Thanks again for all the help.  I'll try to post my results a little more timely now.

---

### Post by mips on 2006-06-22
Whats the Make & Model of the card ?

---

