---
title: "no internet connection after install"
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by grw on 2005-12-07
I have jsut installed Ubuntu 5.10 but can't connect to teh network. 

One problem with installation - i got a message saying that the Network autoconfiguration was successful but no default route was set. I continued anyway.

I have configured eth0 with System > Admin > Networking

After browsing these forums I ran a few commands in teh terminal and got this (I'll type a summary - I can't copy the data to floppy cos there's a prob after mounting the thing with sudo mount -t msdos /dev/fd0 /media/floppy - "Invalid parameters" when copying data):

Ping 139.184.32.27
Network is unreachable

ifconfig -a
eth0 .....   everything seems ok at first I think ...
               UP BROADCAST RUNNING MULTICAST  MTU:1500  METRIC:1
               RX packets: 1904 errors: 0 dropped: 0 overuns: 0 frame: 0
               TX packets: 9 errors: 0 ... 0... 0... 0
               Collisions: 0 txqueuelen: 1000
               RX bytes: 223820    TX bytes: 1746

lo             RX packets: 5489 errors: 0 ....0....0.....0
               TX packets: 5489 ....0.....0....0.....0.

Sit0    Link encap:IPv6 - in - IPv4
         NOARP  MTU:1480 Metric:1
         Then all values 0

Prompt> route
Kernel IP routing table
Destination       Gateway       Genmask      Flags  Metric   Ref      Use  Iface
That's it .... no info under any of these

Any ideas

---

### Post by stuporglue on 2005-12-07
Try reconfiguring your ethernet interface in System-->Administration-->Networkng. 

See if you can bring it up by clicking the buttons there.

---

### Post by grw on 2005-12-07
I've tried doing that. It's set up for DHCP. Nothing.
Is the routing table not the problem?

---

### Post by mips on 2005-12-07
Do you actually get allocated an IP address via DHCP ?

---

### Post by grw on 2005-12-07
I think so. But how exactly do I tell?

---

### Post by grw on 2005-12-07
I have been trying to create an IP routing table. When i try to add a default route (which is what the installation couldn't detect) I get a message saying 'Network is unreachable'. Well, I actually have little idea if I am doing things right. Help!!

---

### Post by mips on 2005-12-07
Follow this guide,  [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)


Output of **ifconfig eth0**
eth0    Link encap:Ethernet  HWaddr 00:AA:BB:DD:55:22
          inet addr:**[COLOR="Red"]192.168.0.5[/COLOR]**  Bcast:192.168.0.255  Mask:255.255.255.0
         .....

---

### Post by tonysathre on 2005-12-07
from your ifconfig it didnt look like u even had an IP, try running:

ifdown eth0 && ifup eth0 && dhclient --> from a terminal

note: u might need sudo

---

### Post by %hMa@?b&lt;C on 2005-12-07
try "sudo pppoeconf"
worked for me
Note: this only works with pppoe interntet ie VERIZON DSL

---

### Post by grw on 2005-12-08
[QUOTE=mips]Follow this guide,  [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)


Output of **ifconfig eth0**
eth0    Link encap:Ethernet  HWaddr 00:AA:BB:DD:55:22
          inet addr:**[COLOR="Red"]192.168.0.5[/COLOR]**  Bcast:192.168.0.255  Mask:255.255.255.0
         .....[/QUOTE]

I have followed the guide above. Everything goes fine to start with. I have an inet addr. etc.
Link encap: Ethernet  HW addr 00:20:e0:6e:a0:66
inet addr:10.0.10.234 Bcast:10.0.10.234 Mask: 255.255.255.255
etc

> route -n 
This gives me an empty Kernel IP routing table. No entries at all. It just gives the headings: Destination  Gateway   genmask etc

> dhclient eth0 
It says: 

There is already a pid file /var/run/dhclient.pid with pid 7791
killed old pid process, removed pid file
Internet systems consortium DHCP client v3.0.2 ....

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:20:e0:6e:a0:66
Sending on LPF/eth0/00:20:e0:6e:a0:66
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.8.1
SIOCADDRT: Network is unreachable
bound to 10.0.10.234 - - renewal in 4889 seconds

Can't ping anything except localhost

Later the troubleshooting doc suggests disabling ipv6. I have not done this. I am on an academic network which may ? use ipv6 (it came up some where in my first post)

>cat /etc/network/interfaces
This gives me: ....
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
           script grep
           map eth0

auto eth0
iface eth0 inet dhcp

?????

---

### Post by mips on 2005-12-09
[QUOTE=grw]I have followed the guide above. Everything goes fine to start with. I have an inet addr. etc.
Link encap: Ethernet  HW addr 00:20:e0:6e:a0:66
inet [COLOR="Red"]addr:10.0.10.234 Bcast:10.0.10.234 Mask: 255.255.255.255[/COLOR]
etc

> route -n 
This gives me an empty Kernel IP routing table. No entries at all. It just gives the headings: Destination  Gateway   genmask etc
[/QUOTE]

Those parameters are incorrect. The IP address & Broadcast address are the same and you have a netmask of 255.255.255.255 which only caters for a single IP address, hence the same address for broadcast & IP. There is no way to establish comms between two endpoints with a 255.255.255.255 netmask.

You want something like:
IP Address:10.0.10.3
Gateway: 10.0.10.1 
Bcast:10.0.10.255
Mask: 255.255.255.0

Check out your routers config to establish the gateway address.

---

### Post by grw on 2005-12-09
Thanks for your reply. 

Can you tell me how to check out the router config to establish teh gateway address?

When I boot into Windows (where everything works fine) this is the info I get:

        Connection-specific DNS Suffix  . : sussex.ac.uk
        IP Address. . . . . . . . . . . . : 10.0.9.96
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 10.0.8.1

C:\Documents and Settings\Gwyn W.GWYN>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 20 e0 6e a0 66 ...... Intel 8255x-based PCI Ethernet Adapter (10/100)
- Packet Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0         10.0.8.1       10.0.9.96       30
        10.0.9.96  255.255.255.255        127.0.0.1       127.0.0.1       30
   10.255.255.255  255.255.255.255        10.0.9.96       10.0.9.96       30
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
        224.0.0.0        240.0.0.0        10.0.9.96       10.0.9.96       30
  255.255.255.255  255.255.255.255        10.0.9.96       10.0.9.96       1
Default Gateway:          10.0.8.1
===========================================================================
Persistent Routes:
  None

---

### Post by mips on 2005-12-09
[QUOTE=grw]Thanks for your reply. 

Can you tell me how to check out the router config to establish teh gateway address?

When I boot into Windows (where everything works fine) this is the info I get:

        Connection-specific DNS Suffix  . : sussex.ac.uk
        IP Address. . . . . . . . . . . . : 10.0.9.96
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 10.0.8.1
[/QUOTE]

Even those settings appear wrong.
According to that you gateway is 10.0.8.1

How do you actually connect to the net ?
Cable or ADSL ?
Do you have a modem or a router, provide brand&model ?
Who is your ISP ?

Looks like you are at some educational facility in Sussex. They might use a proxy server to grant internet access. Maybe contact your network admin and ask him/her for all relevant setting and come back to us.

---

### Post by grw on 2005-12-13
Been away for a few days, which is why I didn't post a reply to your query. I am connected to a university network which does have a proxy server. I am on what's is called the 'roaming network' - although I am plugged in with ethernet cable, I could, technically, connect to the network anywhere via wireless. According to one of teh IT people here, the network settings that you found so strange are something to do with being on this roaming network. Anyway, he didn't seem to know too much about it and is looking into things (and into Ubuntu). So I'll wait to see what happens and will let the thread drop for teh moment.
Thanks a lot though mips.

---

### Post by incrept on 2008-05-23
I currently installed 8.04 on my computer (dell dimension 3000) and after the install i have no connection, no ip actually nothing. and im very new to linux. what could possibly be the problem?

---

