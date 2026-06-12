---
title: "eth0 ARP not working"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by embedUser on 2011-07-24
Hi 
I have been using Ubuntu 11.04 for a month. I am trying to connect a MINI2440 to my Laptop with Ubuntu on it. MINI2440 is a SBC with u-boot 1.3.2 on it. My problem is that when I am trying to download a image from my laptop to the board through TFTP, it is timing out. I installed wireshark to see the network messages. I am able to see ARP requests originating from my mini2440 and ARP replies being sent by the laptop but mini2440 doesnt acknowledge them and keeps sending ARP requests. When mini2440 tries to ping my Ubuntu machine, my Ubunnut machine doesnt respond to ARP requests .
Following is the config in my /etc/network/interfaces file
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
#gateway 192.168.1.1
 
IP address on my mini2440 is 192.168.1.2
I have disable ufw, selinux and avahi-daemon on my ubuntu. 
When I connect a Windows based system with my Mini2440 both are able to communicate and mini2440 acknowledges the ARP replies from the windows machine. Ping is successful between them.
I am also able to ping from my Ubuntu laptop to my windows machine,
IP address of my windows machine is 192.168.1.3
I dont think its a physical layer issue as the same cable is being used in all three scenarios and the connection between each machine is direct. 
Following is the output of ifconfig
eth0 Link encap:Ethernet HWaddr b8:70:f4:02:a7:4a 
inet addr:192.168.1.4 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::ba70:f4ff:fe02:a74a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2078 errors:0 dropped:0 overruns:0 frame:0
TX packets:3472 errors:0 dropped:0 overruns:0 carrier:129
collisions:0 txqueuelen:1000 
RX bytes:128306 (128.3 KB) TX bytes:237515 (237.5 KB)
Interrupt:43 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2665 errors:0 dropped:0 overruns:0 frame:0
TX packets:2665 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:252070 (252.0 KB) TX bytes:252070 (252.0 KB)
wlan0 Link encap:Ethernet HWaddr 68:a3:c4:3d:ae:e6 
inet addr:192.168.0.189 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::6aa3:c4ff:fe3d:aee6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:313206 errors:0 dropped:0 overruns:0 frame:0
TX packets:214101 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:430131511 (430.1 MB) TX bytes:28154643 (28.1 MB)
 
and following is the result of route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
192.168.0.0 0.0.0.0 255.255.255.0 U 2 0 0 wlan0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlan0
0.0.0.0 192.168.0.1 0.0.0.0 UG 0 0 0 wlan0
Please let me know if any configuration is missed out.
Thanks.

---

### Post by capscrew on 2011-07-24
> **embedUser said:**
> Hi 
I have been using Ubuntu 11.04 for a month. I am trying to connect a MINI2440 to my Laptop with Ubuntu on it. MINI2440 is a SBC with u-boot 1.3.2 on it. My problem is that when I am trying to download a image from my laptop to the board through TFTP, it is timing out. I installed wireshark to see the network messages. I am able to see ARP requests originating from my mini2440 and ARP replies being sent by the laptop but mini2440 doesnt acknowledge them and keeps sending ARP requests. When mini2440 tries to ping my Ubuntu machine, my Ubunnut machine doesnt respond to ARP requests .
...
auto eth0
iface eth0 inet static
address 192.168.1.4
...
IP address on my mini2440 is 192.168.1.2
...
When I connect a Windows based system with my Mini2440 both are able to communicate and mini2440 acknowledges the ARP replies from the windows machine. Ping is successful between them.
I am also able to ping from my Ubuntu laptop to my windows machine,
IP address of my windows machine is 192.168.1.3
...

Following is the output of ifconfig
eth0 Link encap:Ethernet HWaddr b8:70:f4:02:a7:4a 
inet addr:192.168.1.4
...
Please let me know if any configuration is missed out.
Thanks.

I don't think this is an  ARP issue.  ARP is really part of Ethernet as it links the MAC address to the IP address on local links only (LAN).  It is layer 2.  As you have said you have connectivity with all devices including the MINI2440 except when using tftp.

