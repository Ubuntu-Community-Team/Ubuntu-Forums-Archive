---
title: "No wired internet"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by o4_srt on 2009-04-21
Just finished installing kubuntu 8.10 x64 on my sony vaio vgn-fw260j. Still working on the graphics issue with the intel 4 chipsets, but the internet is my main priority.

Laptop is dual boot with vista x64. Internet works fine with vista. Connection type is wired, set to DHCP in windows. When I open up a browser in windows, i get a login screen. I type my user id and password, hit login, and internet works. However, in kubuntu, I never get the login screen.

I used the network manager to create a new DHCP connection for eth0. As far as I can tell, kubuntu is pulling a valid IP, just no internet. 

-eth0 dev is a arvell yukon 88E8055 PCI-E Gigabit Ethernet Controller

- ISP is US Comz, operating on camp taji, iraq

-login address is phc.prontonetworks.com/cgi-bin/authlogin

-internet connects to multiple connections in vista, even though using only 1 NIC and cable. could this cause a problem?

- power save feature is NOT enabled for NIC in vista

Outputs are as follows:

**bru@bru-laptop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:81:c6:82  
          inet addr:172.30.41.175  Bcast:172.30.41.175  Mask:255.255.255.255
          inet6 addr: fe80::21d:baff:fe81:c682/64 Scope:Link                
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                
          RX packets:43849 errors:0 dropped:0 overruns:0 frame:0            
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0             
          collisions:0 txqueuelen:1000                                      
          RX bytes:2685395 (2.6 MB)  TX bytes:8665 (8.6 KB)                 
          Interrupt:16                                                      

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2016 (2.0 KB)  TX bytes:2016 (2.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:83:a3:8c
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-83-A3-8C-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




**bru@bru-laptop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


[B]

bru@bru-laptop:~$ route -n[/B]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0


[B]
bru@bru-laptop:~$ ping -c 3 208.67.219.101[/B]
connect: Network is unreachable



**bru@bru-laptop:~$ ping -c 3 [www.opendns.com](www.opendns.com)**
ping: unknown host [www.opendns.com](www.opendns.com)

---

### Post by Iowan on 2009-04-21
> **o4_srt said:**
> 
**bru@bru-laptop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:81:c6:82  
          inet addr:172.30.41.175  Bcast:172.30.41.175  [COLOR="Red"]Mask:255.255.255.255[/COLOR]
          inet6 addr: fe80::21d:baff:fe81:c682/64 Scope:Link                
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                
          RX packets:43849 errors:0 dropped:0 overruns:0 frame:0            
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0             
          collisions:0 txqueuelen:1000                                      
          RX bytes:2685395 (2.6 MB)  TX bytes:8665 (8.6 KB)                 
          Interrupt:16                                                      
Something seems odd about a machine in it's own subnet... Does Vista give same results?

---

### Post by o4_srt on 2009-04-21
no, i'm 95% sure that the subnet in vista is 255.0.0.0 but i am at work at the moment. I'll post ipconfig /all when I have access to the pc again.

---

### Post by doas777 on 2009-04-21
well the problem is your route. you need a route to 0.0.0.0
```

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0


```

do you know the ip address of the correct gateway?
try this:
```

sudo route add default gw <GatewayIPAddress> eth0

``` (where <GatewayIPAddress> is... well...the ip address of your gateway..)

---

### Post by doas777 on 2009-04-21
> **o4_srt said:**
> no, i'm 95% sure that the subnet in vista is 255.0.0.0 but i am at work at the moment. I'll post ipconfig /all when I have access to the pc again.
it kinda looks like you are on a micro-segmented vlan, with no other hosts. are you in a school dorm? that would be one way to keep the students from trying to hack each other.

---

### Post by o4_srt on 2009-04-21
not a school dorm, but probably set up similar.

one ISP here, with a satellite connection. 2 LAN drops run to every room here on post.

ipconfig /all in vista will show me the gateway i'm connected to, correct?

also, i'm unsure whether it uses that gateway all the time, because in vista, i connect to multiple connections when connected to the internet. Probably 5-10 different connections show up altogether.

---

### Post by o4_srt on 2009-04-22
Ok here's my ipconfig /all from vista:

Host Name - Greg-PC
Primary DNS Suffix - (blank)
Node Type - Mixed
IP Routing Enabled - No
WINS proxy enabled - No
DNS Suffix search list - mshome,  net

Ethernet adapter Local Area Connection:
connection-specific DNS suffix - mshome
description - marvell yukon 99E9055 PCI-E Gigabit Ethernet Adapter
Physical Address - 00-1D-BA-81-C6-82
DHCP Enabled - Yes
Autoconfiguration Enabled - Yes
Link-Local IPv6 Address - fe80::bd8b:8d35:c94:f4ba%10 (preferred)
IPv4 Address - 172.30.57.151 (preferred)
subnet mask - 255.255.255.255
(lease stuff omitted, not important)
default gateway - fe80::65aa:67f4:934f:fd7%10
                  fe80::444d:2b22:5797:526c%10
                  fe80::4845:c4e7:717a:c93d%10
                  fe80::f4f6:c724:c3de:eddc%10
                  fe80::3840:283e:c36a:1522%10
                  fe80::a1b2:d410:d27c:b473%10
             (a few more, not posting them unless its releveant)
                  172.30.1.1
DHCP server - 172.30.1.1
DHCPv6 IAID - 251665024
DHCPv6 Client DUID - 00-01-00-01-10-E1-CA-D9-00-1D-bA-81-C6-82

DNS Servers - fe80::a55a:cd83"b6cb:efbc%10
              172.30.1.1
NetBIOS over tcpip - enabled
Connection-specific DNS suffix search list - mshome, net




Do you need information for the 10 tunnel adapters as well?

---

### Post by doas777 on 2009-04-22
hmmm. in windows, try running 'route print' and let us know what it says.

also, do you have any proxies defined in Interet Explorer?

one last thing, if you disable IPv6 in windows, does the internet still work?

---

