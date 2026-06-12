---
title: "Can connect to internet but cannot ping  router"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by mattyhatty on 2013-07-13
I can ping localhost,ping public IP's....basically my Internet is working.But I am not able to connect to my router
Router addr given by ISP: 192.168.1.1
ping 192.168.1.1 is not working.
I could do so previously but few days ago it stopped working.
I am using ppp over ethernet and used the pppoeconf package to setup my internet.

route -n gives the following result:
 
Kernel IP routing table
Destination          Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0              0.0.0.0         0.0.0.0                 U     0      0        0     ppp0
IP  addr             0.0.0.0         255.255.255.255   UH    0      0        0     ppp0

My gateway address is set to 0.0.0.0 and I am being set a public IP .

any help would be appreciated.

---

### Post by papibe on 2013-07-13
Hi mattyhatty.

It looks like either your are connected to a modem, or the router is set in bridge mode.

Could you post the output of these commands?
```
ifconfig

mtr -rnc 1 google.com
```
Regards.

---

### Post by mattyhatty on 2013-07-13
Yes it's a bridged connection
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:a4:e5:12:2a  
          inet6 addr: fe80::217:a4ff:fee5:122a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58509221 (58.5 MB)  TX bytes:9542580 (9.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2729097 (2.7 MB)  TX bytes:2729097 (2.7 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.205.114.252  P-t-P:117.205.112.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:308050 (308.0 KB)  TX bytes:63401 (63.4 KB)
```
mtr result : 
```

HOST: monstermachine              Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 117.205.112.1              0.0%     1   38.9  38.9  38.9  38.9   0.0
  2.|-- 218.248.175.118            0.0%     1   48.8  48.8  48.8  48.8   0.0
  3.|-- 115.113.128.17             0.0%     1   78.7  78.7  78.7  78.7   0.0
  4.|-- 172.29.251.34              0.0%     1  104.6 104.6 104.6 104.6   0.0
  5.|-- ???                       100.0     1    0.0   0.0   0.0   0.0   0.0
  6.|-- 115.114.85.245             0.0%     1  320.2 320.2 320.2 320.2   0.0
  7.|-- 180.87.37.14               0.0%     1  320.2 320.2 320.2 320.2   0.0
  8.|-- 180.87.12.1                0.0%     1  319.9 319.9 319.9 319.9   0.0
  9.|-- 72.14.220.134              0.0%     1  369.6 369.6 369.6 369.6   0.0
 10.|-- 66.249.95.124              0.0%     1  331.5 331.5 331.5 331.5   0.0
 11.|-- 66.249.94.73               0.0%     1  139.4 139.4 139.4 139.4   0.0
 12.|-- 72.14.232.101              0.0%     1  137.2 137.2 137.2 137.2   0.0
 13.|-- 209.85.241.189             0.0%     1  135.1 135.1 135.1 135.1   0.0
 14.|-- 173.194.36.41              0.0%     1  135.0 135.0 135.0 135.0   0.0
```

---

### Post by windows2003 on 2013-07-13
it looks like an connection between 2 computers using an serial interface? Is this a computer connected by a phone line to a server? 

Annyway if the surfway to your router is 192.168.1.1 (gateway)
then your computer needs something like:
IP:            192.168.1.30  (30 is an example can be other address, take one who is not in use by other computer or network printer)
submask:  255.255.255.0
gateway:   192.168.1.1

you should something have like mine here below if you ask ifconfig -a

eth0      Link encap:Ethernet  HWaddr (your HW address)  
          inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe19:c83f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:430293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:255965 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:601659425 (573.7 MiB)  TX bytes:21217492 (20.2 MiB)
          Interrupt:17

maybe this link can also help yuo: [http://www.icurtain.co.uk/79_Linux_IP_address_Configuration_ifconfig](http://www.icurtain.co.uk/79_Linux_IP_address_Configuration_ifconfig)

---

### Post by papibe on 2013-07-13
Thanks.

I don't think you will be able to access your router with that configuration, as the router becomes "transparent".

Getting access to it, usually means either:
[LIST]
[*]Temporary disabling ppp, setting your machine with an temporary static IP, say 192.168.1.2, and connect it to the router using a ethernet cable, or
[*]Using some well know trick for the actual router's brand and model. For instance, some Netgear router can be access through another device using a wireless connection.
[/LIST]
Let us know how it goes.
Regards.

---

### Post by mattyhatty on 2013-07-13
Yes this is over phone line.
So how do I set gateway and netmask manually because they were automatically set by dhcp.Is it through ifconfig ppp0 xxx.xxx.xxx.xxx netmask 255.255.255.0?Because my network manager does not show any connections.I don't know if this has any bearing to this problem but my network-manager service stopped loading at boot time and my Ubuntu Precise gives a "Waiting for network manager configuration" message at boot time.I restarted the service manually.

I do get similar IP's like yours when I tether my mobile network.

---

### Post by mattyhatty on 2013-07-13
> **papibe said:**
> Thanks.

I don't think you will be able to access your router with that configuration, as the router becomes "transparent".

Getting access to it, usually means either:
[LIST]
[*]Temporary disabling ppp, setting your machine with an temporary static IP, say 192.168.1.2, and connect it to the router using a ethernet cable, or 
[*]Using some well know trick for the actual router's brand and model. For instance, some Netgear router can be access through another device using a wireless connection. 
[/LIST]
Let us know how it goes.
Regards.

hmm.Could you make me understand how am I able to connect to internet when I am unable to ping my router?And why I could access my router earlier through my browser?

---

### Post by papibe on 2013-07-13
When you set a router in bridge mode, it reduces its functionality significantly, and became a transparent device so that another machine can establish both the PPP link and the DHCP request to the ISP.

As you can see from your mtr output, the modem (192.168.1.1) does not appear in the list. It start in your computer (117.205.112.1) and jumps directly to another machine in the Internet (218.248.175.118).

Setting it in bride mode is is almost like downgrading it to a modem.

Does that help?

---

### Post by mattyhatty on 2013-07-13
> **papibe said:**
> When you set a router in bridge mode, it reduces its functionality significantly, and became a transparent device so that another machine can establish both the PPP link and the DHCP request to the ISP.

As you can see from your mtr output, the modem (192.168.1.1) does not appear in the list. It start in your computer (117.205.112.1) and jumps directly to another machine in the Internet (218.248.175.118).

Setting it in bride mode is is almost like downgrading it to a modem.

Does that help?
I have always connected through this mode for a while.Even in the manual given with the router that's what they instruct - create a bridge connection in Windows.If I am still sending [ethernet frames ]("http://en.wikipedia.org/wiki/Pppoe")which obviously pass through my router why  is it not in my first hop (from mtr output)?

---

### Post by mattyhatty on 2013-07-13
Anyways I set my eth0 interface and now I am able to ping my router as well as open it in my browser.But it still does not appear on mtr output

 ```
sudo ifconfig eth0 192.168.1.30 netmask 255.255.255.0
```

---

### Post by papibe on 2013-07-13
Here's a good article you may find useful: [Bridge versus Router Mode Differences, Advantages and Applications]("http://www.moonblinkwifi.com/routervsbridge.cfm").

Basically, bridge mode set your router's networking to Layer 2:
> Bridges operate at the Data Link Layer (level 2) and do not understand anything about any communications protocol other than the physical medium (MAC), which is typically an Ethernet.
In other words, what goes in goes out and vice-versa. No IP foot print or coloring. 

Regards.

P.S.: another way to access your router set in bridge mode would be to create a VLAN and the proper route on the router itself. This would be possible only if the router's firmware allows that functionality (for instance Tomato and DD-WRT do). Another way would be to enable your ethernet interface and setting manually as described in post #5.

---

### Post by mattyhatty on 2013-07-13
> **papibe said:**
>  Another way would be to enable your ethernet interface and setting manually as described in post #5.

I have been provided with a username and password for authentication to my ISP server.
pppoeconf uses the pap/chap protocols to achieve this from /etc/ppp/chap-secrets and etc/ppp/pap-secrets.

If I configure manually and not use bridge(ppp)how do I achieve this.
I edit the interface eth0 in /etc/network/interfaces and put the interface to static and put in the details.
Get DNS from etc/resolv.conf .
If I am not using ppp where do I edit my username and password?
Also if I will use a private ip like 192.xxx.xxx.xxx how do I setup NAT or is it already configured?

---

