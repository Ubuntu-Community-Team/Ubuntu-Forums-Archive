---
title: "Unusual inbound traffic??"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2010-05-08
I saw a spike in the resources being used in the system monitor and noticed a few spikes in network traffic. This concerned me so I looked at dmesg, and this is what I received:```
[1621095.225465] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=92.238.172.144 DST=192.168.1.100 LEN=61 TOS=0x00 PREC=0x00 TTL=115 ID=9145 PROTO=UDP SPT=28925 DPT=61510 LEN=41 
[1621096.557723] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=115.177.91.166 DST=192.168.1.100 LEN=129 TOS=0x00 PREC=0x20 TTL=111 ID=15988 PROTO=UDP SPT=23999 DPT=61510 LEN=109 
[1621097.727187] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=90.17.226.145 DST=192.168.1.100 LEN=52 TOS=0x00 PREC=0x20 TTL=107 ID=29431 DF PROTO=TCP SPT=65391 DPT=61510 WINDOW=8192 RES=0x00 SYN URGP=0 
[1621098.037933] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=95.106.29.37 DST=192.168.1.100 LEN=131 TOS=0x00 PREC=0x00 TTL=117 ID=5982 PROTO=UDP SPT=57006 DPT=61510 LEN=111 
[1621098.300347] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=92.238.172.144 DST=192.168.1.100 LEN=61 TOS=0x00 PREC=0x00 TTL=115 ID=9727 PROTO=UDP SPT=28925 DPT=61510 LEN=41 
[1621100.722469] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=90.17.226.145 DST=192.168.1.100 LEN=52 TOS=0x00 PREC=0x20 TTL=107 ID=29710 DF PROTO=TCP SPT=65391 DPT=61510 WINDOW=8192 RES=0x00 SYN URGP=0 
[1621103.887793] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=211.1.219.223 DST=192.168.1.100 LEN=129 TOS=0x00 PREC=0x00 TTL=109 ID=46940 PROTO=UDP SPT=12887 DPT=61510 LEN=109 
[1621103.894759] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=87.231.105.154 DST=192.168.1.100 LEN=131 TOS=0x00 PREC=0x20 TTL=119 ID=15186 PROTO=UDP SPT=57797 DPT=61510 LEN=111 
[1621104.462745] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=92.238.172.144 DST=192.168.1.100 LEN=61 TOS=0x00 PREC=0x00 TTL=115 ID=10689 PROTO=UDP SPT=28925 DPT=61510 LEN=41 
[1621106.727711] Inbound IN=wlan0 OUT= MAC=00:19:7e:66:e0:e7:00:13:10:10:08:c3:08:00 SRC=90.17.226.145 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=30390 DF PROTO=TCP SPT=65391 DPT=61510 WINDOW=8192 RES=0x00 SYN URGP=0 

```

This just looks odd. I looked up a few ips and they areall over the map. What does this all mean?

---

### Post by therjnel on 2010-05-08
The strange thing is that all of those IP addresses are attempting to connect via port 61510.  Have you installed an application recently, perhaps a MMOG that might require that port for some kind of communication?

---

### Post by lsutiger on 2010-05-08
Hmmm...no I haven't installed anything lately. The machine I am on has been steady crusing since I installed 9.04.

