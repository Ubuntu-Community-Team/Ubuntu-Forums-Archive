---
title: "how to print network IPs"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by rashwan on 2009-10-02
[SIZE="3"]Hello ,

how can i view my network IP _addresses_ from Command Line , 
rather than view them from router's page ?!


Thanks[/SIZE]

---

### Post by rashwan on 2009-10-02
anyone ?

---

### Post by Iowan on 2009-10-02
Current machine's IP address - or addresses of all machines on network?
(**ifconfig** will show machine's IP address).

---

### Post by rashwan on 2009-10-02
Yeah all machines on network (if possible)

---

### Post by jonobr on 2009-10-02
THeres a few ways to do that, although it doesnt beat having all this information already noted,

You could nmap the network and find all active hosts, or more simply without having to learn nmap, you could try opening two terminal windows.


on one run the network sniffer tcpdump using the following options which filters icmp (ping ) replies only

```
sudo tcpdump -i eth0 'icmp[icmptype] = icmp-echo'
```

This assumes your ethernet interface is eth0

On the second window, issue a broadcast ping to all hosts on the network.
i.e. if your in a class C network, and using a 192.168.1.X addressing scheme you would ping 192.168.1.255 with the -b option


Devices should respond with their ip addresses and it should show up in the other screen.

This also generates a bit of network traffic and if being used for nefarious reasons, it could be spotted by a diligent network admin or a device like an intrusion detection system.

I should also note  Some devices could be configred not to respond to ICMP requests,

---

### Post by rashwan on 2009-10-02
well it prints only one client of the network , heres the output:

```
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=3.96 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=4.54 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=4.11 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=64 time=4.97 ms
64 bytes from 192.168.1.3: icmp_seq=5 ttl=64 time=4.72 ms
64 bytes from 192.168.1.3: icmp_seq=6 ttl=64 time=4.09 ms
64 bytes from 192.168.1.3: icmp_seq=7 ttl=64 time=5.36 ms
64 bytes from 192.168.1.3: icmp_seq=8 ttl=64 time=5.77 ms
64 bytes from 192.168.1.3: icmp_seq=9 ttl=64 time=13.0 ms
64 bytes from 192.168.1.3: icmp_seq=10 ttl=64 time=3.59 ms
64 bytes from 192.168.1.3: icmp_seq=11 ttl=64 time=4.06 ms
64 bytes from 192.168.1.3: icmp_seq=12 ttl=64 time=3.56 ms
64 bytes from 192.168.1.3: icmp_seq=13 ttl=64 time=4.95 ms
64 bytes from 192.168.1.3: icmp_seq=14 ttl=64 time=3.55 ms
64 bytes from 192.168.1.3: icmp_seq=15 ttl=64 time=3.78 ms
64 bytes from 192.168.1.3: icmp_seq=16 ttl=64 time=4.37 ms
64 bytes from 192.168.1.3: icmp_seq=17 ttl=64 time=6.00 ms
64 bytes from 192.168.1.3: icmp_seq=18 ttl=64 time=3.45 ms
64 bytes from 192.168.1.3: icmp_seq=19 ttl=64 time=3.44 ms
64 bytes from 192.168.1.3: icmp_seq=20 ttl=64 time=4.36 ms
64 bytes from 192.168.1.3: icmp_seq=21 ttl=64 time=7.87 ms
64 bytes from 192.168.1.3: icmp_seq=22 ttl=64 time=5.26 ms
64 bytes from 192.168.1.3: icmp_seq=23 ttl=64 time=19.0 ms
64 bytes from 192.168.1.3: icmp_seq=24 ttl=64 time=3.41 ms
64 bytes from 192.168.1.3: icmp_seq=25 ttl=64 time=4.15 ms
64 bytes from 192.168.1.3: icmp_seq=26 ttl=64 time=5.52 ms

```

and so on...

---

### Post by amauk on 2009-10-02
install nmap
```
sudo apt-get install nmap
```

then ping your subnet
Eg.
```
nmap -sP 192.168.1.0/24
```
will ping machines 192.168.1.1 - 192.168.1.254

```
nmap -sP 192.168.0.0/16
```
will ping machines 192.168.0.1 - 192.168.255.254

The ping scan is only one of many scans nmap can do
there's all sorts of things possible, including OS detection and port scans
See nmap's man page for (a lot) more info

---

### Post by rashwan on 2009-10-02
cool , but it shows only 3 of 4 addresses up! 
```
rashwan@rashwan-desktop:~$ nmap -sP 192.168.1.0/24

Starting Nmap 4.76 ( http://nmap.org ) at 2009-10-03 01:09 EET
Illegal character(s) in hostname -- replacing with '*'
Host *arpa (192.168.1.1) appears to be up.
Host 192.168.1.2 appears to be up.
Host 192.168.1.3 appears to be up.
Nmap done: 256 IP addresses (3 hosts up) scanned in 5.11 seconds

```

while i successfully ping the missed one:

```
desktop:~$ ping 192.168.1.7
PING 192.168.1.7 (192.168.1.7) 56(84) bytes of data.
64 bytes from 192.168.1.7: icmp_seq=1 ttl=128 time=13.1 ms
64 bytes from 192.168.1.7: icmp_seq=2 ttl=128 time=2.38 ms
64 bytes from 192.168.1.7: icmp_seq=3 ttl=128 time=4.69 ms
64 bytes from 192.168.1.7: icmp_seq=4 ttl=128 time=2.54 ms
--- 192.168.1.7 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 2.382/5.696/13.161/4.405 ms
```

am i missing something ?

---

