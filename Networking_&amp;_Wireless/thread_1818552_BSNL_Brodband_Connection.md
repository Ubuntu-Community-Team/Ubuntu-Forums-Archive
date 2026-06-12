---
title: "BSNL Brodband Connection"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by ravimehrotra on 2011-08-04
Hi All,

I am using BSNL Brodband. my mordam is ZTE ZXDSL 531B. When I open my system it will show that I am connected to eth0 (which is connected to my mordam wired), but I am unable to use internet.

In windows mode it works fine. I have user id and password to access brodband.

Help me to connect my ubuntu 10.04 using the same

---

### Post by dineshs on 2011-08-05
> In windows mode it works fine. I have user id and password to access brodband.
You mean you have a dialler in windows?Then try [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9")
Also pl let us know whether [COLOR="Red"]internet[/COLOR] lamp is lighting in modem

---

### Post by ravimehrotra on 2011-08-06
Hi Dineshs,

Thanks for your quick reply.

As per description in try link, I try the same previously but it couldn't work in my case. 

Yes, Internet lamp is lighting is modem but after creating a DSL connection when I click on to connect then it will not connected

---

### Post by dineshs on 2011-08-06
If internet lamp is lighting your modem is in PPPoE mode(username and password stored in modem) so you dont need to create a DSL connection via network manager.Just connect ethernet cable from modem to PC and once network manager says "eth connection established" open firefox and proceed.If you have any difficulty please post the results of```
sudo lshw -C network
ping 4.2.2.1 -c3
route -n
```

---

### Post by ravimehrotra on 2011-08-08
My modem not in PPPoE mode

the results of commands are as follows: - 

==========================================
sudo lshw -C network
==========================================
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:80:48:61:f9:1f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=32 link=yes maxlatency=32 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:c000(size=256) memory:e5000000-e50000ff memory:20000000-2003ffff(prefetchable)

==========================================
ping 4.2.2.1 -c3
==========================================

PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 0 received, +1 errors, 100% packet loss, time 2003ms


===========================================
route -n
===========================================

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by dineshs on 2011-08-09
Pl try [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2") link.If you still have problems please boot windows, connect internet and post the result of ```
ipconfig /all
```

---

### Post by ravimehrotra on 2011-08-10
I try the above link but it not work.

My windows connection detail is as follows

Windows IP Configuration



        Host Name . . . . . . . . . . . . : srmo

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No

        DNS Suffix Search List. . . . . . : Home



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : Home

        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC

        Physical Address. . . . . . . . . : 00-80-48-61-F9-1F

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 192.168.1.3

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

        DHCP Server . . . . . . . . . . . : 192.168.1.1

        DNS Servers . . . . . . . . . . . : 192.168.1.1

                                            192.168.1.1

        Lease Obtained. . . . . . . . . . : Thursday, August 11, 2011 8:56:06 AM

        Lease Expires . . . . . . . . . . : Friday, August 12, 2011 8:56:06 AM



PPP adapter My ISP:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface

        Physical Address. . . . . . . . . : 00-53-45-00-00-00

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 117.199.168.44

        Subnet Mask . . . . . . . . . . . : 255.255.255.255

        Default Gateway . . . . . . . . . : 117.199.168.44

        DNS Servers . . . . . . . . . . . : 218.248.255.196

                                            218.248.255.194

---

### Post by dineshs on 2011-08-11
What happens when you click Network manager icon on top right of the panel and "click DSL connection" ? It should show "ethernet disconnected" followed by "DSL connection established"
Note:Why cant you configure your modem in PPPoE mode for an always ON internet connection.(At present you are using Bridge mode so you need to connect internet using a DSL dialler as explained in the previous link posted)

---

### Post by ravimehrotra on 2011-08-13
As per the link you posted previously, I check my settings of network-manger. It was the same as defined in the link. So I do nothing with my settings. 

When I restart my network-manger It would not connected either with eth0 nor with DSL Connection. Then I select the connection for eth0 it would connected. Than I test the ping 192.168.1.1 which would study after first 64bit transfer successfully for long time and then show seq=193 successfully. So I think there is some problem with LAN connection but on same machine it works fine in windows.

Now what I would do suggest me..

---

### Post by dineshs on 2011-08-13
> Then I select the connection for eth0 it would connected
But what happens when you click on DSL connection?

---

