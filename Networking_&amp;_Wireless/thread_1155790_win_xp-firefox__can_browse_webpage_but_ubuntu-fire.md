---
title: "win xp-firefox  can browse webpage but ubuntu-firefox can not browse webpage"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by abu salma on 2009-05-11
Hallo for all af ubuntu masters,

Please help me, i have a problem that  i can not solve it, until now.
here is my problem.

My ubuntu box, i use ubuntu 8.10. in a few days can not browse web pages. but i can ping normally, i can ping use name of site i.e. [www.google.com](www.google.com), so iam sure that my dns is true.

I am sure my cable connected normally, cause i can use browse web page if i use firefox with win xp in same pc and same connection. 

I try to solve this problem by browse in this forum and some site, i try to disable my ipv6, my firewall, i try to edit my /etc/resolv.conf, but until now i can get solution. and my ubuntu cannot open web page.

I cannot use apt-get, i cannot use wget. so my ubuntu cannot  improved.

Please help me, i am confusing.:confused:

Sory if my english not perfect.

---

### Post by pro003 on 2009-05-11
I suppose your internet connection is down (in ubuntu). 

did you try to ping from terminal?

---

### Post by LequidMetal on 2009-05-11
If firefox refuses to connect to the internet then its possible that it may be working in offline mode

check if File>Work Offline Mode is checked (does it have a tick mark near it?) ..... if it is checked , uncheck it by clicking on it once . 

If not then you have to check whether your internet connection is disabled in ubuntu

Are you trying to connect to the internet from Ubuntu for the first time ?

---

### Post by bigboy_pdb on 2009-05-11
Ping uses the ICMP protocol and the other programs that you mentioned use TCP/IP ([which are different internet protocols]("http://en.wikipedia.org/wiki/Internet_Protocol_Suite")).

