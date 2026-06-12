---
title: "FQDN DNS not what I expected"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by omro on 2009-06-15
Hi,

I've been following the instructions laid out in this [**guide**]("Ubuntu Forums - Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller") and all the server related instructions seem to have worked fine.

I have a server set up as fs1.mydomain.com.local

When I set up a client kubuntu computer, it can only see fs1 and it resolves name that fine, but I was expecting it to resolve the fully qualified domain name.

> 
ping -w 3 fs1
PING fs1.mydomain.com.local (172.18.30.100) 56(84) bytes of data.
64 bytes from 172.18.30.100: icmp_seq=1 ttl=64 time=0.186 ms

--- fs1.mydomain.com.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.186/0.186/0.186/0.000 ms

ping -w 3 fs1.mydomain.com.local
ping: unknown host fs1.mydomain.com.local



Any ideas where I might have gone wrong?

Thanks!

---

### Post by omro on 2009-06-26
I've tried this again with an ubuntu client and still having the same issue.

Is the issue in the server config? Which is ubuntu server 8.04 or my desktop config?

The server can ping itself using either just it's name fs1 or it's fully qualified domain name of fs1.mydomain.com.local

The ubuntu computer can ping it as fs1, but not fs1.mydomain.com.local

It's a bit confusing and any help would be appreciated!

---

### Post by jonobr on 2009-06-26
It sounds as if you have just setup the name in one host and you want another host to know about it?

If thats the case you have a couple of options.
Either you need to set the other host to have the name resolved in its own host file, or, you set the server up as a dns server where the other host can resolve to (thats trickier) or if you are already usign a dns , add that entry to the dns.

if the desktop gets a ping to a name, it will look at its 
nsswitch.conf file to see the order where to query that name

it has an entry usually of

hosts file dns

This means when you ping a name, it looks at the host file first and then the dns. THe dns is defined in /etc/resolv.conf

If its not in either of those locations the ping will fail.

---

### Post by omro on 2009-06-26
The server is set up as a DNS server as per the instructions in the guide I followed, link in first post.

The server can ping itself using fs1 and fs1.mydomain.com.local

The ubuntu and kubuntu desktops have

> 
search mydomain.com.local
nameserver 192.168.2.101


in their resolv.conf (where the IP is the IP of the server).

Would this suggest that the DNS server is set up incorrectly or that I have not correctly set up the client?

How can I test this?

---

### Post by jonobr on 2009-06-26
On the server you are resolving from (the desktop)

enter 

```
sudo tcpdump -vvxNs0 -i any port 53 
```

This will do a packet trace looking for a dns lookup packets

Do your ping and if you like we could try and interpret the results

---

### Post by omro on 2009-06-26
Thanks

When running

ping fs1.mydomain.com.local

nothing happens

when running

ping fs1

the following comes up:

> sysadmin@fs1:~$ sudo tcpdump -vvxNs0 -i any port 53
tcpdump: WARNING: Promiscuous mode not supported on the "any" device
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 65535 bytes
11:02:19.401095 IP (tos 0x0, ttl 64, id 47947, offset 0, flags [DF], proto UDP (17), length 71) 192.168.2.102.47683 > fs1.domain: [udp sum ok] 62358+ A? fs1.mydomain.com.local. (43)
        0x0000:  4500 0047 bb4b 4000 4011 f93e c0a8 0266
        0x0010:  c0a8 0265 ba43 0035 0033 d1e1 f396 0100
        0x0020:  0001 0000 0000 0000 0776 7365 7276 6572
        0x0030:  076f 7265 736f 6d65 0363 6f6d 056c 6f63
        0x0040:  616c 0000 0100 01