I'm sure wireshark will reveal the problem.  What does the data in the packets (Layer 3 and above) show?  What do you see in the frames (Layer 2).

You should be able to see and confirm that the MAC addresses are correct for all hosts.

You can manually confirm the mac address like this```
arp <IP address>
```

---

### Post by embedUser on 2011-07-25
Hi Capscrew,
Yeah I realize its also not an ARP issue. But about connectivity about the devices I would like to clear the confusion that PING between mini2440 and Ubuntu is not working. So we have a situation where Mini2440 can connect to Windows machine and windows machine can connect to Linux laptop but Linux laptop and mini2440 cannot talk to each other. 
As suggested I was monitoring messages on wireshark and saw that on trying a PING from mini2440, mini2440 sent an ARP request packet for Linux machine, but the Linux machine didnt respond back. When a ARP request was sent as part of TFTP then Linux replied to the ARP request but mini2440 didnt receive any reply, at least the debug prints dont show any reception of packets. 
The ARP requests and replies were all proper and had the correct MAC addresses.
I tried after disabling ufw, seLinux and avahi-daemon but the same result.
So I still doubt if any configuration is incorrect .
on trying on my linux laptop -- 192.168.1.2 is th IP address of mini2440 
arp 192.168.1.2
192.168.1.2 (192.168.1.2) -- no entry
 
Thanks

---

### Post by capscrew on 2011-07-25
> **embedUser said:**
> Hi Capscrew,
...
So I still doubt if any configuration is incorrect .
on trying on my linux laptop -- 192.168.1.2 is th IP address of mini2440 
arp 192.168.1.2
192.168.1.2 (192.168.1.2) -- no entry
 
Thanks
That would appear to mean that there is no ARP cache record.   See what is in the ARP cache and post it back here with this ```
arp -a
```

Try to broadcast ARP requests across the entire subnet and post that ```
ping -b 192.168.1.255
```

The above assumes that the b'cast address for your network is 192.168.1.255 ;-)

---

### Post by embedUser on 2011-07-26
Hi Capscew 
Following is the result of arp -a on my Ubuntu machine before mini2440 did a tftp request 
? (192.168.0.1) at 00:1b:11:a0:c1:d4 [ether] on wlan0
? (192.168.0.1) at 00:1b:11:a0:c1:d4 [ether] on wlan0
Following is the result after mini2440 did a TFTP request
? (192.168.1.2) at 08:00:2f:00:00:02 [ether] on eth0
? (192.168.0.1) at 00:1b:11:a0:c1:d4 [ether] on wlan0
On trying a broadcast ping I got the following result -
 ping -b 192.168.1.255
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
on doing a CTRL+ C
--- 192.168.1.255 ping statistics ---
505 packets transmitted, 0 received, 100% packet loss, time 506893ms
In this case there were no ethernet packets sent out on eth0, as shown by Wireshark. 
 
When I did a ping on 192.168.1.2 (Mini2440 IP address) these were sent out of the "lo" interface.  
 
Following is output of ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:02:a7:4a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe02:a74a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:360 (360.0 B)  TX bytes:828 (828.0 B)
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18965 (18.9 KB)  TX bytes:18965 (18.9 KB)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:3d:ae:e6  
          inet addr:192.168.0.189  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe3d:aee6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1353822 (1.3 MB)  TX bytes:452752 (452.7 KB)
and following are the routes defined output of route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
 
Thanks

---

### Post by capscrew on 2011-07-26
> When I did a ping on 192.168.1.2 (Mini2440 IP address) these were sent out of the "lo" interface. 

Who were you pinging?  This does not make sense unless you are pinging yourself (the host you are at).  The loopback (lo) on any host is only for testing that hosts IP stack.  If the mini2440 uses the loopback adapter when attempting tftp requests it will always fail.  

