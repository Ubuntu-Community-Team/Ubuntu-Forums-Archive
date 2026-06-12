---
title: "Connect two Linux machines via ethernet"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by daniel488 on 2012-08-17
Hi,

I have problem with connection between two devices, my notebook with Ubuntu 11.04 and Beagleboard with Angstrom Linux distro.

Connected via crossover cable. I made:
On notebook:
```
ifconfig eth0 192.168.4.2 up
```
On Beagleboard:
```
ifconfig usb0 192.168.4.1 up
```

On both I can ping to that addresses, and I see on notebook eth0 and on beagle usb0 ethernet cards when I use ifconfig. 
But can't ping each other. On notebook I see messages like:
```
From 192.168.4.2 icmp_seq=1 Destination Host Unreachable

```

What thing I forgot to do? Or what can block ICMP?

---

### Post by bakegoodz on 2012-08-18
Are you sure your cable is correctly wired and crimped?
My next trouble shooting step would be to get a third device and test it one at a time with the first 2 devices.

---

### Post by dandnsmith on 2012-08-19
First step, surely, is to look at the config after doing the 'up' using ifconfig, and then look at the routing with 'route print' - you'll probably find that there is no gateway or possible route defined.

If in doubt, post results of the commands for us to analyse.

---

### Post by Iowan on 2012-08-19
My machine (11.04) doesn't like **route print**, but just **route** or **route -n** works.

---

### Post by bakegoodz on 2012-08-19
A gateway/router, or DNS is not needed just connecting 2 devices by IP address. I've done this several times when configuring routers.

---

### Post by dandnsmith on 2012-08-20
I agree that no additional hardware is needed - in fact the only special requirement, in terms of hardware, is that you either use a X-over patch cable, or at least one end has an auto-sensing port.

However, if you issue a command to communicate, then you need at least some primitive routing to get the output sent outside the computer, and this should show up in the output of the ifconfig and route commands.

My apologies for giving the Windows form of the route command - the print bit only causes confusion.

---

### Post by daniel488 on 2012-08-31
Finally I have connection to that device but there is Ubuntu 12.04 now.
And here is another complication. On my notebook I have wireless connection to the Internet and when I attach ethernet cable to that device I lose my connection to world. I'd like provide Internet to that device and of course have on my notebook. Is it possible?

EDIT:
I see what I need, bridge. I installed NetBridge. It is GUI for bridge-utils. But it doesn't work for my wlan0 interface: can't add wlan0 to bridge br0: Operation not supported. 
It is known problem and people use hostapd tool to deal with it. But it is too much for me. Could you help? My wireless card: BCM43225 802.11b/g/n.

---

### Post by SeijiSensei on 2012-08-31
Bridging is almost never the right solution.

So I take it that the laptop is one of the wired devices and there is another wired device as well?  And the laptop also runs wifi to the Internet via a router?

I know it's possible to have both adapters active on the laptop, but I can't remember how I did it.  A little digging in the documentation should provide the answer.

Make sure that the addresses on the wired side are in a different subnet from the wifi side.  If the wifi adapter gets an address in 192.168.1.0/24, use 192.168.2.0/24 for the wired devices.

Next, edit (as root with sudo) the file /etc/sysctl.conf on the laptop and remove the hash mark from the line  "net.ipv4.ip_forward=1".  That will enable the machine to forward packets between the interfaces.  You'll need to reboot to make this take effect.

On the laptop, make sure there is only one "default gateway" and that it points to your router.  On the other box, make the laptop be its default gateway.

Finally, on the laptop, run the command:

```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

That will tell the laptop to "masquerade" traffic from the box behind it so that box can connect to the Internet.  If all that works properly, put the command into the file /etc/rc.local (again using sudo) so it will run at boot.

If you're having problems, please post the results of the commands:

ifconfig
route -n
iptables -L -nv

We'll see if we can help.

---

### Post by daniel488 on 2012-09-01
Thanks for answer.
Unfortunatelly it doesn't work now so I count on more of your help.

Laptop side commands results:

```
daniel@123:~$ sudo iptables -L -nv
Chain INPUT (policy ACCEPT 846 packets, 367K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 907 packets, 70989 bytes)
 pkts bytes target     prot opt in     out     source               destination
