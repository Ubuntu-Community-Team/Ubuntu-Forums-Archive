---
title: "Using extra nic card to host internet for network"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by cjnunez on 2010-10-22
First I would like to say hello and that I'm kind of new to the Linux, but not completly slow with it either.
I have this problem that i have been trying to trouble shoot for a day or so and hope this is a godd place to start. Heres the quick and skinny, I recently installed ubuntu server on to a home built pc, after install i used sudo apt-get desktop so that way i had a place to see what i was doing rather then having to learn all the command prompt quicker then i have been able to.

I have been trying to use my second NIC card to host the internet for my network. I have installed everything and followed every possible guide i could get my hands on yet i end up with one problem or the other.

Heres what my 

```
# Set up the local loopback interface
auto lo
iface lo inet loopback

# Set up the external interface
#
auto eth1
iface eth1 inet dhcp
    post-up iptables-restore < /etc/iptables.up.rules

# Set up the internal wired network
#
#
auto eth0
iface eth0 inet dhcp

```Heres a copy of my ifconfig:

```
king@king-media:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:0c:41:23:a5:b1  
          inet6 addr: fe80::20c:41ff:fe23:a5b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5159370 (5.1 MB)  TX bytes:749545 (749.5 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:0c:41:23:a5:b1  
          inet addr:169.254.8.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0c:41:23:a5:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:61724 errors:9 dropped:0 overruns:0 frame:13
          TX packets:554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6855315 (6.8 MB)  TX bytes:102237 (102.2 KB)
          Interrupt:16 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:14:2a:bb:ef:71  
          inet addr:70.174.46.46  Bcast:70.174.47.255  Mask:255.255.248.0
          inet6 addr: fe80::214:2aff:febb:ef71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:593890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:199687531 (199.6 MB)  TX bytes:14638952 (14.6 MB)
          Interrupt:23 

eth0:avahi Link encap:Ethernet  HWaddr 00:0c:41:23:a5:b1  
          inet addr:169.254.8.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8824306 (8.8 MB)  TX bytes:8824306 (8.8 MB)
```What I don't get is that it is trying to connect from eth0 and aquire a dhcp address (eth0:avahi), yet in the dhcpd.conf file i have it set to accept incoming connections and listen on that device.

Heres a copy of my /etc/dhcp3/dhcpd.conf:

```

ddns-update-style none;

option domain-name-servers 145.253.2.75, 193.174.32.18;

default-lease-time 86400;
max-lease-time 604800;

authoritative;

shared-network home {
    subnet 192.168.0.0 netmask 255.255.255.0 {
        authoritative;
        range 192.168.0.2 192.168.0.33;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.0.255;
        option routers 192.168.0.1;
        range 192.168.0.200 192.168.0.229;
        }
    host eth0 {
        hardware ethernet 00:0c:41:23:a5:b1;
        fixed-address 192.168.0.1;
                }
    }
```This is a copy of my syslog when i try and restart the dhcpd server:

> Oct 22 21:45:50 king-media dhclient: DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 5
Oct 22 21:45:55 king-media dhclient: No DHCPOFFERS received.
Oct 22 21:45:55 king-media dhclient: No working leases in persistent database - sleeping.
Oct 22 21:45:58 king-media dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 22 21:46:05 king-media dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Oct 22 21:46:16 king-media dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Oct 22 21:46:17 king-media dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Oct 22 21:46:17 king-media dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Oct 22 21:46:17 king-media dhcpd: Wrote 0 deleted host decls to leases file.
Oct 22 21:46:17 king-media dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 22 21:46:17 king-media dhcpd: Wrote 1 leases to leases file.
Oct 22 21:46:17 king-media dhcpd: 
Oct 22 21:46:17 king-media dhcpd: No subnet declaration for eth0 (169.254.8.1).
Oct 22 21:46:17 king-media dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 22 21:46:17 king-media dhcpd:    you want, please write a subnet declaration
Oct 22 21:46:17 king-media dhcpd:    in your dhcpd.conf file for the network segment
Oct 22 21:46:17 king-media dhcpd:    to which interface eth0 is attached. **
Oct 22 21:46:17 king-media dhcpd: 
Oct 22 21:46:17 king-media dhcpd: 
Oct 22 21:46:17 king-media dhcpd: Not configured to listen on any interfaces!


