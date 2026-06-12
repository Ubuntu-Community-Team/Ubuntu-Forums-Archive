---
title: "VirtualBox: ping gives &quot;DUP!&quot; with Bridged wifi interface"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by sanderj on 2012-02-26
I'm running VirtualBox 4.1.8 on Ubuntu 64-bit, which is connected to the the network via wireless adapter WLAN0. 

I'm running another Ubuntu as a VM on VirtualBox with "Bridged Adapter" via  WLAN0, and it has some network problems:
1) ping results in "(DUP!)" messages as seen below
2) the Ubuntu guest does get a public IPv6 address from the modem, but IPv6 doesn't work

When I switch the host system to fixed ethernet and disable wifi, the problem is gone: ping works normal, IPv6 works.

Problem seems related to [https://forums.virtualbox.org/viewtopic.php?f=7&t=45886](https://forums.virtualbox.org/viewtopic.php?f=7&t=45886) which has no solution.

Any tips?


```

sander@sander-VirtualBox:~$ ping ping.xs4all.nl
PING uucp1.xs4all.nl (194.109.21.51) 56(84) bytes of data.
64 bytes from uucp1.xs4all.nl (194.109.21.51): icmp_req=1 ttl=59 time=22.8 ms
64 bytes from uucp1.xs4all.nl (194.109.21.51): icmp_req=1 ttl=58 time=23.0 ms (DUP!)
64 bytes from uucp1.xs4all.nl (194.109.21.51): icmp_req=2 ttl=59 time=20.2 ms
64 bytes from uucp1.xs4all.nl (194.109.21.51): icmp_req=2 ttl=58 time=20.3 ms (DUP!)
^C
--- uucp1.xs4all.nl ping statistics ---
2 packets transmitted, 2 received, +2 duplicates, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 20.254/21.612/23.022/1.342 ms
sander@sander-VirtualBox:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_req=1 ttl=64 time=15.9 ms
64 bytes from 192.168.1.254: icmp_req=1 ttl=63 time=16.0 ms (DUP!)
64 bytes from 192.168.1.254: icmp_req=2 ttl=64 time=5.10 ms
64 bytes from 192.168.1.254: icmp_req=2 ttl=63 time=5.27 ms (DUP!)
^C
--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, +2 duplicates, 0% packet loss, time 1006ms
rtt min/avg/max/mdev = 5.105/10.578/16.027/5.391 ms
sander@sander-VirtualBox:~$

```

---

### Post by yss8166 on 2012-02-26
I have the exact same problem , the Host system is ubuntu 11.10 and the guest is ubuntu server 10.04 .!

it was running fine before one week ago , but today I saw the error and the internet inside the VM is really slow

---

### Post by sanderj on 2012-03-02
FWIW:

The real problem for me is that IPv6 is half / not working: The guest does get an IPv6 address from the router/modem on the LAN, but IPv6 is not working. See below.


```

Stateful address conf.    :           No
Stateful other conf.      :          Yes
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :        30000 (0x00007530) milliseconds
Retransmit time           :  unspecified (0x00000000)
 Prefix                   : 2a00:cd8:5288::/64
  Valid time              :      2592000 (0x00278d00) seconds
  Pref. time              :       604800 (0x00093a80) seconds
 MTU                      :         1480 bytes (valid)
 Source link-layer address: 50:67:F0:D7:69:0B
 from fe80::5267:f0ff:fed7:690b
sander@sander-VirtualBox:~$ 


sander@sander-VirtualBox:~$ wget www.xs4all.nl
--2012-03-02 09:13:58--  http://www.xs4all.nl/
Resolving www.xs4all.nl (www.xs4all.nl)... 2001:888:0:18::80, 194.109.6.92
Connecting to www.xs4all.nl (www.xs4all.nl)|2001:888:0:18::80|:80... failed: No route to host.
Connecting to www.xs4all.nl (www.xs4all.nl)|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 17,598      --.-K/s   in 0.05s   

2012-03-02 09:14:06 (314 KB/s) - `index.html' saved [17598]

sander@sander-VirtualBox:~$

sander@sander-VirtualBox:~$ ping6 ipv6.google.com
PING ipv6.google.com(ey-in-x69.1e100.net) 56 data bytes
From 2a00:cd8:5288::27ff:fec4:5758 icmp_seq=1 Destination unreachable: Address unreachable
From 2a00:cd8:5288::27ff:fec4:5758 icmp_seq=2 Destination unreachable: Address unreachable
From 2a00:cd8:5288::27ff:fec4:5758 icmp_seq=3 Destination unreachable: Address unreachable
^C
--- ipv6.google.com ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4371ms

sander@sander-VirtualBox:~$

```

---

