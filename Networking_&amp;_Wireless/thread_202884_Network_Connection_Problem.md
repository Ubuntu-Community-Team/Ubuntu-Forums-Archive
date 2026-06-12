---
title: "Network Connection Problem"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by Paul41 on 2006-06-24
I am having problems getting Ubuntu to work with my router from my installed version.  I can not get to the internet, and when I try to ping the router I get messages that it can not find it.  If I restart the router things work, but only for a very short time (~1 minute or less) then it looses connection again.  When I run Ubuntu from the live CD I have no problems.  I have checked the network setup for both the live CD and my local install and I can't find any differences.  

This is my first attempt at using Linux and I like the look and feel of Ubuntu, but I am at the point now that I am ready to give up on it and try Fedora or Susse.  I figured I would give this forum a try before completely giving up.  Any help would be greatly appreciated.

---

### Post by digimars on 2006-06-24
Is it a wireless or ethernet connection?

Have you checked System->Administration->Networking and checked out your settings there?  If you have more than one network card make sure that your "Default Gateway device" is set to the correct one.

What is your output when you type into the terminal
```

ifconfig <interface>

```

where <interface> is your ethernet card (typically eth0, eth1).

If it's ethernet, was your cable plugged in when you booted Ubuntu?

Is your router set up for DHCP or a static IP?  By default Ubuntu is set up to recieve IP's via DHCP.

What if you tried bouncing your interfaces?
```

sudo ifconfig <interface> down
sudo ifconfig <interface> up
sudo dhclient <interface>

```

---

### Post by Paul41 on 2006-06-24
My connection is a ethernet connection.

I have checked System->Administration->Networking and everything there is set up the same as in live CD (which works fine).  I only have 1 network card and it is eth0.

I have run ifconfig, but having never used Linux it didn't mean much to me.  I have to run out for a bit so I can't login on the local install right now.  I will post the results to this a little later today.

Yes my ethernet cable was plugged in when I started Ubuntu.

The router is set for DHCP.

I have tried sudo ifconfig <interface> dup, but not sudo ifconfig <interface> down or sudo dhclient <interface>.  I will give those a try.

Thanks for your help so far.  I really want to get this working so I can keep using Ubuntu.

---

### Post by pudgexl on 2006-06-24
I am having the same problem.  I have no problems using my network connection for internet traffic in XP nor when using the live cd, but when I ran Ubuntu from the Hard drive my connection simply stops working after a minute or so.  

Network Topology:

CNet Pro200 PCI ---->  Linksys 4 Port Switch ----> Terayon Cable Router

Interestingly enough, if I change ports on my Linksys switch (ie unplug from port 1, plug into port 2) my connection will work for about another minute and then die.

When I say die I mean no http, no ICMP, nothing.  ICMP either drops packets or reports Dest. Host Unreachable.  I've set my eth0 interface to use a static ip and have made no changes to any other networking modules.  I've explored the Network Settings, and Network Monitor utilities and have found these useless (other than to configure a static ip).

I'm trying to install ethereal to get a packet capture, but its a bit difficult to download and install an app without a working internet connection.  (I had to boot up xp to post this message).

Any assistance on stabilizing my network interface would be greatly appreciated. 

-PJ

---

### Post by mips on 2006-06-25
You provide very little information.

Could I suggest you do a search for IPv6 or DNS. Gaurenteed you r problem has been encountered and solved elsewhere on this forum.

---

### Post by Paul41 on 2006-06-25
OK here are my results from ifconfig.

eth0      Link encap:Ethernet  HWaddr 00:08:A1:10:07:3C
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe10:73c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437 errors:35 dropped:0 overruns:0 frame:0
          TX packets:417 errors:12 dropped:0 overruns:0 carrier:12
          collisions:0 txqueuelen:1000
          RX bytes:455692 (445.0 KiB)  TX bytes:62796 (61.3 KiB)
          Interrupt:201 Base address:0xe800

I tried the ifconfig down, but this did not work.

