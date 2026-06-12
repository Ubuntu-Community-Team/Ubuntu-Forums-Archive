---
title: "Ubuntu router and PS3."
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by gadikas on 2011-03-29
Hi I have problem with connecting my PlayStation 3 through my Ubuntu router.
The server/router runs Ubuntu server 10.10, webmin and and other server software. 
My machine has  two network cards.

eth0  is connected to the unsafe menacing internet.
eth1 is my  local and safe LAN. 

With my  windows pc the network traffic works. The ps3 gets a ip-number from the router but cant connect to internet. It gets the "dns 80710102" error. I tried enter the DNS info manually. I even tryed to use other DNS like Google DNS and a friends ISP's DNS nothing works. Here are my  iptabels from webmin.

Packet filtering (FILTER)
```
Incoming packets (INPUT) - Only applies to packets addressed to this host
    Action      Condition        
    Accept     If protocol is TCP and source port is 22         
    Accept     If protocol is TCP and source port is 80         
    Accept     If protocol is TCP and source port is 10000         
    Accept     If protocol is TCP and source port is 9091         
    Accept     If input interface is lo         
    Accept     If input interface is eth1         
    Accept     If input interface is eth0 and state of connection is ESTABLISHED,RELATED
``````
Forwarded packets (FORWARD) - Only applies to packets passed through this host
    Action     Condition 
    Accept     If input interface is eth1 and output interface is eth0         
    Accept     If input interface is eth0 and output interface is eth1 and state of connection is ESTABLISHED,RELATED
```Network addres translation (NAT)
```
Packets after routing (POSTROUTING)
    Action          Condition    
    Masquerade     If output interface is eth0

```Do i need to add a other line somewhere to make the ps3 to connect to internet?

---

### Post by dacoolio on 2011-03-29
Has the Windows computer you tried connecting with ever given you any problems, or did it work out of the box?

---

### Post by gadikas on 2011-03-29
> **dacoolio said:**
> Has the Windows computer you tried connecting with ever given you any problems, or did it work out of the box?
yes, no problems  at all. :)

Followed this guide for webmin. 
[http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001)

---

### Post by gadikas on 2011-03-30
Communication between  ps3an and my router  must surely create a  selection in a log  file. The only question is which.

---

### Post by patryk77 on 2011-03-30
Hey!

First thing you should do is open access from UDP port 53, as DNS queries generally use UDP and not TCP, so under forwarded:

Accept If protocol is UDP and source port is 53

Apply... If it still doesn't work, try browsing with an IP address like [http://74.125.159.105](http://74.125.159.105) for google's website.

Good luck!

