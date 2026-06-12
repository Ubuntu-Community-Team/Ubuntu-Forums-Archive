---
title: "SwissVPN - Able to connect, but can't reach anything."
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by niccoswe on 2009-04-19
Hi, i have been struggling trying to get a working VPN connection for my ubuntu server/firewall for four days now. I can get a connection to the swissVPN server. 

Here is the output from ifconfig ppp0

```


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:80.254.73.180  P-t-P:80.254.79.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1456  Metric:1
          RX packets:1893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:115814 (113.0 KB)  TX bytes:862 (862.0 B)
```


I'm also able to ping the server.

```
ping -I ppp0 80.254.79.64
PING 80.254.79.64 (80.254.79.64) from 80.254.73.180 ppp0: 56(84) bytes of data.
64 bytes from 80.254.79.64: icmp_seq=1 ttl=64 time=49.1 ms
64 bytes from 80.254.79.64: icmp_seq=2 ttl=64 time=50.6 ms
64 bytes from 80.254.79.64: icmp_seq=3 ttl=64 time=49.0 ms

--- 80.254.79.64 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 49.047/49.591/50.608/0.719 ms

```

But i can´t in the world figure out what to do to be able to reach internet through the VPN connection. I tried pinging google.com with "ping -I ppp0 google.com", but i get no response. Whatever i ping on the internet through ppp0 i get no response. 

What am i missing?

---

### Post by niccoswe on 2009-04-19
Here´s the output from 
pon swissvpn debug dump logfd 2 nodetach

```
pon swissvpn debug dump logfd 2 nodetach
pppd options in effect:
debug		# (from command line)
nodetach		# (from command line)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options_swiss)
refuse-chap		# (from /etc/ppp/options_swiss)
refuse-mschap		# (from /etc/ppp/options_swiss)
refuse-eap		# (from /etc/ppp/options_swiss)
name bvwjzmgz		# (from /etc/ppp/peers/swissvpn)
remotename PPTP		# (from /etc/ppp/peers/swissvpn)
		# (from /etc/ppp/options_swiss)
pty pptp connect.swissvpn.net --nolaunchpppd		# (from /etc/ppp/peers/swissvpn)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam swissvpn		# (from /etc/ppp/peers/swissvpn)
proxyarp		# (from /etc/ppp/options)
usepeerdns		# (from /etc/ppp/peers/swissvpn)
nobsdcomp		# (from /etc/ppp/options_swiss)
nodeflate		# (from /etc/ppp/options_swiss)
require-mppe		# (from /etc/ppp/peers/swissvpn)
require-mppe-128		# (from /etc/ppp/options_swiss)
noipx		# (from /etc/ppp/options)
using channel 20
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xfeb5705> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <accomp> <pcomp> <mru 1460> <magic 0xcd9766f6> <auth chap MS-v2> <mrru 2048> <ssnhf> <endpoint [MAC:00:50:56:9c:1c:61]>]
sent [LCP ConfRej id=0x1 <mrru 2048> <ssnhf>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xfeb5705> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x2 <accomp> <pcomp> <mru 1460> <magic 0xcd9766f6> <auth chap MS-v2>]
sent [LCP ConfAck id=0x2 <accomp> <pcomp> <mru 1460> <magic 0xcd9766f6> <auth chap MS-v2>]
sent [LCP EchoReq id=0x0 magic=0xfeb5705]
rcvd [CHAP Challenge id=0x1 <bb1e68e5784b24c4fa4675c58bfca412>, name = ""]
sent [CHAP Response id=0x1 <0d3b4ac52bf28172b40ae5a2f90aa4da000000000000000027369b2175f9d305e5446e2f7d7b59ff22a903feb972995800>, name = "bvwjzmgz"]
rcvd [LCP EchoRep id=0x0 magic=0xcd9766f6]
rcvd [CHAP Success id=0x1 "S=09B5EB8443EB75DE80A2AEEF4A328875906B8047"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [IPCP ConfReq id=0x1 <addr 80.254.79.49> <compress VJ 0f 00>]
sent [IPCP TermAck id=0x1]
rcvd [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <addr 80.254.75.28> <ms-dns1 80.254.79.157> <ms-dns3 80.254.77.39>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 80.254.75.28> <ms-dns1 80.254.79.157> <ms-dns3 80.254.77.39>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 80.254.75.28> <ms-dns1 80.254.79.157> <ms-dns3 80.254.77.39>]
rcvd [IPCP ConfReq id=0x2 <addr 80.254.79.49> <compress VJ 0f 00>]
sent [IPCP ConfAck id=0x2 <addr 80.254.79.49> <compress VJ 0f 00>]
Cannot determine ethernet address for proxy ARP
local  IP address 80.254.75.28
remote IP address 80.254.79.49
primary   DNS address 80.254.79.157
secondary DNS address 80.254.77.39
Script /etc/ppp/ip-up started (pid 28376)
Script /etc/ppp/ip-up finished (pid 28376), status = 0x0
```

---

### Post by superprash2003 on 2009-04-19
post output of **ping 208.67.222.222**

---

### Post by niccoswe on 2009-04-19
If i make a regular **ping 208.67.222.222** i do get a connection, but that´s thrugh my wan interface (eth0). 

If i do a **ping -I ppp0 208.67.222.222** i get this:

```
ping -I ppp0 208.67.222.222
PING 208.67.222.222 (208.67.222.222) from 80.254.74.5 ppp0: 56(84) bytes of data.


```

Then nothing happens since it can´t connect. :(

Can it have something to do with my shorewall firewall?  If that was the case, i should not even be able to ping the vpn server, right?

---

### Post by niccoswe on 2009-04-19
I just noticed that althou i´m not getting a response from 208.67.222.222. I do get something.

Making a tcpdump on the vpn interface, i seem to get a reply. Seems that someting is blocking it from turning up on the console where i´m pinging from.

```
tcpdump -i ppp0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ppp0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
21:22:58.348961 IP 80-254-74-181.dynamic.swissvpn.net > resolver1.opendns.com: ICMP echo request, id 32606, seq 4, length 64
21:22:58.411443 IP resolver1.opendns.com > 80-254-74-181.dynamic.swissvpn.net: ICMP echo reply, id 32606, seq 4, length 64
21:22:59.348946 IP 80-254-74-181.dynamic.swissvpn.net > resolver1.opendns.com: ICMP echo request, id 32606, seq 5, length 64
21:22:59.411697 IP resolver1.opendns.com > 80-254-74-181.dynamic.swissvpn.net: ICMP echo reply, id 32606, seq 5, length 64
21:23:00.348942 IP 80-254-74-181.dynamic.swissvpn.net > resolver1.opendns.com: ICMP echo request, id 32606, seq 6, length 64
21:23:00.410991 IP resolver1.opendns.com > 80-254-74-181.dynamic.swissvpn.net: ICMP echo reply, id 32606, seq 6, length 64
...

```

I have made a VPN tunnel in shorewall, it "shouldn´t" be whats blocking the response.

/etc/shorewall/tunnels:
```
pptpserver	net	0.0.0.0/0
pptpclient	net     0.0.0.0/0
```

Anyone who can point me in the right direction?

---

### Post by niccoswe on 2009-04-20
Anyone? 

i´m stuck. I get the echo response to ppp0, but i can´t get any response output from the ping application.

---

### Post by superprash2003 on 2009-04-22
well if your able to ping then try opening [http://209.85.171.100](http://209.85.171.100)

---

