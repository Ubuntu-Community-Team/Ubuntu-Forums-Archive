---
title: "How to get connected to DSL"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by foots2015 on 2006-07-11
Hi 

I am trying to get connected to the internet via my dsl connection. 
My isp gave me a disk that install the stuff needed to setup the connection, but it is only for Mac and Windows. I called the support desk of my provider and they said that it was possible to connect in linux, but they did not support it and that is all they could tell me.

So I ask you people how can I get my dsl connected?:-k

---

### Post by RRS on 2006-07-11
Is this a new connection or did you use it before in Windows or Mac?

Also what modem and/or router do you have?

The main purpose of the disc they provided was to configure the modem with the proper settings for the ISP and usually your login name and password.

This can usually be done manually but the disc makes it "automatic" for the basic windows user.

Let us know what equipment and ISP you have and I'm sure we can help, someone else is bound to have the same or similar setup.

---

### Post by DigitalXpert on 2006-07-11
I'd go out and get a router.  Dlink DI-604 is good and cheap.  Then you just configure the PPPoE settings on the router.

It will firewall your computer from hackers as an extra bonus.  

If you were planning on hooking the modem to your Ubuntu with USB I'd definetly get the router instead.  USB has always been hit or miss for me in Linux.

Just trying to save you from headaches. ;)

---

### Post by foots2015 on 2006-07-11
I have a ADSL modem that is connected directly to my computer with a LAN cable. I have been using the internet for many months on my PC with windows installed. It works fine on the windows system...

---

### Post by foots2015 on 2006-07-11
My modem number is: Corega DSL200A

---

### Post by RRS on 2006-07-11
System>Administration>Networking

Open the DNS page and enter your modems IP under DNS servers.

Then go to the connections page and select eth0 and checkmark "enable this connection"
For configuration select DHCP from the dropdown menue. Click OK, then OK again and you should be online.

If this doesn't work post back with the results of the terminal command [COLOR="Blue"]ifconfig[/COLOR]

---

### Post by jml on 2006-07-11
I agree with DigitalXpert.  Get a router, I've used Linksys brand successfully.  Plug the modem into the router.  Use your windows PC to make sure the hardware setup works.  Set up the router to assign the computer's IP address, (DHCP).  Then plug in your Ubuntu box with a network cable into the router.  You then need to configure and activate the connection.  A router is very cheap extra protection for people with DSL connections.  I even recommmend it for people with only one computer.

Joe

---

### Post by foots2015 on 2006-07-12
eth0      Link encap:Ethernet  HWaddr 00:14:22:8E:39:40
          inet6 addr: fe80::214:22ff:fe8e:3940/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:128 (128.0 b)  TX bytes:2914 (2.8 KiB)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)





](*,)  Shouldn't there be a dialoge box that asks me for my username and password to log on to the internet?

---

### Post by RRS on 2006-07-12
Ifconfig looks ok, have you tried Firefox?

Your modem normally enters the username and password when initiating the connection @ boot. That's one of the items configured when you originally ran the ISP's cd from windows.

---

### Post by mips on 2006-07-12
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by foots2015 on 2006-07-12
> **mips said:**
> My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.



First off, thank you for your responses.

