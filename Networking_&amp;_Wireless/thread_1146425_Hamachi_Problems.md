---
title: "Hamachi Problems"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by melefire on 2009-05-02
I set up Hamachi and a GUI and every thing seemed to go well. But now i cannot ping or access any other computers in my hamachi network. Every time I try I get a destination host unreachable error. Any Ideas?

thanks

---

### Post by trigsenior on 2009-05-26
have exactly same problem running ubuntu 8.04.

---

### Post by superprash2003 on 2009-05-26
check to see if iptables it blocking , post output of sudo iptables -L

---

### Post by Mononofu on 2009-05-26
I have a similar problem: I can't even login anymore.

However, I could play fine before - it all happened about a week ago, while I was playing a game of DotA. Suddenly, I was disconnected and couldn't reconnect, and I still can't.

I've deleted my configuration, reinstalled hamachi, checked iptables, just about anything. I know it isn't a problem with my network since on Windows XP, I can play just fine.

Any ideas what could have caused this?

"route -n":
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

"ifconfig":
```
ham0      Link encap:Ethernet  HWaddr 3a:0f:fd:43:6d:40
          inet addr:5.136.146.165  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:2230 (2.2 KB)

```

---

### Post by superprash2003 on 2009-05-27
are you sure?? your hamachi interface has an ip 5.x.x.x

---

### Post by Mononofu on 2009-05-27
Yes, I am sure, why?

I also tried [this]("http://ubuntuforums.org/showpost.php?p=3849250&postcount=11"), but it didn't help. (my local network also has 0.0.0.0 as gateway, and it's always reset to this value when restarting hamachi)

---

### Post by superprash2003 on 2009-05-27
your ifconfig shows a hamachi ip 5.x.x.x which means it is already connected.. are you able to ping that ip?

---

### Post by Mononofu on 2009-05-27
Yes, I can ping it:

```
mononofu@mononofu-laptop:~$ ping 5.136.146.165
PING 5.136.146.165 (5.136.146.165) 56(84) bytes of data.
64 bytes from 5.136.146.165: icmp_seq=1 ttl=64 time=0.033 ms
64 bytes from 5.136.146.165: icmp_seq=2 ttl=64 time=0.030 ms
64 bytes from 5.136.146.165: icmp_seq=3 ttl=64 time=0.033 ms
64 bytes from 5.136.146.165: icmp_seq=4 ttl=64 time=0.034 ms
64 bytes from 5.136.146.165: icmp_seq=5 ttl=64 time=0.033 ms

```

Same time as if I had pinged localhost, as it should be.

However, I can't join any networks since I can't login.

---

### Post by superprash2003 on 2009-05-28
does it give you an authentication failed error? try reinstalling hamachi

---

### Post by Mononofu on 2009-05-28
Yes, I've reinstalled it, deleted my config files, etc. 

What do you mean with "authorization error"? I start hamachi, and when I type "hamachi login" it tries for a few seconds and then fails. ("login failed")

This is not a temporary server problem, as I tried logging in a few hundred times with a script and still had no success. 

I believe that there is some sort of networking or routing problem, but I can't really pinpoint it.

---

### Post by superprash2003 on 2009-05-28
are you able to access the internet?? post output of route -n

---

### Post by Mononofu on 2009-05-28
Of course I am, else I couldn't post now ^^

route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

after starting hamachi:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

---

