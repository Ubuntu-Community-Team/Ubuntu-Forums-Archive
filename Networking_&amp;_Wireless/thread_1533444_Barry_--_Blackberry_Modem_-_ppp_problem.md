---
title: "Barry -- Blackberry Modem - ppp problem"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by slinkeey on 2010-07-18
Hello,

I have been trying to use barry to use my blackberry modem.

When I run "sudo pppd call barry-att_cingular" the blackbery does it thing, displays a message on it that the modem is in use, then I see a message on my ubuntu based notebook that it got assigned an ip address..

It tells me the dns servers being used..

a ppp0 device shows up in ifconfig..

```

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.83.33.133  P-t-P:169.254.1.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:174 (174.0 B)  TX bytes:222 (222.0 B)


slinkeey@slinkeey-laptop:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

```

I can not get to google.com by domain name or ip.


Am I missing something here?

Thanks,
Jeff

---

### Post by slinkeey on 2010-07-18
Here is my pppd output

```

slinkeey@slinkeey-laptop:~$ sudo pppd call barry-att_cingular
[sudo] password for slinkeey: 
Setting abort string
Initializing modem
Carrier Information
Connecting
Script /usr/sbin/chat -f /etc/chatscripts/barry-att_cingular.chat finished (pid 2587), status = 0x0
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth pap>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth pap>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0>]
sent [PAP AuthReq id=0x1 user="" password=<hidden>]
rcvd [PAP AuthAck id=0x1]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 169.254.1.1>]
sent [IPCP ConfAck id=0x1 <addr 169.254.1.1>]
rcvd [IPCP ConfNak id=0x1 <compress VJ 0f 01> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <compress VJ 0f 01> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfNak id=0x3 <compress VJ 0f 01> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfNak id=0x4 <compress VJ 0f 01> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
sent [IPCP ConfReq id=0x5 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfNak id=0x5 <compress VJ 0f 01> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Received bad configure-nak:  02 06 00 2d 0f 01 81 06 00 00 00 00 83 06 00 00 00 00
sent [IPCP ConfReq id=0x5 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfRej id=0x5 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x6 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfNak id=0x6 <addr 10.70.54.25> <ms-dns1 172.16.145.103> <ms-dns2 172.16.145.103>]
sent [IPCP ConfReq id=0x7 <addr 10.70.54.25> <ms-dns1 172.16.145.103> <ms-dns2 172.16.145.103>]
rcvd [IPCP ConfAck id=0x7 <addr 10.70.54.25> <ms-dns1 172.16.145.103> <ms-dns2 172.16.145.103>]
Cannot determine ethernet address for proxy ARP
local  IP address 10.70.54.25
remote IP address 169.254.1.1
primary   DNS address 172.16.145.103
secondary DNS address 172.16.145.103
Script /etc/ppp/ip-up started (pid 2595)
Script /etc/ppp/ip-up finished (pid 2595), status = 0x0

```

---

### Post by slinkeey on 2010-07-18
Ok I have an Update:

Internet does work!! It resolved addresses from the command line..  I can use commend line tools like ftp, telnet and etc..  I just can't use the X stuff like mozilla and etc... any ideas?

---

### Post by slinkeey on 2010-07-19
Progress!!

There problem is network manager doesn't see ppp so I did the following in Firefox.

I changed: toolkit.networkmanager.disable;false
To: toolkit.networkmanager.disable;true

Now I can surf the web.. Manually un-checking off-line did not do the trick.

This is kind of a pain, but whatever I guess.

---

