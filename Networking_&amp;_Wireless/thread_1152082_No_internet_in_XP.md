---
title: "No internet in XP"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by fatsheep on 2009-05-07
Here's the deal.  I've got a Desktop that I run in a dual boot setup (Ubuntu Linux and Windows XP).  Internet works perfectly on Ubuntu.  I can use either the NIC integrated into the motherboard or my PCI Ethernet card.  Both connect through an Ethernet cable.  However,  I have been unable to get my internet working with either one (I can't get to websites) on Windows XP.  

The first thing I tried was installing the latest drivers for the network cards.  I couldn't seem to find the drivers for my onboard NIC.  It shows up as "nvidia nforce networking controller".  I have a [DFI nF4 Ultra-Infinity 939 NVIDIA nForce4 Ultra ATX AMD Motherboard](http://www.newegg.com/product/product.aspx?Item=N82E16813136163) if that helps.  If you know where to find the latest drivers for the onboard network card on this one, please tell. :)

Anyways, I found the latest drivers for the Realtek PCI network card and installed them.  Still no internet.  However, I can ping websites successfully using the Realtek card:

```
C:\Documents and Settings\Fatsheep>ping www.google.com

Pinging www.l.google.com [64.233.161.104] with 32 bytes of data:

Reply from 64.233.161.104: bytes=32 time=37ms TTL=241
Reply from 64.233.161.104: bytes=32 time=37ms TTL=241
Reply from 64.233.161.104: bytes=32 time=36ms TTL=241
Reply from 64.233.161.104: bytes=32 time=39ms TTL=241

Ping statistics for 64.233.161.104:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 36ms, Maximum = 39ms, Average = 37ms

C:\Documents and Settings\Fatsheep>ipconfig

Windows IP Configuration

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.6
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

C:\Documents and Settings\Fatsheep>
```

Here are some additional things that might help someone more knowledgeable than me.

Hosts file (located in C:\WINDOWS\system32\drivers\etc):

```
# Copyright (c) 1993-1999 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

127.0.0.1       localhost
```

```
C:\Documents and Settings\Fatsheep>ipconfig  /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : fatsheepmobile
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth
ernet NIC
        Physical Address. . . . . . . . . : 00-08-54-D8-81-AB
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.6
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 74.128.17.114
                                            74.128.19.102
        Lease Obtained. . . . . . . . . . : Thursday, May 07, 2009 12:29:44 PM
        Lease Expires . . . . . . . . . . : Monday, January 18, 2038 11:14:07 PM


Ethernet adapter Mobo Port:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-01-29-D2-2B-5F
```

I can**not** ping either of the DNS servers for whatever reason.  However, as shown above I **can** ping [www.google.com](www.google.com).  The big problem is that I cannot get to websites and I'm assuming my failure to ping DNS servers has something to do with that.  Any assistance or advice is much appreciated. :)

So I have an internet connection, but I don't have an internet connection?  I'm not sure what's going on here.  I've tried repairing the connection and just about everything I can think of but this problem is a bugger.  Any advice would be greatly appreciated. :)

---

### Post by fatsheep on 2009-05-07
ZoneAlarm was running in the background (despite not showing up in the system tray) and apparently blocking the internet.  Everything works fine now.  :popcorn:

---

