---
title: "Debian eth0 Problems/ No Internet Connection/Network"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by Pyth7 on 2010-09-25
Hi,
I cross-posted this on the Debian forum for reasons that are obvious.

To begin with my problem I need to describe my system(s) a little.
I am working on a cross-platform application for Linux ,Apple and Windows, so I have a full tower system with four SATA hard drives that be selected with a switch, so that I can change drives and operating systems at will. -sort of makes me a jack of linux systems, but master of none.
It's important to mention this, because it shows the strangeness of the problem as it is isolated to Debian* systems.
 drive 1:  A dual-boot with Windows7 and Ubuntu 10.4
 drive 2: Debian 5.0.2
 drive 3: Fedora 11
 drive 4: openSuse 11.1
I have lost my internet connection in both Ubuntu 10.4 and Debian 5.0.2, but Windows7, Fedora, and openSuse all connect!
The internet connections for Debian and Ubuntu worked fine up until this past week.
The LAN is on the mother board: a RealTek RTL8111B 1000/100/10 Ethernet/LAN -single-Chip Gigabit LOM Ethernet Controller for PCI Express.

Googling the issue for possible solutions I found modifying the /etc/network/interfaces file and then reseting the network:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

#: nano /etc/network/interfaces

##edit eth1 your dispositive
auto eth1
iface eth1 inet dhcp
##save

#:/etc/init.d/networking restart

Trying this I get a script errors saying: misplaced option ifdown: couldn't read interfaces file "etc/network/interfaces"
and 
 ifup: couldn't read interfaces file "etc/network/interfaces"

I have a second computer with WinXP and Ubuntu 9.04 dual-boot which connects fine, so I get the bright idea to look at the interfaces file on the Ubuntu 9.04
to give a clue to the error. 
All the interfaces file says is:
auto lo
iface lo inet loopback

No mention of dhcp!

So where does debian/ubuntu get it's information to establish a network connection?
How do I rectify the problem? I can hardly blame the hardware (RTL8111B), because the problem is isolated to Debian systems.

Thanks!
Russ Kinter

---

### Post by mrhhug on 2010-09-25
try and find your card in 
```
sudo /sbin/ifconfig
```
and make sure its still eth1
somehow it might have changed then just change in etc/network/interfaces "iface ethXXX inet dhcp

also this looks remarkably similar [http://ubuntuforums.org/showthread.php?t=632181](http://ubuntuforums.org/showthread.php?t=632181)

---

### Post by Pyth7 on 2010-09-26
> **mrhhug said:**
> try and find your card in 
```
sudo /sbin/ifconfig
```and make sure its still eth1
somehow it might have changed then just change in etc/network/interfaces "iface ethXXX inet dhcp

also this looks remarkably similar [http://ubuntuforums.org/showthread.php?t=632181](http://ubuntuforums.org/showthread.php?t=632181)

Hi, 
Sorry I copied that from [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)
verbatum. I should have changed it to reflect my setup.

my card (chip in my case) is really "eth0"
Here is the print out for ifconifg:

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:f2:ef:4d:af  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7456 (7.4 KB)  TX bytes:7456 (7.4 KB)

Meanwhile my problems with Debian 5.0.2 seem to have solved themselves.
I booted into it and it had a connection. I still can't get Ubuntu 10.4 working though

Thanks!
Russ Kinter

---

### Post by mrhhug on 2010-09-26
ok so does you /etc/network/interfaces reflect eth0 or eth1?

your is apparently configured eth0.. your /etc/network/interfaces need to reflect that

---

### Post by Pyth7 on 2010-09-26
> **mrhhug said:**
> ok so does you /etc/network/interfaces reflect eth0 or eth1?

your is apparently configured eth0.. your /etc/network/interfaces need to reflect that

interfaces reflects "eth0"

I actually copied the now-working debian 5.0.2 interfaces file over to replace the Ubuntu one 
and did /etc/init.d/networking restart 
It restarted without complaint, but I still have no connection.

Thanks!

---

### Post by mrhhug on 2010-09-26
> **Pyth7 said:**
> interfaces reflects "eth0"

I actually copied the now-working debian 5.0.2 interfaces file over to replace the Ubuntu one 
and did /etc/init.d/networking restart 
It restarted without complaint, but I still have no connection.

Thanks!
 so your good?? do you need more support??? when u say >  Thanks! im confused.... repost if you need more help with ubuntu

---

### Post by Pyth7 on 2010-09-26
> **mrhhug said:**
> so your good?? do you need more support??? when u say  im confused.... repost if you need more help with ubuntu

Yes I need more support. I still do not have an internet connection.

Replacing the Ubuntu interfaces file with the Debian one did not solve the problem.

---

### Post by mrhhug on 2010-09-26
post the complete output of ```
cat /etc/network/interfaces
```

---

### Post by Pyth7 on 2010-09-26
> **mrhhug said:**
> post the complete output of ```
cat /etc/network/interfaces
```
 
[EMAIL="russkinter@ubuntu:~$"]russkinter@ubuntu:~$[/EMAIL] cat /etc/network/interfaces
 
# file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp
#
[EMAIL="russkinter@ubuntu:~$"]russkinter@ubuntu:~$[/EMAIL] 
 
What about dns servers?
I looked at the /etc/resolve.conf file on Ubuntu and nothing was listed.
 
So I replaced it with the resolve.conf file from the connection working Debian 5.0.2:
 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   2792
#
### END INFO
domain home

search home

nameserver 192.168.1.1
nameserver 71.242.0.12
 
However that did not solve the problem either after rebooting or /etc/init.d/networking restart :(

---

### Post by mrhhug on 2010-09-26
hotplug?

mine doesn't have that and it is still hotplug: try changing your /etc/network/interfaces to 

```
auto eth0
iface eth0 inet dhcp
```

here's mine, i even have some of mine commented out 
```
auto lo
iface lo inet loopback
#
auto eth0
#iface eth0 inet dhcp
```

heres a good link for you [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by Pyth7 on 2010-09-26
Got it working! Thank you!
Besides mrhhugs esteemed advice, properly editing the files with vi is a necessity imho.
Part of the problem I think was I used nano to edit.
This tutorial helped considerably:
[http://www.unix-manuals.com/tutorials/vi/vi-in-10-1.html](http://www.unix-manuals.com/tutorials/vi/vi-in-10-1.html)
This makes vi much simpler than i had been led to believe by other tutorials.

---

