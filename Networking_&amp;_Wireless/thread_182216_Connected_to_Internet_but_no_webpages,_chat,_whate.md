---
title: "Connected to Internet but no webpages, chat, whatever..."
date: 2006-05-25
forum: Networking &amp; Wireless
---

### Post by [Rado] on 2006-05-25
I have installed successfully **ERICSSON HM120DP** on my new **Ubuntu 5.10** OS.

This is the log:

> [EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

GlobeSpan GS7070 USB ADSL WAN Modem compatible modem found (in 2406ms)
eciadsl-firmware: success
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

OK eciadsl-synch: success
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 22
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <magic 0xcb33fe65>]
rcvd [LCP ConfReq id=0x1 <auth pap> <magic 0x59524b0c>]
sent [LCP ConfAck id=0x1 <auth pap> <magic 0x59524b0c>]
sent [LCP ConfReq id=0x1 <magic 0xcb33fe65>]
rcvd [LCP ConfAck id=0x1 <magic 0xcb33fe65>]
sent [PAP AuthReq id=0x1 user="xxx@xxx.xx" password=<hidden>]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 192.168.100.1>]
sent [IPCP ConfAck id=0x1 <addr 192.168.100.1>]
rcvd [IPCP ConfNak id=0x1 <addr 87.10.227.179> <ms-dns1 85.37.17.16> <ms-dns3 85.38.28.68>]
sent [IPCP ConfReq id=0x2 <addr 87.10.227.179> <ms-dns1 85.37.17.16> <ms-dns3 85.38.28.68>]
rcvd [IPCP ConfAck id=0x2 <addr 87.10.227.179> <ms-dns1 85.37.17.16> <ms-dns3 85.38.28.68>]
local  IP address 87.10.227.179
remote IP address 192.168.100.1
primary  DNS address 85.37.17.16
secondary DNS address 85.38.28.68
Connection successful

[EciAdsl 5/5] Setting up route table...

Waiting for ppp0...
rado@Rado:~/Desktop/eciadsl-usermode-0.11$

**Remote Desktop** - it works, maybe a little bit slow, but still works. A friend of my was able to connect to me and try to configure Ubuntu with no luck.
**Ping** - it works, I can ping whatever website I want.

*ping [www.symantec.com](www.symantec.com)*  for examle

HOWEVER:

**Firefox** - no pages are displayed. Not even using the IP of the given website.
**Synaptic** - it downloads at ~ 30B or even slower :-k 
**Gaim** - it says: connection established, cookie sent, BUT then it suddenly stops.
**XIRC**, could not connect.

I'm directly connected to internet with this USB modem, no routers, firewall, whatsoever... ](*,) 

Please help!


Thanks in advance :)

---

### Post by evilgold on 2006-05-25
use the ethernet connection instead of USB. usb is MUCH slower then a normal ethernet cable.

---

### Post by jvictor on 2006-05-26
Firefox - no pages are displayed. Not even using the IP of the given website.

type about:config in ur brwsers add bar and toggle the value of 

network.dns.disableIpv6 ( it must be chaged to true)

next, 
disable IPV6 system wide and reboot , search forums on  "disable ipv6".. then lets us know whether things are working.

---

### Post by claytonc on 2006-05-26
Hi,

Have you assigned DNS servers addresses?

---

### Post by [Rado] on 2006-05-26
jvictor, thanks a lot!

However I have deleted Ubuntu and can't try with IPv6 right now.
Will give it a try in the future and will repply here.


@ claytonc - yes the DNS are OK.
As I said I have no problem to ping [www.microsoft.com](www.microsoft.com) and it resolves the IP adress - so the DNS is just fine ;)

---

### Post by [Rado] on 2006-05-28
Hi again!

This time I installed ubuntu-6.06-rc-desktop-i386 ;) 
It's cool however I have exactly the same problem with my Internet connection.

Here are some logs so hopefully someone could understand what's wrong:


> [EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

GlobeSpan GS7070 USB ADSL WAN Modem compatible modem found (in 2070ms)
eciadsl-firmware: success
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

OK eciadsl-synch: success 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 2
Using interface ppp0
Connect: ppp0 <--> /dev/pts/0
sent [LCP ConfReq id=0x1 <magic 0x2d50efb3>]
sent [LCP ConfReq id=0x1 <magic 0x2d50efb3>]
rcvd [LCP ConfReq id=0x1 <auth pap> <magic 0x68221408>]
sent [LCP ConfAck id=0x1 <auth pap> <magic 0x68221408>]
sent [LCP ConfReq id=0x1 <magic 0x2d50efb3>]
rcvd [LCP ConfAck id=0x1 <magic 0x2d50efb3>]
sent [PAP AuthReq id=0x1 user="xxx@xxx.xx" password=<hidden>]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 192.168.100.1>]
sent [IPCP ConfAck id=0x1 <addr 192.168.100.1>]
rcvd [IPCP ConfNak id=0x1 <addr 87.7.214.112> <ms-dns1 212.216.172.62> <ms-dns3 151.99.125.1>]
sent [IPCP ConfReq id=0x2 <addr 87.7.214.112> <ms-dns1 212.216.172.62> <ms-dns3 151.99.125.1>]
rcvd [IPCP ConfAck id=0x2 <addr 87.7.214.112> <ms-dns1 212.216.172.62> <ms-dns3 151.99.125.1>]
local  IP address 87.7.214.112
remote IP address 192.168.100.1
primary   DNS address 212.216.172.62
secondary DNS address 151.99.125.1
Connection successful

[EciAdsl 5/5] Setting up route table...

Waiting for ppp0...
Adding default route... SIOCADDRT: File exists
failed to set default route to ppp0

**route -n**
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

I think this is bad ](*,) 
It was written in my drivers I have to see one UG flag :-k 


**ifconfig ppp0**
> ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.7.214.112  P-t-P:192.168.100.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:15237 (14.8 KiB)  TX bytes:15547 (15.1 KiB)


**cat /etc/resolv.conf**
> nameserver 212.216.172.62
nameserver 151.99.125.1
These DNS are the same as those I see in WinXP ;) 


Furthermore:

**disabling IPv6** using:

> 1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

// tried with these as well:
alias net-pf-10 off ipv6
alias net-pf-10 off #ipv6

When I disable IPv6 in this way I can't connect to Internet at all.
All I see is [EciAdsl 4/5] Connecting to provider... and it takes forever ](*,) 

Disabling IPv6 in Firefox doesn't change anything.


Any help is much appreciated :D

---

