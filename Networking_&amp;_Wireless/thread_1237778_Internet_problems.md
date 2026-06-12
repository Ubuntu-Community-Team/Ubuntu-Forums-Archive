---
title: "Internet problems"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by beardo28 on 2009-08-11
Hi, just recently installed ubuntu, internet was working fine, it then asked me to install some updates, did that and restarted the computer and since then the internet does not work. The network manager shows that its connected to the network, but thats about it. its a wired network. can anyone help please?

---

### Post by jonobr on 2009-08-11
Hello And welcome to the forums,

You should list what you have  hardware wise, including your machine, nic if possible, then your connection to the internet, what type of service you have and if there is anything about your home network that may be of interest.

If your just connecting to a broadband router, dialup, wireless etc.
Are you using DHCP or static IP addressing?



Then if you open a terminal window and supply the output of ifconfig, that may help to figure whats going on

---

### Post by beardo28 on 2009-08-11
ok so a bit more info on my setup

laptop with nvidia network card, broadband internet connection through a wired router, using dhcp,

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1b:24:98:93:21  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe98:9321/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2540 (2.5 KB)  TX bytes:5034 (5.0 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by jonobr on 2009-08-12
hello

could you try the following

ping 192.168.1.3

ping 192.168.1.1

nslookup pingplotter.com

nslookup google.com
post the results of the above

then open a browser and type in 

[http://216.92.151.75](http://216.92.151.75)

What do you get???


Are you using pppoe from your ISP?

---

### Post by beardo28 on 2009-08-12
tried them
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=0.077 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=0.023 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=0.020 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=64 time=0.037 ms
64 bytes from 192.168.1.3: icmp_seq=5 ttl=64 time=0.021 ms
64 bytes from 192.168.1.3: icmp_seq=6 ttl=64 time=0.021 ms
64 bytes from 192.168.1.3: icmp_seq=7 ttl=64 time=0.018 ms
64 bytes from 192.168.1.3: icmp_seq=8 ttl=64 time=0.023 ms
64 bytes from 192.168.1.3: icmp_seq=9 ttl=64 time=0.051 ms
64 bytes from 192.168.1.3: icmp_seq=10 ttl=64 time=0.034 ms

--- 192.168.1.3 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8995ms
rtt min/avg/max/mdev = 0.018/0.032/0.077/0.018 ms

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.806 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.696 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.708 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.701 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.693 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.563 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.686 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.698 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.681 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.691 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9001ms
rtt min/avg/max/mdev = 0.563/0.692/0.806/0.058 ms


nslookup pingplotter.com:
Server:        192.168.1.1
Address:    192.168.1.1#53

** server can't find pingplotter.com: SERVFAIL


nslookup google.com:
;; connection timed out; no servers could be reached

I'm pretty sure that i'm using pppoe from my isp.

---

### Post by jonobr on 2009-08-12
Looks like your not getting anything back from your DNS 

what about the ping to 216.92.151.75
and also putting that ip address into your browser

---

### Post by beardo28 on 2009-08-12
PING 216.92.151.75 (216.92.151.75) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
From 192.168.1.1 icmp_seq=3 Destination Net Unreachable
From 192.168.1.1 icmp_seq=4 Destination Net Unreachable
From 192.168.1.1 icmp_seq=5 Destination Net Unreachable
From 192.168.1.1 icmp_seq=6 Destination Net Unreachable
From 192.168.1.1 icmp_seq=7 Destination Net Unreachable
From 192.168.1.1 icmp_seq=8 Destination Net Unreachable
From 192.168.1.1 icmp_seq=9 Destination Net Unreachable
From 192.168.1.1 icmp_seq=10 Destination Net Unreachable

--- 216.92.151.75 ping statistics ---
10 packets transmitted, 0 received, +10 errors, 100% packet loss, time 9000ms

When entering it into a browser it came up failed to connect

---

### Post by jonobr on 2009-08-12
Hello

Just want to check your router is setup correctly?

Can you verify that the router is connected to the internet,

Is the machine you are doing posts here with using the same router?

---

### Post by beardo28 on 2009-08-12
yes it is conected to the internet, i'm using the smae router to post on here.

---

### Post by jonobr on 2009-08-12
Interesting,

Im not a fan of fiddling with MTU size
but see what running this does

```
 sudo ifconfig eth0 mtu 1450
```

If that doesnt work we can always change MTU back to 1500

---

### Post by beardo28 on 2009-08-12
still not working

---

### Post by jonobr on 2009-08-12
WHats you assigned IP address of your broadband router?

Is there a web screen that shows you what that is 
Does it have admin screens to show you the assigned DNS IP and public IP address?

---

### Post by jonobr on 2009-08-12
I would also recommend that you reset MTU to 1500
you check the MTU size in use on your working machine.
and that you post the results of 

cat /etc/resolv.conf
and
cat /etc/nsswitch.conf

---

### Post by beardo28 on 2009-08-12
ok, router does have amin screen:

router ip, not 100% on this one is likely to be this one 212.248.157.74 or 192.168.2.1, and with regards to public ip i'm guessing it will be one of those as well.
DNS: 195.8.160.64

---

### Post by beardo28 on 2009-08-12
results of those files:

# Generated by NetworkManager
nameserver 192.168.1.1



# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by jonobr on 2009-08-12
ok so can you ping 212.248.157.74

also what does the 192.168.2.1 ip address refer to?

That sounds odd

---

### Post by beardo28 on 2009-08-13
ok so tried pinging that and failed. the 212 ip address, having a had another look at the setup of the network is for the modem, and the 192 ip address is for the router, don't know if this makes any difference. i did manage to get internet working last night by going straight to the modem, and entering the settings manually, but this only works if i go straight to the modem and isn't a long term solution.

---

### Post by jonobr on 2009-08-13
Hello


What do you mean by "straight to the modem?

The 192.168.2 address is probably the problem as the 192.168.1.3 cannot route to 192.168.2.1 IP address.

Understanding your network setup is important.

---