11:02:19.403137 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 101) fs1.domain > 192.168.2.102.47683: [bad udp cksum 757e!] 62358* q: A? fs1.mydomain.com.local. 1/1/0 fs1.mydomain.com.local. A fs1 ns: mydomain.com.local. NS fs1.mydomain.com.local. (73)
        0x0000:  4500 0065 0000 4000 4011 b46c c0a8 0265
        0x0010:  c0a8 0266 0035 ba43 0051 867e f396 8580
        0x0020:  0001 0001 0001 0000 0776 7365 7276 6572
        0x0030:  076f 7265 736f 6d65 0363 6f6d 056c 6f63
        0x0040:  616c 0000 0100 01c0 0c00 0100 0100 0096
        0x0050:  0000 04c0 a802 65c0 1400 0200 0100 0096
        0x0060:  0000 02c0 0c
11:02:19.412835 IP (tos 0x0, ttl 64, id 47962, offset 0, flags [DF], proto UDP (17), length 72) 192.168.2.102.55626 > fs1.domain: [udp sum ok] 51867+ PTR? 101.2.168.192.in-addr.arpa. (44)
        0x0000:  4500 0048 bb5a 4000 4011 f92e c0a8 0266
        0x0010:  c0a8 0265 d94a 0035 0034 16a1 ca9b 0100
        0x0020:  0001 0000 0000 0000 0331 3031 0132 0331
        0x0030:  3638 0331 3932 0769 6e2d 6164 6472 0461
        0x0040:  7270 6100 000c 0001
11:02:19.415194 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 72) fs1.13551 > mymodem.domain: [bad udp cksum 2397!] 26845+ PTR? 101.2.168.192.in-addr.arpa. (44)
        0x0000:  4500 0048 0000 4000 4011 b4ee c0a8 0265
        0x0010:  c0a8 0201 34ef 0035 0034 85fc 68dd 0100
        0x0020:  0001 0000 0000 0000 0331 3031 0132 0331
        0x0030:  3638 0331 3932 0769 6e2d 6164 6472 0461
        0x0040:  7270 6100 000c 0001
11:02:19.419608 IP (tos 0x0, ttl 64, id 37917, offset 0, flags [DF], proto UDP (17), length 72) fs1.36730 > fs1.domain: [bad udp cksum 75d1!] 54070+ PTR? 102.2.168.192.in-addr.arpa. (44)
        0x0000:  4500 0048 941d 4000 4011 206d c0a8 0265
        0x0010:  c0a8 0265 8f7a 0035 0034 8660 d336 0100
        0x0020:  0001 0000 0000 0000 0331 3032 0132 0331
        0x0030:  3638 0331 3932 0769 6e2d 6164 6472 0461
        0x0040:  7270 6100 000c 0001
11:02:19.420766 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 72) fs1.21818 > mymodem.domain: [bad udp cksum 5a55!] 35418+ PTR? 102.2.168.192.in-addr.arpa. (44)
        0x0000:  4500 0048 0000 4000 4011 b4ee c0a8 0265
        0x0010:  c0a8 0201 553a 0035 0034 85fc 8a5a 0100
        0x0020:  0001 0000 0000 0000 0331 3032 0132 0331
        0x0030:  3638 0331 3932 0769 6e2d 6164 6472 0461
        0x0040:  7270 6100 000c 0001
11:02:19.606602 IP (tos 0x0, ttl 255, id 35397, offset 0, flags [DF], proto UDP (17), length 72) mymodem.domain > fs1.13551: [udp sum ok] 26845 NXDomain q: PTR? 101.2.168.192.in-addr.arpa. 0/0/0 (44)
        0x0000:  4500 0048 8a45 4000 ff11 6ba8 c0a8 0201
        0x0010:  c0a8 0265 0035 34ef 0034 9c9c 68dd 8183
        0x0020:  0001 0000 0000 0000 0331 3031 0132 0331
        0x0030:  3638 0331 3932 0769 6e2d 6164 6472 0461
        0x0040:  7270 6100 000c 0001
11:02:19.606700 IP (tos 0x0, ttl 255, id 35398, offset 0, flags [DF], proto UDP (17), length 72) mymodem.domain > fs1.21818: [udp sum ok] 35418 NXDomain q: PTR? 102.2.168.192.in-addr.arpa. 0/0/0 (44)
        0x0000:  4500 0048 8a46 4000 ff11 6ba7 c0a8 0201
        0x0010:  c0a8 0265 0035 553a 0034 5ad3 8a5a 8183
        0x0020:  0001 0000 0000 0000 0331 3032 0132 0331
        0x0030:  3638 0331 3932 0769 6e2d 6164 6472 0461
        0x0040:  7270 6100 000c 0001