I looked up port 61510. This is what I found via google:
[http://isc.sans.org/port.html?port=61510](http://isc.sans.org/port.html?port=61510)

There definitely is not a lot of info for that port.

I ran firestarter to see the activity and all of the requests on that port are being blocked.

I attached the result of a ps -ejH to see if someone can help me see if I have some program/process running that would ask for such communication.

---

### Post by itsjareds on 2010-05-08
This command lists all programs that have a connection or are listening:

```
netstat -pant
```

Maybe this will turn up something interesting?

---

### Post by lsutiger on 2010-05-08
Thanx for the replies! 

Here's what I have done.

Blocked access to that port on the router- no dice
Forwarded the port to a non existent IP - no dice
Tried to get a new WAN IP by release/renew on router - no dice
changed my LAN IP to .101 (vs 100)...fixed!. 
Let me try going back to 100 and running netstat.

---

### Post by lsutiger on 2010-05-08
OK, changed IP back to .100, and the inbound request come again.
sudo netstat -pant doesn't have port 61510 listed

---

### Post by itsjareds on 2010-05-08
Maybe check UDP too with `netstat -pantu` .. some of those requests are coming from udp

---

### Post by lsutiger on 2010-05-08
OK, reset IP again to .100, verified the incoming requests. ran netstat -pantu.
Under the udp ports, 61510 is not listed.

Thanx for your help anyway!

---

### Post by lsutiger on 2010-05-13
(This is from another post [here]("http://ubuntuforums.org/showthread.php?t=1479081")
This is on my office machine, but same subject.

New and intriguing information. I ran dmesg this morning. Here is the end of it:```
[168125.388842] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.123 DST=239.255.255.250 LEN=172 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=47349 DPT=1900 LEN=152 
[168125.388866] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.123 DST=239.255.255.250 LEN=172 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=47349 DPT=1900 LEN=152 
[168125.388881] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.123 DST=239.255.255.250 LEN=172 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=47349 DPT=1900 LEN=152 
[168449.845003] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=437 TOS=0x00 PREC=0x00 TTL=1 ID=17955 PROTO=UDP SPT=1900 DPT=1900 LEN=417 
[168450.146737] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=384 TOS=0x00 PREC=0x00 TTL=1 ID=17957 PROTO=UDP SPT=1900 DPT=1900 LEN=364 
[168450.269692] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=375 TOS=0x00 PREC=0x00 TTL=1 ID=17959 PROTO=UDP SPT=1900 DPT=1900 LEN=355 
[168450.271808] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=443 TOS=0x00 PREC=0x00 TTL=1 ID=17961 PROTO=UDP SPT=1900 DPT=1900 LEN=423 
[168450.531409] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=384 TOS=0x00 PREC=0x00 TTL=1 ID=17963 PROTO=UDP SPT=1900 DPT=1900 LEN=364 
[168450.986748] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=423 TOS=0x00 PREC=0x00 TTL=1 ID=17965 PROTO=UDP SPT=1900 DPT=1900 LEN=403 
[168452.158683] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=447 TOS=0x00 PREC=0x00 TTL=1 ID=17967 PROTO=UDP SPT=1900 DPT=1900 LEN=427 
[168452.278476] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=429 TOS=0x00 PREC=0x00 TTL=1 ID=17969 PROTO=UDP SPT=1900 DPT=1900 LEN=409 
[168452.303083] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=455 TOS=0x00 PREC=0x00 TTL=1 ID=17971 PROTO=UDP SPT=1900 DPT=1900 LEN=435 
[168452.764899] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=384 TOS=0x00 PREC=0x00 TTL=1 ID=17973 PROTO=UDP SPT=1900 DPT=1900 LEN=364 
[168452.850751] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=437 TOS=0x00 PREC=0x00 TTL=1 ID=17975 PROTO=UDP SPT=1900 DPT=1900 LEN=417 
[168453.152602] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=384 TOS=0x00 PREC=0x00 TTL=1 ID=17977 PROTO=UDP SPT=1900 DPT=1900 LEN=364 
[168453.275728] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=375 TOS=0x00 PREC=0x00 TTL=1 ID=17979 PROTO=UDP SPT=1900 DPT=1900 LEN=355 
[168453.277519] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=443 TOS=0x00 PREC=0x00 TTL=1 ID=17981 PROTO=UDP SPT=1900 DPT=1900 LEN=423 
[168453.537291] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=384 TOS=0x00 PREC=0x00 TTL=1 ID=17983 PROTO=UDP SPT=1900 DPT=1900 LEN=364 
[168453.992451] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=423 TOS=0x00 PREC=0x00 TTL=1 ID=17985 PROTO=UDP SPT=1900 DPT=1900 LEN=403 
[168455.164345] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=447 TOS=0x00 PREC=0x00 TTL=1 ID=17987 PROTO=UDP SPT=1900 DPT=1900 LEN=427 
[168455.284359] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=429 TOS=0x00 PREC=0x00 TTL=1 ID=17989 PROTO=UDP SPT=1900 DPT=1900 LEN=409 
[168455.308816] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=455 TOS=0x00 PREC=0x00 TTL=1 ID=17991 PROTO=UDP SPT=1900 DPT=1900 LEN=435 
[168455.770722] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=384 TOS=0x00 PREC=0x00 TTL=1 ID=17993 PROTO=UDP SPT=1900 DPT=1900 LEN=364 
[168455.856667] Inbound IN=eth0 OUT= MAC=01:00:5e:7f:ff:fa:00:1d:09:b7:a3:aa:08:00 SRC=192.168.1.119 DST=239.255.255.250 LEN=437 TOS=0x00 PREC=0x00 TTL=1 ID=17995 PROTO=UDP SPT=1900 DPT=1900 LEN=417
```

One interesting point, 192.168.1.119 is not my IP. From ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:cb:87:de  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:fecb:87de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50062642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65777498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24944212 (24.9 MB)  TX bytes:2474076814 (2.4 GB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:279484 (279.4 KB)  TX bytes:279484 (279.4 KB)
```
The second interesting fact, the destination IP is a reserved block and owned by the IANA
[http://www.faqs.org/rfcs/rfc3171.html](http://www.faqs.org/rfcs/rfc3171.html)

---

