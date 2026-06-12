---
title: "Please help I've broke my Openvpn"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by marcus178 on 2009-10-08
I did something which broke my VPN set up. I tried starting over again but if I run

openvpn /etc/openvpn/server.conf

i get this error

```
Thu Oct  8 18:07:05 2009 OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May  8 2009
Thu Oct  8 18:07:05 2009 Diffie-Hellman initialized with 1024 bit key
Thu Oct  8 18:07:05 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Thu Oct  8 18:07:05 2009 TLS-Auth MTU parms [ L:1590 D:138 EF:38 EB:0 ET:0 EL:0 ]
Thu Oct  8 18:07:05 2009 TCP/UDP: Socket bind failed on local address [undef]:1194: Address already in use
Thu Oct  8 18:07:05 2009 Exiting

```

I've even tried changing the port in server.conf but I just get the same error with the new port number. I've been trying all day to fix it and I'm completely stuck now.

---

### Post by sedawk on 2009-10-08
There are two things I see:

1) Address in use
This means there is still a process running using that address.
You can try tool "lsof" (or netstat) to detect which process
is using it.
Worst case scenario: reboot once! But that shouldn't be
necessary anyway.

2) undef
This might be totally okay, but I would feel more comfortable
if it said something like "localhost" or you own hostname ...

---

### Post by marcus178 on 2009-10-08
I was hoping I be able to remote ssh but looks as if that's not working anymore either.

when I've done netstat earlier the only process running were relating to openvpn but there were 3 different results. Unfortunately can't get that info at the moment and won;t be back in work for another 12 hours.

Is there any way of stopping everything that is running on that port.

I'm really confused I've had this VPN working for months now and it all gone a bit wrong,

I don't think undef is a problem as it did the same with localhost defined.

---

### Post by marcus178 on 2009-10-09
ok if I run lsof -i:1194 i get

```
COMMAND   PID USER   FD   TYPE DEVICE SIZE NODE NAME
openvpn 11315 root    4u  IPv4  28969       UDP *:openvpn 

```

so i did kill -9 11315 which cleared that.

Then if I do openvpn /etc/openvpn/server.conf

I get 

```
Fri Oct  9 09:00:49 2009 OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May  8 2009
Fri Oct  9 09:00:49 2009 Diffie-Hellman initialized with 1024 bit key
Fri Oct  9 09:00:49 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri Oct  9 09:00:49 2009 TLS-Auth MTU parms [ L:1590 D:138 EF:38 EB:0 ET:0 EL:0 ]
Fri Oct  9 09:00:49 2009 TUN/TAP device tap0 opened
Fri Oct  9 09:00:49 2009 TUN/TAP TX queue length set to 100
Fri Oct  9 09:00:49 2009 Data Channel MTU parms [ L:1590 D:1450 EF:58 EB:135 ET:32 EL:0 AF:3/1 ]
Fri Oct  9 09:00:49 2009 Socket Buffers: R=[111616->131072] S=[111616->131072]
Fri Oct  9 09:00:49 2009 UDPv4 link local (bound): [undef]:1194
Fri Oct  9 09:00:49 2009 UDPv4 link remote: [undef]
Fri Oct  9 09:00:49 2009 MULTI: multi_init called, r=256 v=256
Fri Oct  9 09:00:49 2009 IFCONFIG POOL: base=192.168.1.180 size=21
Fri Oct  9 09:00:49 2009 Initialization Sequence Completed

```

which suggests it working but if i run it again the original error returns and running lsof shows that the is only one process

---

### Post by marcus178 on 2009-10-09
OK I found it's something to do with DHCP3-server, uninstalling this has fixed the problem.

I would still like to know why this was happening though.

---

