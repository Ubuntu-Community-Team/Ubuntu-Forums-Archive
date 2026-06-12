---
title: "internet connection"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by jlal on 2010-11-13
Both PCs have dual boot - windows & ubuntu 10.04.

Home:
I am using adsl wired modem (nokia siemens make) supplied by BSNL, India. For the first few days, internet worked well. Then, I am unable to connect to internet. Even the iPod which was connecting could not be connected.

But the windows is able to connect to internet. All attempts to connect have failed.

Office:
I have two cards with adsl wired modem. One for intranet in the company and other for internet. In windows both are working. But, in ubuntu I could not connect even once.

Would appreciate help. I have tried the steps in documentation without any success.
Thanks

---

### Post by uncaspi on 2010-11-13
Please post sudo /sbin/route

---

### Post by jlal on 2010-11-15
sudo /sbin/route response
Home PC:
Kernel IP routing table 
Destination  Gateway    Genmask      Flags Metric Ref  Use Iface 
192.168.1.0     *    255.255.255.0   U     0      0    0   eth0 
default     192.168.1.1  0.0.0.0     UG    0      0    0   eth0 
Home PC is responding to ping 192.168.1.1

Office PC:
Kernel IP routing table 
Destination  Gateway    Genmask      Flags Metric Ref  Use Iface 
192.168.1.0     *    255.255.255.0   U     1      0     0 eth1 
link-local      *    255.255.0.0     U     1000   0     0 eth1 
default     192.168.1.1  0.0.0.0     UG    0      0     0 eth1 
Ping not tried in office PC.

Windows ipconfig /all output in office PC.


Windows IP Configuration



        Host Name . . . . . . . . . . . . : dgmvig

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local ISP:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC

        Physical Address. . . . . . . . . : 00-80-48-5C-A1-26

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 10.150.25.98

        Subnet Mask . . . . . . . . . . . : 255.255.0.0

        Default Gateway . . . . . . . . . : 10.150.100.1



Ethernet adapter Local BSNL:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Intel(R) 82566DM-2 Gigabit Network Connection

        Physical Address. . . . . . . . . : 00-1E-90-30-C8-C2

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 192.168.1.3

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

        DHCP Server . . . . . . . . . . . : 192.168.1.1

        DNS Servers . . . . . . . . . . . : 192.168.1.1

        Lease Obtained. . . . . . . . . . : Tuesday, November 16, 2010 9:01:30 AM

        Lease Expires . . . . . . . . . . : Friday, November 19, 2010 9:01:30 AM



Ethernet adapter Local Blue tooth:



        Media State . . . . . . . . . . . : Media disconnected

        Description . . . . . . . . . . . : Bluetooth PAN Network Adapter

        Physical Address. . . . . . . . . : 00-15-83-15-A3-10



PPP adapter bsnl:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface

        Physical Address. . . . . . . . . : 00-53-45-00-00-00

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 59.93.213.217

        Subnet Mask . . . . . . . . . . . : 255.255.255.255

        Default Gateway . . . . . . . . . : 59.93.213.217

        DNS Servers . . . . . . . . . . . : 218.248.241.6

                                            218.248.240.180

        NetBIOS over Tcpip. . . . . . . . : Disabled

---

### Post by dineshs on 2010-11-16
To make the home PC OK ,
Try   
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
If you have problems please post the results of
```
sudo lshw -C network
``` and ```
ping 4.2.2.1 -c3
```
_Office PC_
Please post the result of ```
ifconfig -a
```
Do you use BSNL broadband both in the office and residence?Can you tell me the exact model name?

---

### Post by jlal on 2010-11-18
Home PC:

Backup done.
interfaces file edited.

Step-II
No such service. There seems to be no such file. In menu under administration only network tools are available though every book talks about network manager.
I have done one update of all the software directly without any problem.

Step-III
sudo lshw -C network

  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:77:e3:b5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:ff500000-ff500fff ioport:bc00(size=64)

PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
From 192.168.1.1 icmp_seq=3 Destination Net Unreachable

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1998ms

Modem: BSNL supplied.
Nokia siements networks router
cz tjm-86-006
residential router 1600
P/N:v50121-s9001-m102

NM icon: 
There is no thumb nail in rh top corner. It was there earlier and has vanished.
ping doesn't work other than 192.168.1.1
ping 192.168.1.0 asks about broadcast.
ping [www.google.co.in](www.google.co.in) doesn't work.

Office PC:
Shall try after I join duty.
Thanks

---

### Post by dineshs on 2010-11-18
> In menu under administration only network tools are available though every book talks about network manager.
It is under system-preferences as network connections
Do you get the icon back when you 
rightclick on top panel-add to panel-click Notification area then add ?

---

### Post by jlal on 2010-11-18
After rebooting, the network manger icon up/down arrows is visible.
There are several connections available.
DSL
Disconnect

Available
wired connection 1
eth2
eth0
auto eth0
DSL Connection 1
Auto eth0
eth0
DSL Connection 1

see attachment about connection details.

---

### Post by dineshs on 2010-11-18
> There are several connections available.
Rightclick NM-edit connections
You need to have only one Auto eth0 under wired tab and one DSL connection  under DSL tab.So delete all other connections.
From The attached screenshot DSL seems to be connected.Please check whether pages are loading.If not 
Right-click on the NM icon-edit connections-click DSL tab-click the DSL connection-edit-ipv4-Auto PPPoE addresses only-enter DNS as 4.2.2.1 and apply

---

### Post by jlal on 2010-11-19
I am able to navigate the net since my last posting yesterday. Thanks a lot.

I am trying for my company to switch over to dual systems i.e.windows and ubuntu so that over a period of time we migrate to linux fully.

In spite of starting the internet I am not fully aware of the process and the files for setting up an internet connection. Could you, briefly explain.

Regarding office PC, I will post either on 20th or 2nd.

At least my family members will become familiar and comfortable with ubuntu though windows cannot be done away as the school projects are in window based.

Many a thanks for the help.

---

### Post by dineshs on 2010-11-19
> In spite of starting the internet I am not fully aware of the process and the files for setting up an internet connection. Could you, briefly explain.
As I said the GUI tool Network manager is very easy to configure.You can use it for DSL VPN Mobile broadband or connection sharing.It has seperate tabs for that .Only thing ensure that /etc/network/interfaces contain only those 2 lines as explained in the link I posted earlier
In case you have any difficulty the forum is always here to help you

---

### Post by jlal on 2010-11-20
Thanks. I will try to update myself as I haven't worked in unix, linux(redhat) for several years. New to ubuntu.

Best wishes.

Bye

---