(Edit: I mean browsing to see if that works, to make sure it's a DNS issue, not as a permanent solution of course.)

---

### Post by gadikas on 2011-03-30
> **patryk77 said:**
> Hey!

First thing you should do is open access from UDP port 53, as DNS queries generally use UDP and not TCP, so under forwarded:

Accept If protocol is UDP and source port is 53

Apply... If it still doesn't work, try browsing with an IP address like [http://74.125.159.105](http://74.125.159.105) for google's website.

Good luck!

(Edit: I mean browsing to see if that works, to make sure it's a DNS issue, not as a permanent solution of course.)
Added the UDP port to forward, but no change to the result. The ps3 still cant connect to internet. I get the same result when i tried to use the ps3 web-browser and entered the adders you gave me.  :confused:

---

### Post by patryk77 on 2011-03-30
My PS3 is kind of 10 000 KMs away, so don't ask me how to do it, but please provide the following (or as much as possible):

settings for the ps3 (IP, netmask, gateway as well as DNS)

Network hardware/layout (mostly is the LAN using a router or a hub?)

If it's a router, LAN / WAN settings

Output of "ifconfig" on the machine running Webmin... 

Hopefully that will give me a bit more info


Edit: Going back over your Webmin rules, I see some strange entries...
When you say "other server software" do you mean you want to be able to access SSH, Apache and Webmin from remote locations? If so, the rules should be for Destination ports, not Source ports ;)

That won't affect the PS3; although if you DO have apache installed on your router/server, you can also try the server's LAN ip in the PS3's browser... [http://192.168.0.1](http://192.168.0.1) or whatever, that should load your page.

---

### Post by gadikas on 2011-03-31
> **patryk77 said:**
> My PS3 is kind of 10 000 KMs away, so don't ask me how to do it, but please provide the following (or as much as possible):

settings for the ps3 (IP, netmask, gateway as well as DNS)

I leve every thing on automatic.

List of internet settings from the ps3
```

internet-connection: activated
uconnection method: weird
Speed and duplex: Automatic
Address settings: Automatic
IP-Addres: 192.168.0.101
Net Mask: 255.255.255.0
Standard router: 192.168.0.0
Primary DNS: 192.168.0.0
Secondery DNS: 0.0.0.0
MAC-address:  A8:E3...............
MTU: Automatic
Proxy: Not used
UPnP: Not available 
NAT-Typ: Failed 

```> 
Network hardware/layout (mostly is the LAN using a router or a hub?)

If it's a router, LAN / WAN settings
I have a fiber switch from my isp "OpeNet". That switch is connected to my Ubuntu pc who acts as a router and server. Then i have a second network chard connected to a standard network switch to create my internal LAN. 
> 
Output of "ifconfig" on the machine running Webmin... 

Hopefully that will give me a bit more info

Do not want to share my ip on the internet for security reasons. I masked out the real ip whith *..
Ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:9d:7f:2e
          inet addr:88.***.***.***  Bcast:88.83.34.63  Mask:255.255.255.192
          inet6 addr: ***::***:49ff:fe9d:7f2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:741109841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1335325332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:115732457026 (115.7 GB)  TX bytes:1829744850839 (1.8 TB)
          Interrupt:42 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:6a:3c:c0
          inet addr:192.168.0.0  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe6a:3cc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265528835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203288382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:292444913327 (292.4 GB)  TX bytes:56674493339 (56.6 GB)
          Interrupt:20 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:287735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:34287298 (34.2 MB)  TX bytes:34287298 (34.2 MB)
```> Edit: Going back over your Webmin rules, I see some strange entries...
When you say "other server software" do you mean you want to be able to  access SSH, Apache and Webmin from remote locations? If so, the rules  should be for Destination ports, not Source ports ;)OPS thanks :)



> That won't affect the PS3; although if you DO have apache installed on  your router/server, you can also try the server's LAN ip in the PS3's  browser... [http://192.168.0.1]("http://192.168.0.1/")  or whatever, that should load your pageno i get the same error. Works on the windows pc

---

### Post by patryk77 on 2011-03-31
```
$ ipcalc 192.168.0.0/24
Address:   192.168.0.0          11000000.10101000.00000000. 00000000
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.0.0/24       11000000.10101000.00000000. 00000000
HostMin:   192.168.0.1          11000000.10101000.00000000. 00000001
HostMax:   192.168.0.254        11000000.10101000.00000000. 11111110
Broadcast: 192.168.0.255        11000000.10101000.00000000. 11111111
Hosts/Net: 254                   Class C, Private Internet

```

Why is your IP address 192.168.0.0 :confused:

AFAIK, this is not a usable address... [quote=http://mwolk.com/192.168.0.0]192.168.0.0 is a private IPv4 router address used by network routers to generically reference the private network. It's unusable, as it's reserved for use as a network address. [/quote]

Try setting eth1 to 192.168.0.1 and see if that helps.

I am quite curious as to what your Windows machine uses as a gateway :o

---

### Post by gadikas on 2011-03-31
> **patryk77 said:**
> 
Try setting eth1 to 192.168.0.1 and see if that helps.
THANKS now every ting works :popcorn:

---

### Post by patryk77 on 2011-03-31
Perfect... I guess that's the nice thing about Open Source software... It will let you do things you aren't meant to, which is a blessing and a curse :P

It will let you do things that should be forbidden, but it doesn't mean it will work the way you expect it.

Cheers!

---