11:02:19.608186 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 72) fs1.domain > 192.168.2.102.55626: [bad udp cksum bc0f!] 51867 NXDomain q: PTR? 101.2.168.192.in-addr.arpa. 0/0/0 (44)
        0x0000:  4500 0048 0000 4000 4011 b489 c0a8 0265
        0x0010:  c0a8 0266 0035 d94a 0034 8661 ca9b 8183
        0x0020:  0001 0000 0000 0000 0331 3031 0132 0331
        0x0030:  3638 0331 3932 0769 6e2d 6164 6472 0461
        0x0040:  7270 6100 000c 0001
11:02:19.608462 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 72) fs1.domain > fs1.36730: [bad udp cksum f250!] 54070 NXDomain q: PTR? 102.2.168.192.in-addr.arpa. 0/0/0 (44)
        0x0000:  4500 0048 0000 4000 4011 b48a c0a8 0265
        0x0010:  c0a8 0265 0035 8f7a 0034 8660 d336 8183
        0x0020:  0001 0000 0000 0000 0331 3032 0132 0331
        0x0030:  3638 0331 3932 0769 6e2d 6164 6472 0461
        0x0040:  7270 6100 000c 0001
11:02:19.614187 IP (tos 0x0, ttl 64, id 37937, offset 0, flags [DF], proto UDP (17), length 70) fs1.50833 > fs1.domain: [bad udp cksum 490d!] 37508+ PTR? 1.2.168.192.in-addr.arpa. (42)
        0x0000:  4500 0046 9431 4000 4011 205b c0a8 0265
        0x0010:  c0a8 0265 c691 0035 0032 865e 9284 0100
        0x0020:  0001 0000 0000 0000 0131 0132 0331 3638
        0x0030:  0331 3932 0769 6e2d 6164 6472 0461 7270
        0x0040:  6100 000c 0001
11:02:19.625527 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 70) fs1.11226 > mymodem.domain: [bad udp cksum 8100!] 15052+ PTR? 1.2.168.192.in-addr.arpa. (42)
        0x0000:  4500 0046 0000 4000 4011 b4f0 c0a8 0265
        0x0010:  c0a8 0201 2bda 0035 0032 85fa 3acc 0100
        0x0020:  0001 0000 0000 0000 0131 0132 0331 3638
        0x0030:  0331 3932 0769 6e2d 6164 6472 0461 7270
        0x0040:  6100 000c 0001
11:02:19.636329 IP (tos 0x0, ttl 255, id 35399, offset 0, flags [DF], proto UDP (17), length 197) mymodem.domain > fs1.11226: [udp sum ok] 15052* q: PTR? 1.2.168.192.in-addr.arpa. 1/1/1 1.2.168.192.in-addr.arpa. PTR mymodem. ns: 1.2.168.192.in-addr.arpa. NS homeportal.gateway.2wire.net. ar: homeportal.gateway.2wire.net. A mymodem (169)
        0x0000:  4500 00c5 8a47 4000 ff11 6b29 c0a8 0201
        0x0010:  c0a8 0265 0035 2bda 00b1 1e93 3acc 8580
        0x0020:  0001 0001 0001 0001 0131 0132 0331 3638
        0x0030:  0331 3932 0769 6e2d 6164 6472 0461 7270
        0x0040:  6100 000c 0001 0131 0132 0331 3638 0331
        0x0050:  3932 0769 6e2d 6164 6472 0461 7270 6100
        0x0060:  000c 0001 0002 a300 0009 076d 796d 6f64
        0x0070:  656d 0001 3101 3203 3136 3803 3139 3207
        0x0080:  696e 2d61 6464 7204 6172 7061 0000 0200
        0x0090:  0100 00a3 0000 1e0a 686f 6d65 706f 7274
        0x00a0:  616c 0767 6174 6577 6179 0532 7769 7265
        0x00b0:  036e 6574 00c0 7b00 0100 0100 00a3 0000
        0x00c0:  04c0 a802 01
