---
title: "Connecting static wireless"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by hroitblat on 2010-05-20
I have read this: [http://ubuntuforums.org/showthread.php?p=9318129](http://ubuntuforums.org/showthread.php?p=9318129)
I have been trying to set a static IP address for my Dell XPS 8100.  It has a wired and wireless connection.

DHCP worked fine for both of them.  My goal is to set up Samba and some other things that require a static IP.  

My /etc/network/interfaces file looks like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.154
    netmask 255.255.255.0
    gateway 192.168.1.1
    network 192.168.1.0

auto wlan0
iface wlan0 inet static
    address 192.168.1.153
    netmask 255.255.255.0
    gateway 192.168.1.1
    network 192.168.1.0


I tried setting wlan0 to the same IP as eth0.  That did not make a difference.

Tried this:
herb@Ubuntu2:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
SIOCDELRT: No such process
RTNETLINK answers: No such process
SIOCDELRT: No such process
                                                                         [ OK ]
herb@Ubuntu2:~$ 

What am I doing wrong?

ifconfig says this:
eth0      Link encap:Ethernet  HWaddr a4:ba:db:f8:5f:db  
          inet addr:192.168.1.154  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141905 (141.9 KB)  TX bytes:141905 (141.9 KB)

wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:71:8c:b0  
          inet addr:192.168.1.153  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f27b:cbff:fe71:8cb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1211697 (1.2 MB)  TX bytes:287915 (287.9 KB)

herb@Ubuntu2:~$ 

If I take the eth0 interface down, I can connect to the internet
sudo ifconfig eth0 192.168.1.154 down

Which is really puzzling because I think that I am setting both interfaces in the exact same way.  What am I missing?

Thanks,
Herb

---

### Post by Iowan on 2010-05-21
First, have you considered using the DHCP server to set up a static lease? The machine still gets a "static" address. Next, it violates some networking "rule" (which I can't quote) for a machine to have multiple interfaces in the same subnet - although I've seen articles for bridging/bonding. (That may be why only one interface activates) Having multiple gateways also complicates things - which interface should the machine use? That may be responsible for the routing (*RT*) errors

---

### Post by hroitblat on 2010-05-24
I don't think that my router will do the DHCP static part.   
I have a laptop with wired and wireless.  These two devices have different IP addresses through DHCP, but they connect to directly to the wireless router.  My Ubuntu box connects to a my Vonage router, which connects to my wireless (via wire) router.

Still you have offered good advice.  I don't really need the wireless connection.  I'm going to try to disable it. 

Here is what I get from ifconfig on my Ubuntu box:

(orcatec)herb@Ubuntu2:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr a4:ba:db:f8:5f:db  
          inet addr:192.168.15.101  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fef8:5fdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:632494 (632.4 KB)  TX bytes:579834 (579.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102852 (102.8 KB)  TX bytes:102852 (102.8 KB)

wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:71:8c:b0  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f27b:cbff:fe71:8cb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1546942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:807069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2139534969 (2.1 GB)  TX bytes:70005242 (70.0 MB)

Both eth0 and wlan0 are getting traffic, but apparently wlan0 gets the lion's share (70MB vs. 579.8KB transmitted).

Thanks,
I'll let you know what happens.
Herb

---

### Post by hroitblat on 2010-05-25
It turned out to be caused by a problem between my computer and my router.  I had plugged into my Vonage router.  although other things plugged into it work fine, this new computer was not happy.  I got myself a small 10/100/1000 switch and plugged the computer into that and plugged that into my WSG router and now everyone is happy.

Thanks for the help.
Herb

---

### Post by Iowan on 2010-05-25
Glad you found a solution - if you're convinced the problem is fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

