---
title: "Strange networking DNS/firewall problem."
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by gtaskeraus on 2012-01-23
I've been trying to get at a particular website and cannot.  It won't ping or anything.  Every other website is fine.

If I use someone elses computer on the same network it finds it so the problem seems to be definitely with my own computer.

I've tried turning off the firewall and yet I still can't get through.

How can I go about diagnosing the problem from this point?

---

### Post by poolet on 2012-01-23
download  the wireshark and capure the network is the only way to see what exactly block out u... But it seems that your problems has to do with authentication... check and confirm the dns server of each pc(name server etc..) ... Also did you try to clen the dns catches?? At the end did you used cisco or linksys router?? if yes  open up the console of the router and give it " no shutdown "  at each interface that isn't works...

---

### Post by matt_symes on 2012-01-23
Hi

You have flushed your iptables rules and then tried to ping ?

```
sudo iptables -F
```

```
ping -c4 <ipaddress>
```

You have tried an external nameserver
```

nslookup <domain or ip address> 8.8.8.8
```

8.8.8.8 is a google name server. You can also use 8.8.4.4 and others.

Do you have any proxy or nanny software.

Wireshark is a very good idea as stated above. You can also use tcpdump and traceroute to see what is happening to the packets.

Kind regards

---

### Post by gtaskeraus on 2012-01-23
This is getting real weird.  
nslookup finds it.