```

```
daniel@123:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```


```
daniel@123:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 60:eb:69:b4:e1:36  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:feb4:e136/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:13514 (13.5 KB)  TX bytes:16203 (16.2 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8540 (8.5 KB)  TX bytes:8540 (8.5 KB)

wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:6e:5d:2a  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8a9f:faff:fe6e:5d2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:22209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16409601 (16.4 MB)  TX bytes:2863687 (2.8 MB)

```


External Board with Ubuntu:

There is no iptables command.

```
ubuntu@omap:~$ route -n                                                         
Kernel IP routing table                                                         
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface   
0.0.0.0         192.168.0.2     0.0.0.0         UG    0      0        0 eth0    
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
```

```
ubuntu@omap:~$ ifconfig                                                         
eth0      Link encap:Ethernet  HWaddr 00:60:6e:00:03:3a                         
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0        
          inet6 addr: fe80::260:6eff:fe00:33a/64 Scope:Link                     
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                    
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0                  
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0                
          collisions:0 txqueuelen:1000                                          
          RX bytes:17161 (17.1 KB)  TX bytes:14314 (14.3 KB)                    
                                                                                
lo        Link encap:Local Loopback                                             
          inet addr:127.0.0.1  Mask:255.0.0.0                                   
          inet6 addr: ::1/128 Scope:Host                                        
          UP LOOPBACK RUNNING  MTU:16436  Metric:1                              
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                    
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                  
          collisions:0 txqueuelen:0                                             
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```

---

### Post by SeijiSensei on 2012-09-02
> **daniel488 said:**
> Thanks for answer.
Unfortunatelly it doesn't work now so I count on more of your help.

Which part doesn't work?  

First, can you ping the router at 192.168.1.1 from the board at 192.168.0.3?  If not, did you activate IP forwarding in /etc/sysctl.conf?  As a test run 

```
cat /proc/sys/net/ipv4/ip_forward
```

If it returns zero, you haven't enable IP forwarding.  One quick test is to run 

```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

and try to ping 192.168.1.1 from 192.168.0.3.  If that works, then fix the entry in /etc/sysctl.conf and reboot.

If you still cannot ping the router, are you sure you added the masquerading rule with iptables?  Sorry I forgot to give you right iptables command to list the rules.  The nat table entries for iptables are not listed by default with "iptables -L".  What do you see when you use 

```
sudo iptables -t nat -L -nv
```

Is there a POSTROUTING masquerading rule like the one I posted before?  If you followed my code exactly, it won't work in your case because the interface facing the router is wlan0.  So use

```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

It obviously won't survive a reboot.  The simplest solution is to put the command (without the initial "sudo") in /etc/rc.local which is the last script run during boot up.

---

### Post by daniel488 on 2012-09-03
I will try again and do all these tests in 10 hours, after work.

---

### Post by daniel488 on 2012-09-04
> **SeijiSensei said:**
> Which part doesn't work?  

First, can you ping the router at 192.168.1.1 from the board at 192.168.0.3?  If not, did you activate IP forwarding in /etc/sysctl.conf?  As a test run 

```
cat /proc/sys/net/ipv4/ip_forward
```

If it returns zero, you haven't enable IP forwarding.  One quick test is to run 

```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

and try to ping 192.168.1.1 from 192.168.0.3.  If that works, then fix the entry in /etc/sysctl.conf and reboot.

I edited /etc/sysctl.conf. First command return 1. But I can't ping from 192.168.0.3 to 192.168.1.1:
```
ubuntu@omap:~$ ping 192.168.1.1                                                 
connect: Network is unreachable 
```

> **SeijiSensei said:**
> 
If you still cannot ping the router, are you sure you added the masquerading rule with iptables?  Sorry I forgot to give you right iptables command to list the rules.  The nat table entries for iptables are not listed by default with "iptables -L".  What do you see when you use 

```
sudo iptables -t nat -L -nv
```

Is there a POSTROUTING masquerading rule like the one I posted before?  If you followed my code exactly, it won't work in your case because the interface facing the router is wlan0.  So use

```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

It obviously won't survive a reboot.  The simplest solution is to put the command (without the initial "sudo") in /etc/rc.local which is the last script run during boot up.

I followed your code so there was mistake. I changed it to wlan0 and the result is:
```
daniel@123:~$ sudo iptables -t nat -L -nv
Chain PREROUTING (policy ACCEPT 399 packets, 127K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 17 packets, 9587 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1572 packets, 98408 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 9 packets, 1459 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1563 96949 MASQUERADE  all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0 
```

Still can only ping between 192.168.0.2 and 192.168.0.3.


EDIT:
I turned on wireshark on eth0 on laptop side. I see incoming/outcoming ICMP packets when I send ping from 192.168.0.3 to 192.168.0.2. Even sending to other addresses in 192.168.0.0/24 subnet, I can see on laptop side broadcast packets from 192.168.0.3.

But when I change subnet e.g. pinging 192.168.1.1 or any other outside 192.168.0.0/24, nothing reaches eth0 interface on laptop. 
So it must be something in that external board system in my opinion. There is:
```
ubuntu@omap:~$ route -n                                                         
Kernel IP routing table                                                         
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface   
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
```
Shouldn't I add something?

EDIT2:
I added default route on that board with (who knows why it disappeard :P)
```
sudo route add default gw 192.168.0.2
```
and it works!

@SeijiSensei thnak you very much. I don't see any kudos/points on this forum so just know that I really appreciate your help.

---