11:02:19.638892 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 149) fs1.domain > fs1.50833: [bad udp cksum a14e!] 37508 q: PTR? 1.2.168.192.in-addr.arpa. 1/1/1 1.2.168.192.in-addr.arpa. PTR mymodem. ns: 1.2.168.192.in-addr.arpa. NS homeportal.gateway.2wire.net. ar: homeportal.gateway.2wire.net. A mymodem (121)
        0x0000:  4500 0095 0000 4000 4011 b43d c0a8 0265
        0x0010:  c0a8 0265 0035 c691 0081 86ad 9284 8180
        0x0020:  0001 0001 0001 0001 0131 0132 0331 3638
        0x0030:  0331 3932 0769 6e2d 6164 6472 0461 7270
        0x0040:  6100 000c 0001 c00c 000c 0001 0002 a300
        0x0050:  0009 076d 796d 6f64 656d 00c0 0c00 0200
        0x0060:  0100 00a3 0000 1e0a 686f 6d65 706f 7274
        0x0070:  616c 0767 6174 6577 6179 0532 7769 7265
        0x0080:  036e 6574 00c0 4b00 0100 0100 00a0 b800
        0x0090:  04c0 a802 01


---

### Post by jonobr on 2009-06-26
HEllo

Heres a comment and then a stupid (your guide link I cant get to for some reason?)

The tcpdump is showing your packets are going to the dns for resolution of one name and not another.

I am wondering if there is something in the hosts file thats mapping to an address.

If the dns doesnt go out, it either can resolve it in hosts, or there is an error in the desktop,

The stupid comment is that in your very first example your pings resolve to a 172, and in your later ones your using 192s. Is the right?

---

### Post by omro on 2009-06-26
Ah, well spotted. The test server is in a virtual machine on a laptop. In the office I had the static IP set to the office network and at home I had the static IP set to my home network.

ubuntuforums.org/showthread.php?t=640760

is the guide.

Thanks!

---

### Post by omro on 2009-06-27
See, I'm pretty sure I set up the ubuntu server correctly. When, admittedly on itself, I issue the following command:

> dig fs1.mydomain.com.local

; <<>> DiG 9.4.2-P2 <<>> fs1.mydomain.com.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 218
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;fs1.mydomain.com.local.     IN      A

;; ANSWER SECTION:
fs1.mydomain.com.local. 38400 IN     A       192.168.2.101

;; AUTHORITY SECTION:
mydomain.com.local.      38400   IN      NS      fs1.mydomain.com.local.

;; Query time: 15 msec
;; SERVER: 192.168.2.101#53(192.168.2.101)
;; WHEN: Fri Jun 26 18:38:04 2009
;; MSG SIZE  rcvd: 73

sysadmin@fs1:~$ ping -w 3 fs1.mydomain.com.local
PING fs1.mydomain.com.local (192.168.2.101) 56(84) bytes of data.
64 bytes from fs1.mydomain.com.local (192.168.2.101): icmp_seq=1 ttl=64 time=0.142 ms
64 bytes from fs1.mydomain.com.local (192.168.2.101): icmp_seq=2 ttl=64 time=0.060 ms
64 bytes from fs1.mydomain.com.local (192.168.2.101): icmp_seq=3 ttl=64 time=0.058 ms
Warning: time of day goes back (-268us), taking countermeasures.
64 bytes from fs1.mydomain.com.local (192.168.2.101): icmp_seq=4 ttl=64 time=0.622 ms

--- fs1.mydomain.com.local ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.058/0.220/0.622/0.234 ms



I get decent output.

The same command on the ubuntu desktop machine also gives decent output, but I can't ping it!

> dig fs1.mydomain.com.local

; <<>> DiG 9.5.1-P2 <<>> fs1.mydomain.com.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37181
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;fs1.mydomain.com.local.	IN	A