The rest of the information is becoming hard for me to decipher. 
> ping -b 192.168.1.255
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
on doing a CTRL+ C
--- 192.168.1.255 ping statistics ---
505 packets transmitted, 0 received, 100% packet loss, time 506893ms
In this case there were no ethernet packets sent out on eth0, as shown by Wireshark.
From which host did you do the above ping?  Did you delete the data? You should have gotten some of these```
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.468 ms
64 bytes from 192.168.1.245: icmp_seq=1 ttl=64 time=1.80 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=1 ttl=64 time=6.90 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.458 ms
64 bytes from 192.168.1.245: icmp_seq=2 ttl=64 time=0.736 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=2 ttl=64 time=6.00 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.440 ms
64 bytes from 192.168.1.245: icmp_seq=3 ttl=64 time=0.761 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=3 ttl=64 time=6.00 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.471 ms

```

I sugest you provide the IP and MAC of each of the hosts (Computers) you are testing with.  I see wlan and eth0 and lo interfaces but it is hard for me to tell which is which.

---

### Post by embedUser on 2011-07-26
Hi Capscrew 
Let me explain the network structure a bit. There are two machines only 
1.My Host Ubuntu system with an IP address on eth0 as 192.168.1.4.
 
Host# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr b8:70:f4:02:a7:4a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe02:a74a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:2100 (2.1 KB)  TX bytes:11655 (11.6 KB)
          Interrupt:41 
The host also has a wlan0 and lo interface for which I had given the details earlier.
2. The second machine is the mini2440, which just has UBOOT 1.3.2 on it. Its IP address is 192.168.1.2
Its MAC address is 08:00:2f:00:00:02
Now these two machines are connected directly and there is no switch/hub or any other machine in between. 
When I did broadcast ping from my Host
Host# ping -b 192.168.1.255
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
^C
--- 192.168.1.255 ping statistics ---
31 packets transmitted, 0 received, 100% packet loss, time 30239ms
 
 
I haven't deleted any data and I couldn't see any traffic moving out of eth0.

when i tried to Ping mini2440 from my host
Host# ping -b 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.1.2 ping statistics ---
 6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5031ms pipe 3

On wireshark I saw ICMP packets with both source and destination set to 192.168.1.4 (Host IP address ) on lo interface. The source and destination MAC for these were set to 0 and the result was Destination Host unreachable.
 
Thanks.

---

### Post by capscrew on 2011-07-26
> **embedUser said:**
> Hi Capscrew 
Let me explain the network structure a bit. There are two machines only 
1.My Host Ubuntu system with an IP address on eth0 as 192.168.1.4.
 
Host# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr b8:70:f4:02:a7:4a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe02:a74a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:2100 (2.1 KB)  TX bytes:11655 (11.6 KB)
          Interrupt:41 
The host also has a wlan0 and lo interface for which I had given the details earlier.

2. The second machine is the mini2440, which just has UBOOT 1.3.2 on it. Its IP address is 192.168.1.2
Its MAC address is 08:00:2f:00:00:02
Now these two machines are connected directly and there is no switch/hub or any other machine in between. 
When I did broadcast ping from my Host
Host# ping -b 192.168.1.255
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
^C
--- 192.168.1.255 ping statistics ---
31 packets transmitted, 0 received, 100% packet loss, time 30239ms
 
 
I haven't deleted any data and I couldn't see any traffic moving out of eth0.

when i tried to Ping mini2440 from my host
Host# ping -b 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.1.2 ping statistics ---
 6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5031ms pipe 3

On wireshark I saw ICMP packets with both source and destination set to 192.168.1.4 (Host IP address ) on lo interface. The source and destination MAC for these were set to 0 and the result was Destination Host unreachable.
 
Thanks.

Well it is not really clear to me what is what.  I can tell you that you CAN NOT communicate between hosts using the lo (loopback) addresses.  The loopback address is always in the 127.0.0.0/8 network.  The first address (localhost) is always 127.0.0.1.

So, If you want my help you will have to be clear and concise with the data for these various machines.  No *"I described that earlier"*.  I don't want to have to go back and forth between the various posts looking for information about *your* problem.   