It's possible that TCP transmissions are being blocked but not other transmissions. If you have a router then you should check the settings. If you're using a switch then the ISP may be blocking one of your computers (provided that the switch doesn't support [NAT]("http://en.wikipedia.org/wiki/Network_address_translation")).

You can check if the ISP is blocking the other machine by only connecting the Linux machine to the internet and resetting the modem/router that the ISP gave you. You could also try [masquerading as the other computer]("http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html") (when only the Linux machine is connected) by using its MAC address if you cannot get a connection, but that shouldn't be necessary.

It's also possible that your local firewall (iptables) is blocking traffic.

---

### Post by superprash2003 on 2009-05-11
try opening [http://209.85.171.100](http://209.85.171.100)

---

### Post by abu salma on 2009-05-11
I was very appreciate for all of respon with my thread.:)

1. i try ping from terminal and success, i can receive packet. even from internet, 
2. my firefox is online mode.
3. no it's not my fist time i run ubuntu, before my internet connection is running well, but sudden my internet is down until now, so i must use win for write this thread. i dont know what happen. I try to use my ubuntu flash but i cannot connect to internet, itry to install again my ubntu but this treat can not solve the problem.
4. my network conn is enabled, 
5. if tcp is blocked, why i can access internet use win-firefox?
6. if my router blocked my ip, why if i try use another ip but my problem is not solved, even if i use ip that enable and can run win-firefox as well as.
7. i have try to disable my ufw (firewall) to but no connection to.
8. This morning i open my ubuntu and i wonder i can get internet connection, but just for minutes, and the connection was down, I don know what happen. if my router
block my ubuntu why this occur? Can some pc block my ubuntu machine to resolve to internet? 
9. can my router admin block linux machine only and bypass win machine?:confused:

10. if i trace path i get that my local-router is  trace  twice but  it  not happen in win.  if i tracert  my local router  was trace  just one times, no more. but both machine  can trace until the destination machine.

11. again if i try scan my network my ubuntu status is "Not Logged in" but my win is "looged in" but both can ping each other.

So what the solution, again tank's for attention.

---

### Post by bigboy_pdb on 2009-05-12
Sorry, when I mentioned checking the router, I meant in general to see that there's nothing enabled that might interfere (so MAC filters and anything unnecessary should be turned off for now). You can try resetting the router, but I think the problem is with your Ubuntu setup.

It would probably be a good idea to boot from the live CD to check that it can connect. If it can then it's your installation that has the problem.

In the event that the live CD works, you can also compare the settings for your installation with the live CD settings. Some files that you'd want to check are:
/etc/network/interfaces
/etc/resolv.conf

You might also want to output the results of commands to files for comparison as well (ie. "ifconfig >& ifconfig_out").

Another option is to dump your IP tables and compare them using the command "sudo iptables -L" (use "man iptables" to view the man page). You can also save the IP tables for the live cd and restore them over the installation's IP tables (but you should back them up first). This can be done using the commands iptables-save and iptables-restore.

---

### Post by matthewboh on 2009-05-12
I'm having the exact same problem - can get to the Internet but not on my one machine that has a dual XP / Ubuntu 9.04 installation.

So far, I've followed the suggestions here, but running into the same problems.

I can get to the same sites running another instance of 9.04 on another machine (not dual boot though).

Another strange bit - I can get to [https://www.google.com/ig?hl=en](https://www.google.com/ig?hl=en) but not to [http://www.google.com/ig?hl=en](http://www.google.com/ig?hl=en) (the https is the difference)

---

### Post by abu salma on 2009-05-13
for [matthewboh]("http://ubuntuforums.org/member.php?u=163897") :
tank for suggestion to googling, but until now i can get some usefull for my problem, would  you give the dirrect link, if you get answer from google.

for [bigboy_pdb]("http://ubuntuforums.org/member.php?u=305128"):
tank for your respon before all.
today i try to use ubuntu live-cd that before can get internet web page normally, but the problem does not corrected.:(

there is my data that may be you want to know about my ubuntu configuration:

**_my /etc/network/interfaces_**
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.45.222
netmask 255.255.255.0
gateway 192.168.45.254

auto eth0


_**my /etc/resolv.conf**_
nameserver 222.124.162.129
nameserver 222.124.162.132

ubuntu@ubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

ubuntu@ubuntu:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.19.104) 56(84) bytes of data.
64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=1 ttl=237 time=731 ms
64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=2 ttl=237 time=790 ms
64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=3 ttl=237 time=805 ms
64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=4 ttl=237 time=769 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 3998ms
rtt min/avg/max/mdev = 731.312/774.364/805.961/27.982 ms


ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:9B:28:89  
          inet addr:192.168.45.222  Bcast:192.168.45.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe9b:2889/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225410 (220.1 KB)  TX bytes:74225 (72.4 KB)
          Interrupt:21 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16883 (16.4 KB)  TX bytes:16883 (16.4 KB)

ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.45.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.45.254  0.0.0.0         UG    100    0        0 eth0

ubuntu@ubuntu:~$ tracepath [www.google.com](www.google.com)
 1:  ubuntu.local (192.168.45.222)                          0.180ms pmtu 1500
 1:  192.168.45.254 (192.168.45.254)                        0.901ms 
 2:  10.2.2.253 (10.2.2.253)                              199.684ms 
 3:  222.124.162.129 (222.124.162.129)                    128.333ms 
 4:  10.20.31.1 (10.20.31.1)                              239.380ms 
 5:  192.168.9.117 (192.168.9.117)                         92.721ms 
 6:  no reply
 7:  203.208.190.121 (203.208.190.121)                    asymm 14 136.902ms 
 8:  ae0-100.sngtp-dr1.ix.singtel.com (203.208.183.194)   asymm 14 163.101ms 
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply

when i ttry wget this is the result:
ubuntu@ubuntu:~$ wget [www.google.com](www.google.com)
--03:51:10--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 74.125.19.104, 74.125.19.147, 74.125.19.99, ...
Connecting to [www.google.com|74.125.19.104|:80](www.google.com|74.125.19.104|:80)... failed: Connection timed out.
Connecting to [www.google.com|74.125.19.147|:80](www.google.com|74.125.19.147|:80)... 

the connection was take long period and fail.

and ones that make me very confuse, why win can work normally with same router but ubuntu linux cant, is there any difference paradigm internet connection between linux and win?

Or is there any machine that can cause stop my ubunutu connection ?

Do you have any suggest?

---

### Post by bigboy_pdb on 2009-05-13
> **abu salma said:**
> 
today i try to use ubuntu live-cd that before can get internet web page normally, but the problem does not corrected.:(


Sorry, I wasn't certain about what you mean here. Does your live CD connect to the internet properly?

You can try changing network interfaces file so that there's a dhcp connection.

```

auto eth0
iface eth0 inet dhcp

```

You can also try changing your nameserver in your resolv.conf file so that it uses your router's ip address.

```

nameserver *router_ip_address*

```

I would also suggest using a program like Wireshark or tcpdump to view the traffic that passes through your network interface, but I'm guessing that you don't have either installed.

---

### Post by abu salma on 2009-05-13
> **bigboy_pdb said:**
> Sorry, I wasn't certain about what you mean here. Does your live CD connect to the internet properly?


You can try changing network interfaces file so that there's a dhcp connection.[B] 
No, i fail to connect to internet with my ubuntu live cd.[/B]
> ```

auto eth0
iface eth0 inet dhcp

```**  Our LAN network use static ip connection, so the number is my ubuntu box ip number.**

> You can also try changing your nameserver in your resolv.conf file so that it uses your router's ip address.** I use name server number, that can work with win xp.**

>  ```

nameserver *router_ip_address*

```I would also suggest using a program like Wireshark or tcpdump to view the traffic that passes through your network interface, but I'm guessing that you don't have either installed.** That's my problem i cant download anything from internet.**

---

### Post by abu salma on 2009-05-15
today i install wireshark in my ubuntu machine of course it's very difficult, i use win-firefox to do this boring job.

when i browse, i capture my eth0 and i get this data. My ubuntu ip address is 192.168.45.222, may be you can help me what happen about my ubuntu internet connection with tihs data:
No.     Time        Source                Destination           Protocol Info
      1 0.000000    192.168.45.222        74.125.19.99          TCP      48664 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 WS=5

Frame 1 (66 bytes on wire, 66 bytes captured)
    Arrival Time: May 15, 2009 11:19:39.669280000
    [Time delta from previous captured frame: 0.000000000 seconds]
    [Time delta from previous displayed frame: 0.000000000 seconds]
    [Time since reference or first frame: 0.000000000 seconds]
    Frame Number: 1
    Frame Length: 66 bytes
    Capture Length: 66 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:tcp]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: AsustekC_9b:28:89 (00:17:31:9b:28:89), Dst: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Destination: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.45.222 (192.168.45.222), Dst: 74.125.19.99 (74.125.19.99)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 52
    Identification: 0x807b (32891)
    Flags: 0x04 (Don't Fragment)
        0... = Reserved bit: Not set
        .1.. = Don't fragment: Set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: TCP (0x06)
    Header checksum: 0x6de2 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.45.222 (192.168.45.222)
    Destination: 74.125.19.99 (74.125.19.99)
Transmission Control Protocol, Src Port: 48664 (48664), Dst Port: http (80), Seq: 0, Len: 0
    Source port: 48664 (48664)
    Destination port: http (80)
    Sequence number: 0    (relative sequence number)
    Header length: 32 bytes
    Flags: 0x02 (SYN)
        0... .... = Congestion Window Reduced (CWR): Not set
        .0.. .... = ECN-Echo: Not set
        ..0. .... = Urgent: Not set
        ...0 .... = Acknowledgment: Not set
        .... 0... = Push: Not set
        .... .0.. = Reset: Not set
        .... ..1. = Syn: Set
        .... ...0 = Fin: Not set
    Window size: 5840
    Checksum: 0x1bba [correct]
        [Good Checksum: True]
        [Bad Checksum: False]
    Options: (12 bytes)
        Maximum segment size: 1460 bytes
        NOP
        NOP
        SACK permitted
        NOP
        Window scale: 5 (multiply by 32)

No.     Time        Source                Destination           Protocol Info
      2 4.999917    AsustekC_9b:28:89     Routerbo_1a:19:d3     ARP      Who has 192.168.45.254?  Tell 192.168.45.222

Frame 2 (42 bytes on wire, 42 bytes captured)
    Arrival Time: May 15, 2009 11:19:44.669197000
    [Time delta from previous captured frame: 4.999917000 seconds]
    [Time delta from previous displayed frame: 4.999917000 seconds]
    [Time since reference or first frame: 4.999917000 seconds]
    Frame Number: 2
    Frame Length: 42 bytes
    Capture Length: 42 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:arp]
    [Coloring Rule Name: ARP]
    [Coloring Rule String: arp]
Ethernet II, Src: AsustekC_9b:28:89 (00:17:31:9b:28:89), Dst: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Destination: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: ARP (0x0806)
Address Resolution Protocol (request)
    Hardware type: Ethernet (0x0001)
    Protocol type: IP (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: request (0x0001)
    Sender MAC address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
    Sender IP address: 192.168.45.222 (192.168.45.222)
    Target MAC address: 00:00:00_00:00:00 (00:00:00:00:00:00)
    Target IP address: 192.168.45.254 (192.168.45.254)

No.     Time        Source                Destination           Protocol Info
      3 5.000023    Routerbo_1a:19:d3     AsustekC_9b:28:89     ARP      192.168.45.254 is at 00:0c:42:1a:19:d3

Frame 3 (60 bytes on wire, 60 bytes captured)
    Arrival Time: May 15, 2009 11:19:44.669303000
    [Time delta from previous captured frame: 0.000106000 seconds]
    [Time delta from previous displayed frame: 0.000106000 seconds]
    [Time since reference or first frame: 5.000023000 seconds]
    Frame Number: 3
    Frame Length: 60 bytes
    Capture Length: 60 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:arp]
    [Coloring Rule Name: ARP]
    [Coloring Rule String: arp]
Ethernet II, Src: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3), Dst: AsustekC_9b:28:89 (00:17:31:9b:28:89)
    Destination: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: ARP (0x0806)
    Trailer: 000000000000000000000000000000000000
Address Resolution Protocol (reply)
    Hardware type: Ethernet (0x0001)
    Protocol type: IP (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: reply (0x0002)
    Sender MAC address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Sender IP address: 192.168.45.254 (192.168.45.254)
    Target MAC address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
    Target IP address: 192.168.45.222 (192.168.45.222)

No.     Time        Source                Destination           Protocol Info
      4 96.000091   192.168.45.222        74.125.19.103         TCP      39735 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 WS=5

Frame 4 (66 bytes on wire, 66 bytes captured)
    Arrival Time: May 15, 2009 11:21:15.669371000
    [Time delta from previous captured frame: 91.000068000 seconds]
    [Time delta from previous displayed frame: 91.000068000 seconds]
    [Time since reference or first frame: 96.000091000 seconds]
    Frame Number: 4
    Frame Length: 66 bytes
    Capture Length: 66 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:tcp]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: AsustekC_9b:28:89 (00:17:31:9b:28:89), Dst: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Destination: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.45.222 (192.168.45.222), Dst: 74.125.19.103 (74.125.19.103)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 52
    Identification: 0x28a2 (10402)
    Flags: 0x04 (Don't Fragment)
        0... = Reserved bit: Not set
        .1.. = Don't fragment: Set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: TCP (0x06)
    Header checksum: 0xc5b7 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.45.222 (192.168.45.222)
    Destination: 74.125.19.103 (74.125.19.103)
Transmission Control Protocol, Src Port: 39735 (39735), Dst Port: http (80), Seq: 0, Len: 0
    Source port: 39735 (39735)
    Destination port: http (80)
    Sequence number: 0    (relative sequence number)
    Header length: 32 bytes
    Flags: 0x02 (SYN)
        0... .... = Congestion Window Reduced (CWR): Not set
        .0.. .... = ECN-Echo: Not set
        ..0. .... = Urgent: Not set
        ...0 .... = Acknowledgment: Not set
        .... 0... = Push: Not set
        .... .0.. = Reset: Not set
        .... ..1. = Syn: Set
        .... ...0 = Fin: Not set
    Window size: 5840
    Checksum: 0x7d6d [correct]
        [Good Checksum: True]
        [Bad Checksum: False]
    Options: (12 bytes)
        Maximum segment size: 1460 bytes
        NOP
        NOP
        SACK permitted
        NOP
        Window scale: 5 (multiply by 32)

No.     Time        Source                Destination           Protocol Info
      5 98.999931   192.168.45.222        74.125.19.103         TCP      39735 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 WS=5

Frame 5 (66 bytes on wire, 66 bytes captured)
    Arrival Time: May 15, 2009 11:21:18.669211000
    [Time delta from previous captured frame: 2.999840000 seconds]
    [Time delta from previous displayed frame: 2.999840000 seconds]
    [Time since reference or first frame: 98.999931000 seconds]
    Frame Number: 5
    Frame Length: 66 bytes
    Capture Length: 66 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:tcp]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: AsustekC_9b:28:89 (00:17:31:9b:28:89), Dst: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Destination: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.45.222 (192.168.45.222), Dst: 74.125.19.103 (74.125.19.103)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 52
    Identification: 0x28a3 (10403)
    Flags: 0x04 (Don't Fragment)
        0... = Reserved bit: Not set
        .1.. = Don't fragment: Set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: TCP (0x06)
    Header checksum: 0xc5b6 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.45.222 (192.168.45.222)
    Destination: 74.125.19.103 (74.125.19.103)
Transmission Control Protocol, Src Port: 39735 (39735), Dst Port: http (80), Seq: 0, Len: 0
    Source port: 39735 (39735)
    Destination port: http (80)
    Sequence number: 0    (relative sequence number)
    Header length: 32 bytes
    Flags: 0x02 (SYN)
        0... .... = Congestion Window Reduced (CWR): Not set
        .0.. .... = ECN-Echo: Not set
        ..0. .... = Urgent: Not set
        ...0 .... = Acknowledgment: Not set
        .... 0... = Push: Not set
        .... .0.. = Reset: Not set
        .... ..1. = Syn: Set
        .... ...0 = Fin: Not set
    Window size: 5840
    Checksum: 0x7d6d [correct]
        [Good Checksum: True]
        [Bad Checksum: False]
    Options: (12 bytes)
        Maximum segment size: 1460 bytes
        NOP
        NOP
        SACK permitted
        NOP
        Window scale: 5 (multiply by 32)

No.     Time        Source                Destination           Protocol Info
      6 100.999920  AsustekC_9b:28:89     Routerbo_1a:19:d3     ARP      Who has 192.168.45.254?  Tell 192.168.45.222

Frame 6 (42 bytes on wire, 42 bytes captured)
    Arrival Time: May 15, 2009 11:21:20.669200000
    [Time delta from previous captured frame: 1.999989000 seconds]
    [Time delta from previous displayed frame: 1.999989000 seconds]
    [Time since reference or first frame: 100.999920000 seconds]
    Frame Number: 6
    Frame Length: 42 bytes
    Capture Length: 42 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:arp]
    [Coloring Rule Name: ARP]
    [Coloring Rule String: arp]
Ethernet II, Src: AsustekC_9b:28:89 (00:17:31:9b:28:89), Dst: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Destination: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: ARP (0x0806)
Address Resolution Protocol (request)
    Hardware type: Ethernet (0x0001)
    Protocol type: IP (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: request (0x0001)
    Sender MAC address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
    Sender IP address: 192.168.45.222 (192.168.45.222)
    Target MAC address: 00:00:00_00:00:00 (00:00:00:00:00:00)
    Target IP address: 192.168.45.254 (192.168.45.254)

No.     Time        Source                Destination           Protocol Info
      7 101.000027  Routerbo_1a:19:d3     AsustekC_9b:28:89     ARP      192.168.45.254 is at 00:0c:42:1a:19:d3

Frame 7 (60 bytes on wire, 60 bytes captured)
    Arrival Time: May 15, 2009 11:21:20.669307000
    [Time delta from previous captured frame: 0.000107000 seconds]
    [Time delta from previous displayed frame: 0.000107000 seconds]
    [Time since reference or first frame: 101.000027000 seconds]
    Frame Number: 7
    Frame Length: 60 bytes
    Capture Length: 60 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:arp]
    [Coloring Rule Name: ARP]
    [Coloring Rule String: arp]
Ethernet II, Src: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3), Dst: AsustekC_9b:28:89 (00:17:31:9b:28:89)
    Destination: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: ARP (0x0806)
    Trailer: 000000000000000000000000000000000000