Here is a link to my modem:
[http://www.alliedtelesyn.com/products/details.aspx?502]("http://www.alliedtelesyn.com/products/details.aspx?502")

I have the modem directly connected to my laptop through the ethernet port.


**1**.tim@DellLap:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:14:22:8E:39:40
          inet6 addr: fe80::214:22ff:fe8e:3940/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22544 (22.0 KiB)  TX bytes:21158 (20.6 KiB)
          Interrupt:217

tim@DellLap:~$

**2**.tim@DellLap:~$ lspci | grep Eth
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
tim@DellLap:~$

**3**.tim@DellLap:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
tim@DellLap:~$

**4**.tim@DellLap:~$ cat /etc/resolv.conf
nameserver 12.6.42.1
nameserver 216.152.182.254
nameserver 192.168.0.6
nameserver 192.168.0.1
nameserver 12.6.42.2
tim@DellLap:~$

**5**.tim@DellLap:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
tim@DellLap:~$

**6**.tim@DellLap:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
tim@DellLap:~$

**7**. Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Bookkeeper>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.6
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        IP Address. . . . . . . . . . . . : fe80::214:22ff:fe8e:3940%4
        Default Gateway . . . . . . . . . : 192.168.0.1

PPP adapter MTA DSL:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 216.152.189.66
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 216.152.189.66

Tunnel adapter Teredo Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : fe80::5445:5245:444f%5
        Default Gateway . . . . . . . . . :

Tunnel adapter 6to4 Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 2002:d898:bd42::d898:bd42
        Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301

Tunnel adapter Automatic Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : fe80::5efe:216.152.189.66%2
        Default Gateway . . . . . . . . . :

Tunnel adapter Automatic Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : fe80::5efe:192.168.0.6%2
        Default Gateway . . . . . . . . . :

**8**. My ISP is MTA. Here is their link:[http://www.mtaonline.net/internet/internethome.html]("http://www.mtaonline.net/internet/internethome.html")

---

### Post by mips on 2006-07-13
You are not getting a IP address via DHCP. Use your windows settings to configure Ubuntu for static IP and see if things work.

You are getting a IPv6 address but I don't think that is going to help you.

---

### Post by foots2015 on 2006-07-13
I got the DSL working these are the steps I took:

**1.** Reinstall Ubuntu 6.06

**2.** 

> **manzuk said:**
> Well, a friend of mine had a similar problem few months ago. Although we solved it, I don't remember exactly what we did but I'll try to help you.


_**Just as general information**_

There are two types of ADSL modems, Ethernet (those which use a cable like telephone's) and USB (which obviously connect through usb)

Ethernet ADSL modems are easier to config. Why? Because we JUST have to find a way to tell the ADSLmodem to establish an internet connection with the ISP. And that's where PPPoE gets into the action (but I'll explain later how)

In the other hand, some USB ADSL modems are not propertly detected when plugged in, and that's because the computer doesn't have the necessary drivers. So we have to find them, compile them, and install them. A real pain, but not the end of the world (I might write a HowTo...)


_**Your particular problem**_

If your modem is Ethernet (or if it's USB and you know your computer has detected it fine), then you need these packages:

**pppoe** & **pppoeconf**

Where to get them? There's quiet an useful page for this cases [http://packages.ubuntulinux.org](http://packages.ubuntulinux.org)
There you can search and download packages from the official repositories. So go there (under win) and get those packages! And install them under linux (double click, and Gdebi will do the rest)

Check again that your modem is connected to your PC (and if it's USB, remember the "link" or whatever is called led should be on)

Now run from a terminal
```
pppoeconf
```
and cross your fingers...

Lets say everything went fine. Now you have to edit /etc/ppp/peers/dsl-provider 
Remember you need SuperUser rights, so you should run: ```
gksu gedit /etc/ppp/peers/dsl-provider
```

Where it says ```
#user myusername@myprovider.net
``` replace "***myusername@myprovider.net***" with your actual user, and delete the "***#***" at the begining.

Now edit /etc/ppp/pap-secrets (here is where your password goes)
Again SuperUser rights needed, so ```
gksu gedit /etc/ppp/pap-secrets
```

At the end it says ```
#	*	password
``` replace "***password***" with your real pass, and **I think** you should delete the "#"

**Let's try the connection!!!**

From a terminal run:
```
pppd call dsl-provider
```
and go to [www.google.com](www.google.com)
Or if it doesn't work, you can try with
```
sudo pppd call dsl-provider
```

**_Final comments_**

I can't remember whether pppoeconf did the username and pass stuff for you or not, so I put it just in case.
I might be forgetting something...
Hope this helps you. (tell me later if it worked)

**3.** Disabled IPV6

**4.** Set MTU to 1452

And Viola the internet works :)

---