What I need is the description of both machines interfaces (ALL of them). In addition you should use the "code" button at the top (looks like this **#**) to wrap your output.  The output should look like this```
output goes here
```

---

### Post by embedUser on 2011-07-27
Hi Capscrew 
 
Following is the output of "ifconfig" on my Ubuntu machine.
 
```

eth0      Link encap:Ethernet  HWaddr b8:70:f4:02:a7:4a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14636 (14.6 KB)  TX bytes:14636 (14.6 KB)
 
wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:3d:ae:e6  
          inet addr:192.168.0.189  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe3d:aee6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1435389 (1.4 MB)  TX bytes:476141 (476.1 KB)
 

```
 
My Mini2440 has only one ethernet interface with IP address 192.168.1.2
and MAC address is 08:00:2f:00:00:02
 
On trying broadcast ping from my Ubuntu host
```

Host# ping -b 192.168.1.255
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
^C
--- 192.168.1.255 ping statistics ---
31 packets transmitted, 0 received, 100% packet loss, time 30239ms

```
 
I havent deleted any data and couldnt see any packets going out of eth0.
 
On trying to ping mini2440 from my ubuntu host I get 
```

Host# ping -b 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.1.2 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5031ms pipe 3
 

```
 
I think there is some configuration issue.
 
Thanks.

---

### Post by capscrew on 2011-07-27
> **embedUser said:**
> Hi Capscrew 
 
Following is the output of "ifconfig" on my Ubuntu machine.
 
```

eth0      Link encap:Ethernet  HWaddr b8:70:f4:02:a7:4a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14636 (14.6 KB)  TX bytes:14636 (14.6 KB)
 
wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:3d:ae:e6  
          inet addr:192.168.0.189  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe3d:aee6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1435389 (1.4 MB)  TX bytes:476141 (476.1 KB)
 

```
 
My Mini2440 has only one ethernet interface with IP address 192.168.1.2
and MAC address is 08:00:2f:00:00:02
 
On trying broadcast ping from my Ubuntu host
```

Host# ping -b 192.168.1.255
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
^C
--- 192.168.1.255 ping statistics ---
31 packets transmitted, 0 received, 100% packet loss, time 30239ms

```
 
I havent deleted any data and couldnt see any packets going out of eth0.
 
On trying to ping mini2440 from my ubuntu host I get 
```

Host# ping -b 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.1.2 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5031ms pipe 3
 

```
 
I think there is some configuration issue.
 
Thanks.

As you have 2 interfaces on Ubuntu are up, how do you know that Ubuntu is pinging via eth0 (192.168.1.4)?  If you are pinging via wlan0 (192.168.0.189) then the host indeed is unreachable.

What does wireshark say?  Monitor wlan0.

Edit:  I'll bet that wlan0 is the the default interface.  I would down that interface.  FYI: you can't have 2 interfaces on the same subnet.  FYI2:  Ping -b is for pinging broadcast addresses not individual hosts (i.e. 192.168.1.2).  The correct ping is```
ping 192.168.1.2
``` To limit the amount of pings you can add this ```
ping **[COLOR="Red"]-c4[/COLOR]** 192.168.1.2
```  This limits pings to 4.

---

### Post by embedUser on 2011-07-28
Hi Capscrew
 
> 
As you have 2 interfaces on Ubuntu are up, how do you know that Ubuntu is pinging via eth0 (192.168.1.4)? If you are pinging via wlan0 (192.168.0.189) then the host indeed is unreachable.
 
What does wireshark say? Monitor wlan0.
 
Edit: I'll bet that wlan0 is the the default interface

wlan0 is the interface being used for connecting to Internet. When I monitored it on Wireshark I could only see packets relate to HTTP being received and sent. How can I check if its the default interface? I also tried to bring down wlan0 by
 
```
sudo ifconfig wlan0 down
```
 
After this I tried to initiate a TFTP from mini2440(192.168.1.2) to my Host(192.168.1.4). On wireshark i could see ARP packets being received and replied back from eth0. The MAC addresses were correct.
 
Following is the output of ifconfig after this
 
```

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:02:a7:4a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe02:a74a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:14
          collisions:0 txqueuelen:1000 
          RX bytes:9540 (9.5 KB)  TX bytes:12996 (12.9 KB)
          Interrupt:41 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47269 (47.2 KB)  TX bytes:47269 (47.2 KB)

```
 
 
Then I tried to ping mini2440(192.168.1.2) from my host (192.168.1.4). And did a ifconfig after that. I couldnt see any packets coming out of
eth0 but when I monitored lo, I saw that 4 packets of ICMP with source and destnation both set to 192.168.1.4(Host) were seen. This we can confirm from the number of Rx and Tx packets being the same for eth0, while count of lo increasing by 4. 
 
```

HOST$ ping -c4 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=4 Destination Host Unreachable
 
--- 192.168.1.2 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3014ms
pipe 3
HOST$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:02:a7:4a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe02:a74a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:14
          collisions:0 txqueuelen:1000 
          RX bytes:9540 (9.5 KB)  TX bytes:12996 (12.9 KB)
          Interrupt:41 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47717 (47.7 KB)  TX bytes:47717 (47.7 KB)

```
 
I am not suggesting lo being used for ping, but what i think is that because of some mis or incomplete configuration the network stack is not working properly. Below is the ouput of arp and route command.
 
```

HOST$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
HOST$ arp -a
? (192.168.1.2) at <incomplete> on eth0

```

---

### Post by capscrew on 2011-07-28
> **embedUser said:**
> Hi Capscrew
 
wlan0 is the interface being used for connecting to Internet. When I monitored it on Wireshark I could only see packets relate to HTTP being received and sent. How can I check if its the default interface? I also tried to bring down wlan0 by
 
```
sudo ifconfig wlan0 down
```
 
After this I tried to initiate a TFTP from mini2440(192.168.1.2) to my Host(192.168.1.4). On wireshark i could see ARP packets being received and replied back from eth0. The MAC addresses were correct.

So at this point both hosts can talk -- right?> 
 
...
 
Then I tried to ping mini2440(192.168.1.2) from my host (192.168.1.4). And did a ifconfig after that. I couldnt see any packets coming out of
eth0 but when I monitored lo, I saw that 4 packets of ICMP with source and destnation both set to 192.168.1.4(Host) were seen. This we can confirm from the number of Rx and Tx packets being the same for eth0, while count of lo increasing by 4. 

[QUOTE]
 
```

HOST$ ping -c4 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=4 Destination Host Unreachable
 
--- 192.168.1.2 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3014ms
pipe 3
...
 
I am not suggesting lo being used for ping, but what i think is that because of some mis or incomplete configuration the network stack is not working properly. Below is the ouput of arp and route command.

[/QUOTE]I agree.  The loopback address is not being used.  As for a misconfiguration -- there is no *user* configuration of ARP, nor is there any user configuration of wired Ethernet unless it is the substitution of the MAC address.  You have not indicated that you modified the MAC address on the mini, so I assume you have not.

The ping results indicate that there is no configured address in the subnet, and we know that is wrong.  The ARP data below is interesting...
> 
 
[CODE]
HOST$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
HOST$ arp -a
? (192.168.1.2) at <incomplete> on eth0

```
The arp -a tells the story.  The Linux networking stack doesn't understand the MAC address!  The mini's OS networking is at fault.  What is the OS on the mini? 

The route info is not relevant.  We are only interested in Layer 2 traffic.  Routing is Layer 3 and above.

---

### Post by embedUser on 2011-07-29
Hi Capscrew

> 
So at this point both hosts can talk -- right?


No, though I can see ARP request and replies on Wireshark for my eth0 on Linux Host, but I dont see any packets being received on MINI2440. On Mini2440 I don't have any OS yet, but it has bootlader Uboot-1.3.2 on it. I have enabled debug messages in the U-Boot code and then loaded the modified image on the board. But I don't see any debug prints for packet being received.

> 
 You have not indicated that you modified the MAC address on the mini, so I assume you have not.


Well I have modified the MAC address of Mini2440, but the behavior was same before modifying also.

Thanks

---