mips, I have seen some posts where people say they switched from using iPv6 to IPv4 and that fixed their problem, but I couldn't find any that said how they made the switch.

On the Hosts tab in System->Administration->Networking there is:
    ff02::2  ip6-allrouters
Could this be the problem?  The same thing is in the Live CD and this works fine so I doubt it.  If this could be the problem could you please give me any advice on fixing it?

Also like pudgexl I have XP also running on this machine with no problems.

---

### Post by mips on 2006-06-25
What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **/etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by Paul41 on 2006-06-25
>  What hardware are you using, modem/router model etc ???
I am using a Dell 8200 Desk top.  I have 2 hard drives, the master has XP on it and the slave has Ubuntu.
The modum = Toshiba PCX2600.  
Router = Linksys RTP300.

> How is the above hardware configured ???
I am not quite sure what you need to know here.  The cable line runs into the modum, then a network cable runs from the modum to the router.  Router runs to the PC.  There is also a phone line out of the router (I have VoIP).  Hopefully this is what you need to know.  If not let me know.

> 1. Please post output of ifconfig eth0 (Depends on your interface number)
I posted this in my previous post.

> 2. Please post output of lspci | grep Eth
0000:02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

> 3. Please post output of route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.15.1    0.0.0.0         UG    0      0        0 eth0

> 4. Please post output of cat /etc/resolv.conf
nameserver 192.168.15.1

> 5. Please post output of cat /etc/network/interfaces
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

> 6. Please post output of /etc/dhcp3/dhclient.conf
/etc/dhcp3/dhclient.conf: command not found

> 7. Please copy entire output of windows ipconfig /all command here
I will have to switch to windows and post back with this one.

> 8. Who is your ISP and provide a web link.
My ISP is Road Runner
[http://www.rr.com/html/index.cfm?p=16&m=108](http://www.rr.com/html/index.cfm?p=16&m=108)

I tried disabling IPv6 according to the links you posted, but that did not solve the problem either.  I don't know if it makes any differenece, but the outputs I just posted were with IPv6 still disabled.  If you need me to reactivate it and repost I can.

---

### Post by Paul41 on 2006-06-25
OK here is the output from windows.  The rest is in my previous post.

> 7. Please copy entire output of windows ipconfig /all command here

Windows IP Configuration

        Host Name . . . . . . . . . . . . : Paul
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : CNet PRO200WL PCI Fast Ethernet Adap
ter
        Physical Address. . . . . . . . . : 00-08-A1-10-07-3C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.15.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.15.1
        DHCP Server . . . . . . . . . . . : 192.168.15.1
        DNS Servers . . . . . . . . . . . : 192.168.15.1
        Lease Obtained. . . . . . . . . . : Sunday, June 25, 2006 12:17:45 PM
        Lease Expires . . . . . . . . . . : Monday, June 26, 2006 12:17:45 PM

---

### Post by mips on 2006-06-25
[QUOTE=Paul41]
/etc/dhcp3/dhclient.conf: command not found
[/QUOTE]

cat /etc/dhcp3/dhclient.conf

I suspect your problem might be related to your Tulip based ethernet card. If I'm not mistaken I recall seeing a lot of posts relating to tulip based cards.

Do a search for tulip in the meantime in these forums.

---

### Post by Paul41 on 2006-06-25
Thanks for your help mips.  It looks like you were right about the Tulip.  I followed the steps here and everything seems to be working now.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by mips on 2006-06-25
Cool, as long as you are working.

---

### Post by poontang on 2006-07-02
I got the same problem with the CNET PRO200 card as well.

---

### Post by mips on 2006-07-05
As far as i recall the CNET PRO200 also uses a Tulip chipset. Does the link solve your problem ?

---

### Post by nilya on 2006-07-06
[QUOTE=mips]I suspect your problem might be related to your Tulip based ethernet card.
Do a search for tulip in the meantime in these forums.[/QUOTE]
Here is the solution:
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