Address Resolution Protocol (reply)
    Hardware type: Ethernet (0x0001)
    Protocol type: IP (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: reply (0x0002)
    Sender MAC address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Sender IP address: 192.168.45.254 (192.168.45.254)
    Target MAC address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
    Target IP address: 192.168.45.222 (192.168.45.222)

No.     Time        Source                Destination           Protocol Info
      8 104.999928  192.168.45.222        74.125.19.103         TCP      39735 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 WS=5

Frame 8 (66 bytes on wire, 66 bytes captured)
    Arrival Time: May 15, 2009 11:21:24.669208000
    [Time delta from previous captured frame: 3.999901000 seconds]
    [Time delta from previous displayed frame: 3.999901000 seconds]
    [Time since reference or first frame: 104.999928000 seconds]
    Frame Number: 8
    Frame Length: 66 bytes
    Capture Length: 66 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:tcp]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: AsustekC_9b:28:89 (00:17:31:9b:28:89), Dst: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Destination: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.45.222 (192.168.45.222), Dst: 74.125.19.103 (74.125.19.103)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 52
    Identification: 0x28a4 (10404)
    Flags: 0x04 (Don't Fragment)
        0... = Reserved bit: Not set
        .1.. = Don't fragment: Set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: TCP (0x06)
    Header checksum: 0xc5b5 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.45.222 (192.168.45.222)
    Destination: 74.125.19.103 (74.125.19.103)
Transmission Control Protocol, Src Port: 39735 (39735), Dst Port: http (80), Seq: 0, Len: 0
    Source port: 39735 (39735)
    Destination port: http (80)
    Sequence number: 0    (relative sequence number)
    Header length: 32 bytes
    Flags: 0x02 (SYN)
        0... .... = Congestion Window Reduced (CWR): Not set
        .0.. .... = ECN-Echo: Not set
        ..0. .... = Urgent: Not set
        ...0 .... = Acknowledgment: Not set
        .... 0... = Push: Not set
        .... .0.. = Reset: Not set
        .... ..1. = Syn: Set
        .... ...0 = Fin: Not set
    Window size: 5840
    Checksum: 0x7d6d [correct]
        [Good Checksum: True]
        [Bad Checksum: False]
    Options: (12 bytes)
        Maximum segment size: 1460 bytes
        NOP
        NOP
        SACK permitted
        NOP
        Window scale: 5 (multiply by 32)

No.     Time        Source                Destination           Protocol Info
      9 116.999933  192.168.45.222        74.125.19.103         TCP      39735 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 WS=5

Frame 9 (66 bytes on wire, 66 bytes captured)
    Arrival Time: May 15, 2009 11:21:36.669213000
    [Time delta from previous captured frame: 12.000005000 seconds]
    [Time delta from previous displayed frame: 12.000005000 seconds]
    [Time since reference or first frame: 116.999933000 seconds]
    Frame Number: 9
    Frame Length: 66 bytes
    Capture Length: 66 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:tcp]
    [Coloring Rule Name: HTTP]
    [Coloring Rule String: http || tcp.port == 80]
