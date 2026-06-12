---
title: "Trouble with Masquerading"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by redxine on 2009-07-09
I'm trying to masquerade an Internet connection using one of my laptops (one running intrepid and the other jaunty) to a dell desktop with jaunty freshly installed. I followed the guide at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) and executed the commands successfully. Here's the laptop's setup:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:57:51:87  
          inet6 addr: fe80::21b:24ff:fe57:5187/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17912 (17.9 KB)  TX bytes:43204 (43.2 KB)
          Interrupt:20 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:a5:df:29:58  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fedf:2958/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19455 errors:0 dropped:0 overruns:0 frame:17770
          TX packets:14911 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26658594 (26.6 MB)  TX bytes:1535389 (1.5 MB)
          Interrupt:19 

``` Where eth0 is the connection that goes to the dell computer with a cross over cable, and eth1 is my wireless connection that supplies internet. So I went to work following the guide:
```
sudo su -
ifconfig eth0 192.168.0.1
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m stsate --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE
echo "1" > /proc/sys/net/ipv4/ip_forward

``` I also edited the /etc/sysctl.conf to read:
```
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.

net.ipv4.conf.defauilt.forwarding=1
net.ipv4.conf.all.forwarding=1

```
I configured the dell machine's networking:
```
sudo /etc/int.d/networking stop
sudo ifconfig eth0 192.168.0.100
sudo route add default gw 192.168.0.1
sudo cp /etc/resolv.conf /etc/resolve.conf.bak
sudo gedit /etc/dhcp3/dhclient.conf
``` and changed the prepend domain-name-servers line to read one of my ISP's DNS servers and 4.2.2.2 as a backup.
then ran ```
sudo /etc/init.d/networking restart
ping 4.2.2.2
  PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
  FROM 192.168.0.1 icmp_seq=1 Destination host unreachable
  ....

```

So I decided to try an use firestarter. I ran the "Restore" script to reset IP tables, and fired up firestarter. I connected the computers, and Enabled internet connection sharing with DHCP. Still no go. The client computer I configured to connect with network manager as DHCP but it never was able to connect. eth0 on the server got 10.42.43.1

Please help!

---

### Post by superprash2003 on 2009-07-09
try doing the ICS without DHCP and insert ip manually in clients.. use firestarter..

---

### Post by redxine on 2009-07-09
I think I've isolated the problem to the connection. I connected the crossover cable to the Jaunty laptop and the Intrepid laptop with network manager set to DHCP on both ends. The Intrepid laptop gets IP 192.168.2.111, Brodcast 255.255.255.255, Subnet Mask 0.0.0.0, and the DNS matches the one for wlan0. On the Jaunty laptop, it's all the same, except it gets IP 192.168.2.112.

but when I ping any of the machines from each other I get:```
PING 192.168.2.111 (192.168.2.111) 56(84) bytes of data.
^C
--- 192.168.2.111 ping statistics ---
11 packets transmitted, 0 received, 100% packet loss, time 10056ms

```

When I try to do the same with the desktop, the laptop says eth0 is connected with the address of 192.168.2.112, but the desktop just keeps requesting an address until it times out. [note that I configured it how the guide said to, I'll try clearing it later].

What is the proper configuration for network manager?

---

### Post by superprash2003 on 2009-07-10
do try with static ip.. and do you have firestarter or gufw or anything installed?? post output of **sudo iptables -L**

---