Hope this is not to much at one time and I thank you so very much for your time, be happy to provide any further information that you need just let me know please. Also any changes I make will be posted here. 

Thanks again
Joe

---

### Post by utilitytrack on 2010-10-23
> **cjnunez said:**
> I have installed everything and followed every possible guide
[B]
:)[/B]

> ```
br0:avahi Link encap:Ethernet  HWaddr 00:0c:41:23:a5:b1  
          inet addr:169.254.8.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:avahi Link encap:Ethernet  HWaddr 00:0c:41:23:a5:b1  
          inet addr:169.254.8.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xc000
```


**:))**


Hello. Here is my thought.
Disable DHCP, set static IP's everything, turn off firewall and kill all non-needed services (especially Avahi). If you can to set up your home network now, we can to continue.

---

### Post by cjnunez on 2010-10-23
Dear utilitytrack,

Thanks for start of assist, heres what i found so far followed by changes i have made in last few hours. I removed the bridge (br0) that was tolink my wireless card with my main internal NIC. and edited appropriate files as such:

/etc/network/interfaces:

```
# Set up the local loopback interface
auto lo
iface lo inet loopback

# Set up the external interface
#
auto eth1
iface eth1 inet dhcp
	post-up iptables-restore < /etc/iptables.up.rules

# Set up the internal wired network
#
#
auto eth0
iface eth0 inet static
	address 192.168.1.1
	netmask 255.255.255.0
```

/etc/dhcp3/dhcpd.conf:


```
ddns-update-style none;
ignore client-updates;

subnet 192.168.1.0 netmask 255.255.255.0 {
 
   # The range of IP addresses the server
   # will issue to DHCP enabled PC clients
   # booting up on the network
 
   range 192.168.1.201 192.168.1.220;
 
   # Set the amount of time in seconds that
   # a client may keep the IP address

  default-lease-time 86400;
  max-lease-time 86400;
 
   # Set the default gateway to be used by
   # the PC clients
 
   option routers 192.168.1.1;
   # Don't forward DHCP requests from this
   # NIC interface to any other NIC
   # interfaces
 
   option ip-forwarding off;
 
   # Set the broadcast address and subnet mask
   # to be used by the DHCP clients
 
  option broadcast-address 192.168.1.254;
  option subnet-mask 255.255.255.0;
  
   # Set the NTP server to be used by the
   # DHCP clients

  option ntp-servers 192.168.1.100;

   # Set the DNS server to be used by the
   # DHCP clients

  option domain-name-servers 192.168.1.100;
 
   # If you specify a WINS server for your Windows clients,
   # you need to include the following option in the dhcpd.conf file:

  option netbios-name-servers 192.168.1.100;
 
   # You can also assign specific IP addresses based on the clients'
   # ethernet MAC address as follows (Host's name is "linksys router":

  host linksys {
      hardware ethernet 00:25:9c:5b:83:7a;
     fixed-address 192.168.1.222;
   }
}
#
# List an unused interface here
#
subnet 192.168.2.0 netmask 255.255.255.0 {
}

```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:0c:41:23:a5:b1  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fe23:a5b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1063 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:280992 (280.9 KB)  TX bytes:103916 (103.9 KB)
          Interrupt:16 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:14:2a:bb:ef:71  
          inet addr:70.174.46.46  Bcast:70.174.47.255  Mask:255.255.248.0
          inet6 addr: fe80::214:2aff:febb:ef71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10246726 (10.2 MB)  TX bytes:1857613 (1.8 MB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:624418 (624.4 KB)  TX bytes:624418 (624.4 KB)

```

Now my next step is to get my wireless router to communicate with the server correctly to share it with other pcs. thank you for your help.

Joe

---

### Post by utilitytrack on 2010-10-28
Please mark this thread as solved.

---

