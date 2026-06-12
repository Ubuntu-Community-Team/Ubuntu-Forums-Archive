---
title: "ERROR: Connection dropped by IMAP server."
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by wlee1970 on 2013-04-05
Hi, i have looked through the forums and still didn't find the answer to the question, when i log into squirrelmail i get the imap error, I ran a 
[https://192.168.1.106/squirrelmail/src/configtest.php](https://192.168.1.106/squirrelmail/src/configtest.php)

and got this error on the next page:

"Secure Connection Failed

 An error occurred during a connection to 192.168.1.106.

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)"
---------------------------------------------------------------------------------------------------------------------------
This is what i got trying to login into squirrelmail

also i ran tail -n 15 /var/log/mail.log
I recieved this error: 

Apr  5 14:15:43 box420 postfix/smtps/smtpd[19845]: disconnect from localhost.localdomain[127.0.0.1]
Apr  5 14:21:10 box420 dovecot: imap-login: Login: user=<cid>, method=PLAIN, rip=192.168.1.106, lip=192.168.1.106, mpid=19856, secured
Apr  5 14:21:10 box420 dovecot: imap(cid): Error: user cid: Initialization failed: mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/cid
Apr  5 14:21:10 box420 dovecot: imap(cid): Error: Invalid user settings. Refer to server log for more information.
Apr  5 14:25:43 box420 postfix/smtps/smtpd[19858]: connect from localhost.localdomain[127.0.0.1]
Apr  5 14:30:43 box420 postfix/smtps/smtpd[19858]: SSL_accept error from localhost.localdomain[127.0.0.1]: Connection timed out
Apr  5 14:30:43 box420 postfix/smtps/smtpd[19858]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Apr  5 14:30:43 box420 postfix/smtps/smtpd[19858]: disconnect from localhost.localdomain[127.0.0.1]
Apr  5 14:40:43 box420 postfix/smtps/smtpd[19882]: connect from localhost.localdomain[127.0.0.1]
Apr  5 14:43:50 box420 dovecot: imap-login: Login: user=<cid>, method=PLAIN, rip=192.168.1.106, lip=192.168.1.106, mpid=19900, secured
Apr  5 14:43:50 box420 dovecot: imap(cid): Error: user cid: Initialization failed: mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/cid
Apr  5 14:43:50 box420 dovecot: imap(cid): Error: Invalid user settings. Refer to server log for more information.
Apr  5 14:45:43 box420 postfix/smtps/smtpd[19882]: SSL_accept error from localhost.localdomain[127.0.0.1]: Connection timed out
Apr  5 14:45:43 box420 postfix/smtps/smtpd[19882]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Apr  5 14:45:43 box420 postfix/smtps/smtpd[19882]: disconnect from localhost.localdomain[127.0.0.1]


Just looking for help guys please.

PS. i am getting the IMAP connection error also. please help thanks.

Thanks,
wlee1970

---

### Post by praseodym on 2013-04-05
Hi,

how do you connect? Cable? Wireless? Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
ping -c 4 192.168.1.1
ping -c 4 www.ubuntuusers.de
ping -c 4 213.95.41.11
```

---

### Post by wlee1970 on 2013-04-05
> **praseodym said:**
> Hi,

how do you connect? Cable? Wireless? Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
ping -c 4 192.168.1.1
ping -c 4 www.ubuntuusers.de
ping -c 4 213.95.41.11
```


I connect with cat5e i run multiple routers in the house.

---

### Post by wlee1970 on 2013-04-05
Hope this helps

 lspci -nnk | grep -ia2 net

Kernel driver in use: snd_intel8x0
Kernel modules: snd-intel8x0
03:09.0 Ethernet controller [0200]: Davicom Semiconductor, Inc. Ethernet 100/10 MBit [1282:9009] (rev 31)
Subsystem: ARCHTEK TELECOM Corp Device [14fe:0008]

lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory

 lsmod

Module                  Size  Used by
ip6table_filter        12711  0
ip6_tables             22528  1 ip6table_filter
xt_multiport           12533  3
iptable_filter         12706  1
ip_tables              18106  1 iptable_filter
x_tables               21974  5 ip6table_filter,ip6_tables,xt_multiport,iptable_filter,ip_tables
ppdev                  12849  0
snd_intel8x0           33455  0
snd_ac97_codec        106082  1 snd_intel8x0
i915                  414603  1
ac97_bus               12642  1 snd_ac97_codec
drm_kms_helper         45466  1 i915
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_timer              28931  1 snd_pcm
shpchp                 32325  0
drm                   197692  2 i915,drm_kms_helper
psmouse                72846  0
serio_raw              13027  0
i2c_algo_bit           13199  1 i915
snd                    62064  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore              14635  1 snd
joydev                 17393  0
lp                     17455  0
video                  19068  1 i915
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
mac_hid                13077  0
parport_pc             32114  1
parport                40930  3 ppdev,lp,parport_pc
dmfe                   22990  0
usbhid                 41906  0
hid                    77367  1 usbhid
floppy                 60310  0

 ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:01:53:81:52:e4
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:53ff:fe81:52e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:195187872 (195.1 MB)  TX bytes:10356717 (10.3 MB)
          Interrupt:21 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:156327 (156.3 KB)  TX bytes:156327 (156.3 KB)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

cat /etc/resolv.conf

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4

ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.624 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=0.425 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=0.428 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=0.433 ms

 ping -c 4 [www.ubuntuusers.de](www.ubuntuusers.de)
PING ubuntuusers.de (213.95.41.13) 56(84) bytes of data.
64 bytes from lisa.ubuntu-eu.org (213.95.41.13): icmp_req=1 ttl=49 time=108 ms
64 bytes from lisa.ubuntu-eu.org (213.95.41.13): icmp_req=2 ttl=49 time=109 ms
64 bytes from lisa.ubuntu-eu.org (213.95.41.13): icmp_req=3 ttl=49 time=114 ms
64 bytes from lisa.ubuntu-eu.org (213.95.41.13): icmp_req=4 ttl=49 time=109 ms

--- ubuntuusers.de ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 108.804/110.631/114.966/2.526 ms

 ping -c 4 213.95.41.11
PING 213.95.41.11 (213.95.41.11) 56(84) bytes of data.
64 bytes from 213.95.41.11: icmp_req=1 ttl=49 time=107 ms
64 bytes from 213.95.41.11: icmp_req=2 ttl=49 time=119 ms
64 bytes from 213.95.41.11: icmp_req=3 ttl=49 time=107 ms
64 bytes from 213.95.41.11: icmp_req=4 ttl=49 time=108 ms

--- 213.95.41.11 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 107.381/110.852/119.884/5.233 ms

---

### Post by wlee1970 on 2013-04-05
I just do not quite understand why you need my connectivity since this is a mail issue.

Thanks 
Wlee1970

---

### Post by praseodym on 2013-04-05
mtu value and nameservers are Ok. Do you need the firewall? Deactivate the iptables:
```

sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by wlee1970 on 2013-04-07
This is a great place to get help. this guy telling me to do other things except answer my mail question.

---

### Post by praseodym on 2013-04-07
Maybe the firewall blocks the connection

---