Ethernet II, Src: AsustekC_9b:28:89 (00:17:31:9b:28:89), Dst: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
    Destination: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        Address: Routerbo_1a:19:d3 (00:0c:42:1a:19:d3)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        Address: AsustekC_9b:28:89 (00:17:31:9b:28:89)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 192.168.45.222 (192.168.45.222), Dst: 74.125.19.103 (74.125.19.103)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 52
    Identification: 0x28a5 (10405)
    Flags: 0x04 (Don't Fragment)
        0... = Reserved bit: Not set
        .1.. = Don't fragment: Set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: TCP (0x06)
    Header checksum: 0xc5b4 [correct]
        [Good: True]
        [Bad : False]
    Source: 192.168.45.222 (192.168.45.222)
    Destination: 74.125.19.103 (74.125.19.103)
Transmission Control Protocol, Src Port: 39735 (39735), Dst Port: http (80), Seq: 0, Len: 0
    Source port: 39735 (39735)
    Destination port: http (80)
    Sequence number: 0    (relative sequence number)
    Header length: 32 bytes
    Flags: 0x02 (SYN)
        0... .... = Congestion Window Reduced (CWR): Not set
        .0.. .... = ECN-Echo: Not set
        ..0. .... = Urgent: Not set
        ...0 .... = Acknowledgment: Not set
        .... 0... = Push: Not set
        .... .0.. = Reset: Not set
        .... ..1. = Syn: Set
        .... ...0 = Fin: Not set
    Window size: 5840
    Checksum: 0x7d6d [correct]
        [Good Checksum: True]
        [Bad Checksum: False]
    Options: (12 bytes)
        Maximum segment size: 1460 bytes
        NOP
        NOP
        SACK permitted
        NOP
        Window scale: 5 (multiply by 32)

---

### Post by abu salma on 2009-05-18
hello everybody where are you, i neep help. please help me, 
Is there any body can analyze wireshark code. why my internet down ?

---

### Post by matyasfalvi on 2009-05-18
Hi I have exactly the same freakin problem!

this should help however only temporarily once you shut down you would have to do the same thing again to get your firefox up and running:

type in terminal: 

```


sudo ifconfig lo 127.0.0.1 netmask 255.0.0.0


```

the loopback doesn't start automatically!

Please anybody who knows how to fix that for good please let us know would be much appreciated.  

peace

---

### Post by abu salma on 2009-05-18
today, after very boring time for inspect my ubuntu box.
and i try inspect my wireshark data, and i was contact my network administartor,  the problem was our network restrict port 8081-until end number port, if the port was enable, the internet connction, can be connected,

The problem now why it is not happen on win xp. Win Xp can connect normally.

Any body have any solutions about it.

---

### Post by matyasfalvi on 2009-05-18
I c then urs is probably different from mine.

 fixed my problem with this:

I deleted:

```

iface eth0 inet dhcp
auto eth0

```

from my 
```

etc/network/interfaces 

```
file

however i dunno why this solved the problem if anybody has an explanation i would love to hear that.

also I have this strange thing when run fprot i get this:

```

[Found possible virus] <Heuristic-90 (not disinfectable)>     /usr/lib/debug/usr/lib/firefox/firefox-2-bin
[Found possible virus] <Heuristic-90 (not disinfectable)>     /usr/lib/debug/usr/lib/firefox/xpcshell
[Found possible virus] <Heuristic-90 (not disinfectable)>     /usr/lib/debug/usr/lib/firefox/regxpcom
[Found possible virus] <Heuristic-90 (not disinfectable)>     /usr/lib/debug/usr/lib/firefox/obscure-tool
[Found possible virus] <Heuristic-90 (not disinfectable)>     /usr/lib/debug/usr/lib/firefox/xpidl
[Found possible virus] <Heuristic-90 (not disinfectable)>     /usr/lib/debug/usr/lib/firefox/xpt_dump
[Found possible virus] <Heuristic-90 (not disinfectable)>     /usr/lib/debug/usr/lib/firefox/xpt_link
[Found possible virus] <Heuristic-90 (not disinfectable)>     /usr/lib/debug/usr/lib/firefox/xpicleanup

``` 

what is this all about???

thanx a lot!

peace

---

