---
title: "Dual NICs, specific processes"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by erictherev on 2009-02-16
I'm running two NICs in the same subnet, with different static IP addresses. What I'd like to accomplish with this is quite simple: I want one NIC dedicated to ktorrent so that any downloads I have running will not clog up my bandwidth. Is there a way to do this?

---

### Post by nixscripter on 2009-02-17
I think you might be able to do it with creative iptables rules. If the destination port is a torrent download, run it through one interface. Otherwise, run it through the other. I'm afraid I can't think of them off the top of my head. 

Generic firewall instructions, which you might be able to modify, are here: [http://www.linux.com/feature/113867](http://www.linux.com/feature/113867)

And a very extensive guide is here: [http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

Hope this helps.

---

### Post by yther on 2009-02-17
Phooey, I was hoping someone had a clever answer for you, because I would like to do a similar thing with different software.  :P

However, since you specifically asked about KTorrent, I can inform you that there is actually a setting within the program that controls which interface it uses!  Go to Settings > Configure KTorrent, and click on the Network icon.  Toward the bottom there is a drop-down list labeled "Network Interface," where you can pick which one to use or let it use them all.

---

### Post by erictherev on 2009-02-18
Another idea I've come up with...

Would it be possible to assign specific ports to a NIC, so that only the ktorrent traffic can go through on one of the NICs but none of the ktorrent traffic can go through on the other NIC?

---

### Post by nixscripter on 2009-02-22
That was sort of what I was suggesting with the firewall rules: if the traffic is going to a destination port A, use the first NIC. Otherwise, use the second.

When I think about it, however, you might want to consider Mode 4 Link Aggregation. It will intelligently balance the load for you in real-time to avoid network slowdowns.

[https://wiki.ubuntu.com/LinkAggregation](https://wiki.ubuntu.com/LinkAggregation)

---

### Post by erictherev on 2009-02-22
I tried mode 4 aggregation, and the result was a lack of connection to anything. I tried to undo the aggregation, but the bond still showed when I ran ifconfig. I then removed the second card from my machine physically and rebooted. The bond still showed when I ran ifconfig, so I edited my /etc/network/interfaces. After doing that I tried connecting again, and still had no internet connectivity.

At this point, I only have one NIC in my system, it is configured correctly with a static IP, my router is only willing to give the static IP to a system with that specific MAC address, I get good response time when pinging my router, and when I attempt to ping google, I get the following message "ping: unknown host google.com"

I have tried restarting the network connections and rebooted the router.


Can somebody please help???

---

### Post by erictherev on 2009-02-22
Additionally, I can communicate with other machines on the local network.

Here is my /etc/networking/interfaces, if it helps.

```
#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth1
iface eth1 inet static
address 192.168.2.246
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
dns-nameservers 192.168.2.1
```

---

### Post by nixscripter on 2009-02-23
I'm sorry it didn't work out. I will try to help you get it working one step at a time if you will try again.

As for your current problem, try removing the "DNS 192.168.2.1" line, and see if the gateway will figure it out for you.

---

### Post by erictherev on 2009-02-25
> **nixscripter said:**
> As for your current problem, try removing the "DNS 192.168.2.1" line, and see if the gateway will figure it out for you.
I still get the unknown host error when I attempt to send out a ping request.

---

### Post by nixscripter on 2009-02-25
If you have any other machines, do they have the DNS nameserver of 192.168.2.1 as well? Since you can ping other things by IP but name lookups fail, I am assuming DNS is the problem.

---

### Post by erictherev on 2009-02-25
> **nixscripter said:**
> If you have any other machines, do they have the DNS nameserver of 192.168.2.1 as well? Since you can ping other things by IP but name lookups fail, I am assuming DNS is the problem.
The other systems on my local network are windoze boxes with dynamic IPs rather than static. The system I'm having issues with needs a static IP because it's a file server. As far as any DHCP requests go, IPs are assigned by a router running Smoothwall 2.0 with the latest updates.

All this being said, I have not assigned a DNS nameserver on any of the other machines. The DNS nameserver was something I saw in the ifenslave HowTo and entered on the machine currently having problems.

---

### Post by capscrew on 2009-02-25
> **erictherev said:**
> ...
At this point, I only have one NIC in my system, it is configured correctly with a static IP, my router is only willing to give the static IP to a system with that specific MAC address, 

The above doesn't really fit with the following:> Here is my /etc/networking/interfaces, if it helps.

```


#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth1
iface eth1 inet static
address 192.168.2.246
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
dns-nameservers 192.168.2.1
```



This further muddys the water:> The other systems on my local network are windoze boxes with dynamic IPs rather than static. The system I'm having issues with needs a static IP because it's a file server. As far as any DHCP requests go, IPs are assigned by a router running Smoothwall 2.0 with the latest updates.

All this being said, I have not assigned a DNS nameserver on any of the other machines. The DNS nameserver was something I saw in the ifenslave HowTo and entered on the machine currently having problems.

Regardless of how you get the NIC configuration, all hosts in a LAN subnet need the following in common to function together.
```

The same network eg. 192.168.2.0/24
The same subnet mask (that's the /24 or it can be 255.255.255.0)
The same gateway out of the subnet (nearside interface of the local router)
And an IP address of a working DNS server (for name resolution)

```

I ask because on one hand you state your server has its IP address assigned "with a static IP, my router is only willing to give the static IP to a system with that specific MAC address".  later you show that the interface is manually configured when you  state:"Here is my /etc/networking/interfaces, if it helps."

The term static used to refer to a manually assigned, unchanging IP address.  Unchanging IP addresses assigned via DHCP would be reserved (permanent) by name.

Post the output from one of your windows hosts with ```
ipconfig /all
``` And post the output from the Ubuntu server using: ```
ifconfig -a
```

The we can sort this out.

---

### Post by erictherev on 2009-02-26
'ifconfig -a' on Intrepid Ibex file server:

```
bond0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:192.168.2.246  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe9e:2631/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:248829 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31463126 (31.4 MB)  TX bytes:219811766 (219.8 MB)
          Interrupt:16 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:337740 (337.7 KB)  TX bytes:337740 (337.7 KB)

pan0      Link encap:Ethernet  HWaddr **:**:**:**:**:**
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

'ipconfig /all' on a Windoze system:
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Nomad>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : iridonia
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8168/8111 PCI-E Gigabit E
thernet NIC
        Physical Address. . . . . . . . . : **-**-**-**-**-**
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.2.238
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1
        DHCP Server . . . . . . . . . . . : 192.168.2.1
        DNS Servers . . . . . . . . . . . : 192.168.2.1
        Primary WINS Server . . . . . . . : 192.168.2.246
        Lease Obtained. . . . . . . . . . : Wednesday, February 25, 2009 2:56:10
 PM
        Lease Expires . . . . . . . . . . : Thursday, December 31, 2015 2:56:10
PM

Ethernet adapter Bluetooth Network Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
        Physical Address. . . . . . . . . : **-**-**-**-**-**

```

I had thought that bond0 had been removed from my Linux system...???

---

### Post by capscrew on 2009-02-26
So far so good.  Both hosts are on the same network.  Do we have the same gateway and dns server?

The gateway is defined in the /etc/network/interfaces.  Mine looks like this:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

All the stuff extra stuff in yours is not normally needed.  This would the following:
```

network 192.168.2.0
broadcast 192.168.2.255
dns-nameservers 192.168.2.1

```

The dns server is defined in /etc/resolv.conf.  Mine looks like this:
```

# Local DNS
nameserver 192.168.1.1
# OpenDNS 
nameserver 208.67.222.222
nameserver 208.67.220.220

```
I noticed you are running a WINS server on your Linux host.  Are you running Samba?  Have you correctly set up the nsswitch.conf for name resolution?  I'm itching to ask, so here goes; Are you using webmin to configure all of this?  This could make all the difference in the world.

My advice, **[B][COLOR="Red"]if you are not using webmin [/COLOR]**[/B], is to remove the extra lines in your /etc/network/interfaces file and make sure your /etc/resolv.conf file has the correct nameservers (dns).  If you have local dns on the gateway great.  I would add the OpenDNS nameservers for an outside fall back.  When you use this setup be aware that the local dns **may **forward the unresolved requests somewhere else.  The OpenDNS is only used if your local dns fails to respond.

Let me know what happens.

---

### Post by erictherev on 2009-02-27
OK, I removed the extra lines from /etc/network/interfaces and added in the nameserver line in my resolv.conf (which was empty) and now I get a good ping from google. My smb sharing works, now if I could only get my printer to work via smb...

---

### Post by capscrew on 2009-02-27
That I can't help you with.  I have networked printers.  They are Jet-Direct HP's.  So i just use the GUI like this: System>>Preferences>Default_Printer for Ubuntu.  In Windows I just go to Printers and Faxes and use the GUI.  Jet-direct advertises itself.

---

### Post by erictherev on 2009-02-27
Cap, which Ubuntu distro are you running? I'm running Kubuntu Intrepid, and under the kde4 menu, there is System>>Printing, but no System>>Preferences. When I've gone into the Printing GUI, there is no way to enter Administrator mode and I can't do a GUI login as root.

*Never mind, I killed KDE and restarted X as root, then went in and made the necessary changes. I don't know why I didn't think of that sooner.*

I can see the printer from my Windoze systems, but under the icon there is a message that says, "Access denied, unable to connect."

---

### Post by erictherev on 2009-02-27
I started a new thread about the printing problems [here]("http://ubuntuforums.org/showthread.php?p=6811445#post6811445").

---

### Post by capscrew on 2009-02-27
I'm a Gnome guy.  Sorry 'bout that.  I forget obout the differences in the GUI's.

---

