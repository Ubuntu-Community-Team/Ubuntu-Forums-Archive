---
title: "ICS Troubles"
date: 2005-02-07
forum: Networking &amp; Wireless
---

### Post by burnt-sigil on 2005-02-07
I've got a WinXP box that's my main machine.  It has two NICs. NIC.0 connects my computer to my dad's computer and NIC.1 connects my comp to my Ubuntu box.  My WinXP box is connected to the internet via a dialup modem.  I have that internet connection shared to NIC.1 so that my Ubuntu box can be online whenever my XP box is.

But there's been a problem.  It was working fine until I updated my virus software today and had to reboot.  When I rebooted, my XP box couldn't communicate with my Ubuntu box.  I fixed this by reinstalling NIC.1's drivers and they can communicate again (not sure why I had to do that...) but now when I turn on ICS and connect to the internet, my Ubuntu box still doesn't have a net connection.  I've got eth0 set up for DHCP and have my XP box's IP address set as the DNS server.  But whenever I try to browse the internet, it times out.  And when I try to ping a website, it either gives me a 'network unreachable' error or the pings time out.  I have no idea what the problem is.  Here is the output of ifconfig for my ubuntu box:

> eth0      Link encap:Ethernet  HWaddr 00:D0:09:27:36:E7  
          inet addr:192.168.0.146  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:9ff:fe27:36e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:655441 (640.0 KiB)  TX bytes:3786750 (3.6 MiB)
          Interrupt:11 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:524622 (512.3 KiB)  TX bytes:524622 (512.3 KiB)

And here's the output of ipconfig on my windows box.

> >ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : kelewan
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Mixed
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2: **# this is NIC.1**

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Linksys NC100 Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-0C-41-EB-9A-48
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

PPP adapter VCI:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 207.162.171.164
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 207.162.171.164
        DNS Servers . . . . . . . . . . . : 207.162.160.11
                                            207.162.162.11
        NetBIOS over Tcpip. . . . . . . . : Disabled

Ethernet adapter Local Area Connection:  **# this is NIC.0**

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adap
ter
        Physical Address. . . . . . . . . : 00-07-95-41-CE-A2
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Edit:  Okay....  Found out something interesting....  linux box can ping windows box.  Windows box can browse samba shares on linux box...  But windows box can't ping linux box... O.o

---

### Post by burnt-sigil on 2005-02-07
Okay....  Found out something interesting....  linux box can ping windows box.  Windows box can browse samba shares on linux box...  But windows box can't ping linux box... O.o

---