;; ANSWER SECTION:
fs1.mydomain.com.local. 38400 IN	A	192.168.2.101

;; AUTHORITY SECTION:
mydomain.com.local.	38400	IN	NS	fs1.mydomain.com.local.

;; Query time: 26 msec
;; SERVER: 192.168.2.101#53(192.168.2.101)
;; WHEN: Fri Jun 26 23:38:35 2009
;; MSG SIZE  rcvd: 73

me@adventubuntu:~$ ping -w 3 fs1.mydomain.com.local
ping: unknown host fs1.mydomain.com.local

me@adventubuntu:~$ dig fs1

; <<>> DiG 9.5.1-P2 <<>> fs1
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60161
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;fs1.			IN	A

;; ANSWER SECTION:
fs1.		0	IN	A	192.168.2.19

;; AUTHORITY SECTION:
fs1.		41728	IN	NS	homeportal.gateway.2wire.net.

;; ADDITIONAL SECTION:
homeportal.gateway.2wire.net. 41728 IN	A	192.168.2.1

;; Query time: 135 msec
;; SERVER: 192.168.2.101#53(192.168.2.101)
;; WHEN: Fri Jun 26 23:45:00 2009
;; MSG SIZE  rcvd: 99

me@adventubuntu:~$ ping -w 3 fs1
PING fs1.mydomain.com.local (192.168.2.101) 56(84) bytes of data.
64 bytes from 192.168.2.101: icmp_seq=1 ttl=64 time=5.08 ms

--- fs1.mydomain.com.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 5.088/5.088/5.088/0.000 ms


---

### Post by omro on 2009-06-29
I've spent the weekend googling and I'm none the wiser.

If anyone can recommend a way I can check and see if the DNS issue is how I set up BIND on the server or how I connected the client desktop to the server, I'd be grateful.

Thanks

---

### Post by omro on 2009-06-29
There must be a diagnostic tool I can use, perhaps?

---

### Post by jonobr on 2009-06-29
mmmm... from your last resonse, I thought this was resolved.

On your client machine could you run a tcpdump again?

This time try

```
sudo tcpdump -w trace1.pcap -i any port 53
```

do the pping that works,
post the results here

then 
```
sudo tcpdump -w trace2.pcap -i any port 53
```

and do the one that doesnt work.

the files should be small

---

### Post by omro on 2009-06-29
sorry, I thought my last response showed that...

the desktop ubuntu machine can see fs1 as fs1, but not as fs1.mydomain.com.local

however the server can see itself both ways.

I'll try those suggestions. Thanks.

---

### Post by omro on 2009-06-30
> **jonobr said:**
> mmmm... from your last resonse, I thought this was resolved.

On your client machine could you run a tcpdump again?

This time try

```
sudo tcpdump -w trace1.pcap -i any port 53
```

do the pping that works,
post the results here

then 
```
sudo tcpdump -w trace2.pcap -i any port 53
```

and do the one that doesnt work.

the files should be small

I ran this on the client desktop machine and all it said was:

> listening on any, link-type LINUX_SSL (Linux cooked), capture size 96 bytes

No clue what to do next :lolflag:

---

### Post by 4o66 on 2009-07-01
Turn off the avahi-daemon. This worked for me just now, with the same situation. Found the clue here:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7398769](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7398769)

Apparently, the avahi is for network service discovery. Why it would disable name resolution, I am not sure.

PS: fastest way to shut it down:
```
sudo /etc/init.d/avahi-daemon stop
sudo update-rc.d -f avahi-daemon remove
```

---

### Post by omro on 2009-07-02
> **4o66 said:**
> Turn off the avahi-daemon. This worked for me just now, with the same situation. Found the clue here:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7398769](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7398769)

Apparently, the avahi is for network service discovery. Why it would disable name resolution, I am not sure.

PS: fastest way to shut it down:
```
sudo /etc/init.d/avahi-daemon stop
sudo update-rc.d -f avahi-daemon remove
```

Thank you so much, 4o66 that fixed it!! :KS

Thank you too jonobr.

---

