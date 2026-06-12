---
title: "No dns on 5.10"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by subpt on 2006-02-04
So, I installed Ubuntu 5.10 on my Toshiba M30-861 this afternoon and it all went smooth. The problem is, I have my network completely configured, I can ping inside&outside my network but i cant resolve web adresses. I'm thinking it's ubuntu's prbolem since i double-checked the dns ip's with both a windows install on the same network and the ones my router shows up.

ill edit this post shortly to show several diags from the lap ^^

thanks in advance

edit:
```
root@ubuntosh:/home/sub# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1

```

```
root@ubuntosh:/home/sub# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0C:F1:34:0B:4B
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1960 errors:11 dropped:0 overruns:0 frame:0
          TX packets:1367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1073805 (1.0 MiB)  TX bytes:161455 (157.6 KiB)
          Interrupt:11 Base address:0x4000 Memory:c2005000-c2005fff


```

```
root@ubuntosh:/home/sub# tail /etc/resolv.conf
search netvisao.pt
nameserver 213.228.128.99
nameserver 213.228.128.6

```

```
root@ubuntosh:/home/sub# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.09 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.78 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=4.39 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 2.782/3.425/4.395/0.699 ms

```

```
root@ubuntosh:/home/sub# ping ubuntuforums.org
PING www.ubuntuforums.org (64.21.33.9) 56(84) bytes of data.
64 bytes from www.ubuntuforums.org (64.21.33.9): icmp_seq=1 ttl=50 time=120 ms
64 bytes from www.ubuntuforums.org (64.21.33.9): icmp_seq=2 ttl=50 time=128 ms
64 bytes from www.ubuntuforums.org (64.21.33.9): icmp_seq=3 ttl=50 time=132 ms
64 bytes from www.ubuntuforums.org (64.21.33.9): icmp_seq=4 ttl=50 time=117 ms

--- www.ubuntuforums.org ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4004ms

```
(i added the board's ip manually to post all this stuff)
```

```

---

### Post by mips on 2006-02-04
Disable IPv6

---

### Post by lcg on 2006-02-04
[QUOTE=subpt]So, I installed Ubuntu 5.10 on my Toshiba M30-861 this afternoon and it all went smooth. The problem is, I have my network completely configured, I can ping inside&outside my network but i cant resolve web adresses.[/QUOTE]
Actually, your Ubuntu can resolve DNS names. Otherwise, you wouldn't have been able to ping ubuntuforums.org as you did below (see the IP address in bold).

[QUOTE=subpt]
```
root@ubuntosh:/home/sub# ping ubuntuforums.org
PING www.ubuntuforums.org (**64.21.33.9**) 56(84) bytes of data.
...
```
(i added the board's ip manually to post all this stuff)
[/QUOTE]
If your browser doesn't resolve names, that is something different. Try a different browser or even 'wget ubuntuforums.org' and see what that does.

HTH,
Lars

---

### Post by 111787 on 2006-02-04
'route add default gw 192.168.1.1 metric 1'
I had the same problem, the route to outside the network isn't right.

---

### Post by Lambert on 2006-02-04
[quote=111787]'route add default gw 192.168.1.1 metric 1'
I had the same problem, the route to outside the network isn't right.[/quote]

Interesting, can you explain what this does, man page didn't give a whole lot of information.

---

### Post by 111787 on 2006-02-04
He most likely has the setup of Computer - Router - Modem - Internet.  Ubuntu doesnt recognize that and it thinks the modem is the internet, 'route add default gw 192.168.1.1 metric 1' fixes the route so it takes an additional hop so it gets to the internet.

---

### Post by vulpine on 2006-02-12
thank you, the metric was what i was missing!

i had been having problems at home with my static settings but everything worked when set to dhcp at another ap
i could ping the router at home but no go outside of local 
thanks

---

