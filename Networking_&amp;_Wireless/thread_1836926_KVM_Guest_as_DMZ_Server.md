---
title: "KVM Guest as DMZ Server?"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by Githlar on 2011-08-31
I'm just toying around with networking a bit and I decided I wanted to set up a VM as a honeypot. Well, I've been working with this for days and I finally got the tap interface working with KVM (which is a huge pain if you're a newbie!). So, I got everything set up and I set my router to use 192.168.1.102 (my VM guest) as the DMZ server and I've been getting some kind of sporadic behavior. So, first let me post my set-up:

/etc/network/interfaces:```

auto lo
iface lo inet loopback

# The bridge network interface(s)
auto br0
iface br0 inet dhcp
	bridge_ports eth0
	bridge_maxwait 2
        bridge_ageing 0
up /sbin/ifconfig eth0 inet 0.0.0.0 promisc

auto eth0
iface eth0 inet static
	address 192.168.1.101
	netmask 255.255.255.0
```


`ifconfig` (with KVM running):```

br0       Link encap:Ethernet  HWaddr 00:21:9b:dd:bf:cb  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fedd:bfcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19127982 (19.1 MB)  TX bytes:968037 (968.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:21:9b:dd:bf:cb  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fedd:bfcb/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:61975 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82160782 (82.1 MB)  TX bytes:4840093 (4.8 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35579 (35.5 KB)  TX bytes:35579 (35.5 KB)

tap0      Link encap:Ethernet  HWaddr 2e:b8:98:32:cb:8c  
          inet6 addr: fe80::2cb8:98ff:fe32:cb8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:9912 (9.9 KB)  TX bytes:634130 (634.1 KB)

virbr0    Link encap:Ethernet  HWaddr 2a:48:14:b2:13:30  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:7788 (7.7 KB)
```

Router configuration:
- Acts as DHCP server, however 192.168.1.4 and 192.168.1.102 are both reserved for their respective MAC addresses
- Port forwards for several ports to 192.168.1.4 - includes http,ssh and more
- DMZ server set as 192.168.1.102

I for testing, I did clear all my iptables rules from the guest's filter table. I have set no iptables rules on the VM host.

Now, if I do all these tests using 192.168.1.x addresses, everything seems to work fine.

1. Ping me.mydomain.com (me.mydomain.com forwards to my actual IP address) - works
2. SSH me.mydomain.com - gives me the host hash of the VM's ssh server
3. [http://me.mydomain.com/](http://me.mydomain.com/) - times out (there is no http server set up)
4. telnet me.mydomain.com 86 - connection times out. For this one, when using 192.168.1.102, I get an ICMP rejection.

I also tried setting up my VM host as the DMZ server and setting iptables rules to DNAT/SNAT all ports to the guest and that didn't fly either.

Can anybody explain to me what I did wrong?

---

### Post by Githlar on 2011-09-02
I figured out what my problem was: my router drops connection attempts that don't have a listening socket attached. In my case I was testing a port knocking scheme. The packet made it to the router, but since nothing was listening on the port it dropped the connection. It works if I use a tool like nmap or knock.

---