supernova:/home/george# nslookup files.rightlytrained.org
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
files.rightlytrained.org	canonical name = [http://c835106.r6.cf2.rackcdn.com](http://c835106.r6.cf2.rackcdn.com).
[http://c835106.r6.cf2.rackcdn.com](http://c835106.r6.cf2.rackcdn.com)	canonical name = a6.rackcdn.com.
a6.rackcdn.com	canonical name = a6.rackcdn.com.mdc.edgesuite.net.
a6.rackcdn.com.mdc.edgesuite.net	canonical name = a8.cf.akamai.net.
Name:	a8.cf.akamai.net
Address: 202.7.177.42
Name:	a8.cf.akamai.net
Address: 202.7.177.18

=======================================

ping
@supernova:/home/george# ping files.rightlytrained.org
ping: unknown host files.rightlytrained.org

browser won't find it either.
However the alternative offered by nslookup (a6.rackcdn.com.a6.rackcdn.com) gets me where I want to go.  This has me really scratching my head.

It proves that the DNS on the home router - a netgear - is functioning.  My ISP confirmed that their effort to contact the site is ok.  And it looks as if it is only my computer out of the five sitting around here at my place.

Wireshark here I come.

---

### Post by matt_symes on 2012-01-23
Hi

FYI:
```

matthew@matthew-Aspire-7540:~$ ping files.rightlytrained.org
ping: unknown host files.rightlytrained.org
matthew@matthew-Aspire-7540:~$
``````

matthew@matthew-Aspire-7540:~$ nslookup files.rightlytrained.org
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
files.rightlytrained.org        canonical name = http://c835106.r6.cf2.rackcdn.com.
http://c835106.r6.cf2.rackcdn.com       canonical name = a6.rackcdn.com.
a6.rackcdn.com  canonical name = a6.rackcdn.com.mdc.edgesuite.net.
a6.rackcdn.com.mdc.edgesuite.net        canonical name = a8.cf.akamai.net.
Name:   a8.cf.akamai.net
Address: 88.221.88.18
Name:   a8.cf.akamai.net
Address: 88.221.88.19

matthew@matthew-Aspire-7540:~$ 
``````
matthew@matthew-Aspire-7540:~$ ping -c3 88.221.88.19
PING 88.221.88.19 (88.221.88.19) 56(84) bytes of data.
64 bytes from 88.221.88.19: icmp_req=2 ttl=54 time=16.3 ms
64 bytes from 88.221.88.19: icmp_req=3 ttl=54 time=14.2 ms

--- 88.221.88.19 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2001ms
rtt min/avg/max/mdev = 14.238/15.300/16.363/1.069 ms
matthew@matthew-Aspire-7540:~$ 
``````
matthew@matthew-Aspire-7540:~$ nslookup files.rightlytrained.org 8.8.8.8
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
files.rightlytrained.org        canonical name = http://c835106.r6.cf2.rackcdn.com.
http://c835106.r6.cf2.rackcdn.com       canonical name = a6.rackcdn.com.
a6.rackcdn.com  canonical name = a6.rackcdn.com.mdc.edgesuite.net.
a6.rackcdn.com.mdc.edgesuite.net        canonical name = a8.cf.akamai.net.
Name:   a8.cf.akamai.net
Address: 92.122.50.136
Name:   a8.cf.akamai.net
Address: 92.122.50.144

matthew@matthew-Aspire-7540:~$ 
``````

matthew@matthew-Aspire-7540:~$ matthew@matthew-Aspire-7540:~$ ping -c3 92.122.50.136
PING 92.122.50.136 (92.122.50.136) 56(84) bytes of data.
64 bytes from 92.122.50.136: icmp_req=2 ttl=49 time=34.1 ms
64 bytes from 92.122.50.136: icmp_req=3 ttl=49 time=32.6 ms

--- 92.122.50.136 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2000ms
rtt min/avg/max/mdev = 32.677/33.419/34.162/0.764 ms
matthew@matthew-Aspire-7540:~$ 
```Are you getting behaviour like this ?

Kind regards

---

### Post by matt_symes on 2012-01-23
Hi

Can we have a look at your file

```
cat /etc/resolv.conf
```

Post it back here.

Kind regards

---

### Post by gtaskeraus on 2012-01-23
Here it is.  I'm about to go to bed so it will be a few hours before I respond.

No hurry.  The problem will still be there tomorrow I'm confident of that.

```
supernova:/home/george# cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1
nameserver 10.0.0.1

```

The first nameserver is the DSL router/modem.  The second nameserver is the wireless router for all the laptops etc.

The prior post asked about nslookup and ping one after the other twice.  The nslookup looks about the same, the ping keeps coming back with "unknown host".

I'll look at wireshark tomorrow after a good sleep.

---

### Post by matt_symes on 2012-01-23
Hi

What do you see if you put the IP address and not the domain name into a browser ?

I am seeing an error message saying "invalid url" returned as an html page.

What exactly is on this server ?

Are the other machines running Ubuntu ?

Kind regards

---

### Post by gtaskeraus on 2012-01-24
Here is some output from wireshark which shows that when I point DNS at 8.8.8.8 that I get a valid response.  

```
No.     Time        Source                Destination           Protocol Info
    202 2.921877    192.168.0.3           8.8.8.8               DNS      Standard query A files.rightlytrained.org

Frame 202: 84 bytes on wire (672 bits), 84 bytes captured (672 bits)
    Arrival Time: Jan 25, 2012 00:46:47.561533000 EST
    Epoch Time: 1327412807.561533000 seconds
    [Time delta from previous captured frame: 0.015599000 seconds]
    [Time delta from previous displayed frame: 0.000000000 seconds]
    [Time since reference or first frame: 2.921877000 seconds]
    Frame Number: 202
    Frame Length: 84 bytes (672 bits)
    Capture Length: 84 bytes (672 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Giga-Byt_41:f7:6f (00:1d:7d:41:f7:6f), Dst: Netgear_1c:93:7c (00:1e:2a:1c:93:7c)
    Destination: Netgear_1c:93:7c (00:1e:2a:1c:93:7c)
        Address: Netgear_1c:93:7c (00:1e:2a:1c:93:7c)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Giga-Byt_41:f7:6f (00:1d:7d:41:f7:6f)
        Address: Giga-Byt_41:f7:6f (00:1d:7d:41:f7:6f)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.0.3 (192.168.0.3), Dst: 8.8.8.8 (8.8.8.8)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x08 (DSCP 0x02: Unknown DSCP; ECN: 0x00)
    Total Length: 70
    Identification: 0xe50f (58639)
    Flags: 0x02 (Don't Fragment)
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (17)
    Header checksum: 0x84d4 [correct]
    Source: 192.168.0.3 (192.168.0.3)
    Destination: 8.8.8.8 (8.8.8.8)
User Datagram Protocol, Src Port: 35725 (35725), Dst Port: domain (53)
    Source port: 35725 (35725)
    Destination port: domain (53)
    Length: 50
    Checksum: 0x8372 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (query)
    [Response In: 203]
    Transaction ID: 0x7ed2
    Flags: 0x0100 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data: Unacceptable
    Questions: 1
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        files.rightlytrained.org: type A, class IN
            Name: files.rightlytrained.org
            Type: A (Host address)
            Class: IN (0x0001)

No.     Time        Source                Destination           Protocol Info
    203 2.949229    8.8.8.8               192.168.0.3           DNS      Standard query response CNAME http://c835106.r6.cf2.rackcdn.com CNAME a6.rackcdn.com CNAME a6.rackcdn.com.mdc.edgesuite.net CNAME a8.cf.akamai.net A 120.29.145.10 A 120.29.145.19

Frame 203: 253 bytes on wire (2024 bits), 253 bytes captured (2024 bits)
    Arrival Time: Jan 25, 2012 00:46:47.588885000 EST
    Epoch Time: 1327412807.588885000 seconds
    [Time delta from previous captured frame: 0.027352000 seconds]
    [Time delta from previous displayed frame: 0.027352000 seconds]
    [Time since reference or first frame: 2.949229000 seconds]
    Frame Number: 203
    Frame Length: 253 bytes (2024 bits)
    Capture Length: 253 bytes (2024 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ip:udp:dns]
    [Coloring Rule Name: UDP]
    [Coloring Rule String: udp]
Ethernet II, Src: Netgear_1c:93:7c (00:1e:2a:1c:93:7c), Dst: Giga-Byt_41:f7:6f (00:1d:7d:41:f7:6f)
    Destination: Giga-Byt_41:f7:6f (00:1d:7d:41:f7:6f)
        Address: Giga-Byt_41:f7:6f (00:1d:7d:41:f7:6f)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Netgear_1c:93:7c (00:1e:2a:1c:93:7c)
        Address: Netgear_1c:93:7c (00:1e:2a:1c:93:7c)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 8.8.8.8 (8.8.8.8), Dst: 192.168.0.3 (192.168.0.3)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
    Total Length: 239
    Identification: 0x0000 (0)
    Flags: 0x02 (Don't Fragment)
    Fragment offset: 0
    Time to live: 58
    Protocol: UDP (17)
    Header checksum: 0x6f43 [correct]
    Source: 8.8.8.8 (8.8.8.8)
    Destination: 192.168.0.3 (192.168.0.3)
User Datagram Protocol, Src Port: domain (53), Dst Port: 35725 (35725)
    Source port: domain (53)
    Destination port: 35725 (35725)
    Length: 219
    Checksum: 0xf9f4 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 202]
    [Time: 0.027352000 seconds]
    Transaction ID: 0x7ed2
    Flags: 0x8180 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .0.. .... .... = Authoritative: Server is not an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... 1... .... = Recursion available: Server can do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... ...0 .... = Non-authenticated data: Unacceptable
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 1
    Answer RRs: 6
    Authority RRs: 0
    Additional RRs: 0
    Queries
        files.rightlytrained.org: type A, class IN
            Name: files.rightlytrained.org
            Type: A (Host address)
            Class: IN (0x0001)
    Answers
        files.rightlytrained.org: type CNAME, class IN, cname http://c835106.r6.cf2.rackcdn.com
            Name: files.rightlytrained.org
            Type: CNAME (Canonical name for an alias)
            Class: IN (0x0001)
            Time to live: 7 minutes, 49 seconds
            Data length: 35
            Primary name: http://c835106.r6.cf2.rackcdn.com
        http://c835106.r6.cf2.rackcdn.com: type CNAME, class IN, cname a6.rackcdn.com
            Name: http://c835106.r6.cf2.rackcdn.com
            Type: CNAME (Canonical name for an alias)
            Class: IN (0x0001)
            Time to live: 4 minutes, 42 seconds
            Data length: 5
            Primary name: a6.rackcdn.com
        a6.rackcdn.com: type CNAME, class IN, cname a6.rackcdn.com.mdc.edgesuite.net
            Name: a6.rackcdn.com
            Type: CNAME (Canonical name for an alias)
            Class: IN (0x0001)
            Time to live: 4 minutes, 42 seconds
            Data length: 34
            Primary name: a6.rackcdn.com.mdc.edgesuite.net
        a6.rackcdn.com.mdc.edgesuite.net: type CNAME, class IN, cname a8.cf.akamai.net
            Name: a6.rackcdn.com.mdc.edgesuite.net
            Type: CNAME (Canonical name for an alias)
            Class: IN (0x0001)
            Time to live: 4 minutes, 42 seconds
            Data length: 15
            Primary name: a8.cf.akamai.net
        a8.cf.akamai.net: type A, class IN, addr 120.29.145.10
            Name: a8.cf.akamai.net
            Type: A (Host address)
            Class: IN (0x0001)
            Time to live: 2 seconds
            Data length: 4
            Addr: 120.29.145.10 (120.29.145.10)
        a8.cf.akamai.net: type A, class IN, addr 120.29.145.19
            Name: a8.cf.akamai.net
            Type: A (Host address)
            Class: IN (0x0001)
            Time to live: 2 seconds
            Data length: 4
            Addr: 120.29.145.19 (120.29.145.19)

```

My problem now is that my browser is still reporting an error.  I tried firefox and also chromium just to be sure it was not browser specific.

The link I'm chasing is [http://files.rightlytrained.org/vid/1102/ayc11/27_randy_skeete_weak_heart_weak_hand-HD.mp4]("http://files.rightlytrained.org/vid/1102/ayc11/27_randy_skeete_weak_heart_weak_hand-HD.mp4") which is a rather large video download if I can get that far.

I got in by going via [http://www.rightlytrained.org/watchvideo.aspx?videoid=154&quality=hd#]("http://www.rightlytrained.org/watchvideo.aspx?videoid=154&quality=hd#") which is fine so far as links go until I hit the link above.

---

### Post by matt_symes on 2012-01-24
Hi

I'm getting exactly the same error as you. I will look into it.

Kind regards

---

### Post by gtaskeraus on 2012-01-24
Good to see someone else can replicate the problem.  I'll be interested in your findings.

---

