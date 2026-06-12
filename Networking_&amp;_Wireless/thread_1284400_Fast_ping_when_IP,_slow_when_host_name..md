---
title: "Fast ping when IP, slow when host name."
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by StrangeWill on 2009-10-06
Painfully slow, 3 pings in 20 seconds. 0.052ms ping for each of the 3 pings though.
```

william@Server:~$ ping example.com
PING example.com (xxx.xxx.xxx.xxx) 56(84) bytes of data.
64 bytes from xxx.xxx.xxx.xxx: icmp_seq=1 ttl=64 time=0.051 ms
64 bytes from xxx.xxx.xxx.xxx: icmp_seq=2 ttl=64 time=0.052 ms
^C64 bytes from xxx.xxx.xxx.xxx: icmp_seq=3 ttl=64 time=0.050 ms

--- example.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 20020ms
rtt min/avg/max/mdev = 0.050/0.051/0.052/0.000 ms

```

Fast.
```

william@Server:~$ ping xxx.xxx.xxx.xxx
PING xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx) 56(84) bytes of data.
64 bytes from xxx.xxx.xxx.xxx: icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from xxx.xxx.xxx.xxx: icmp_seq=2 ttl=64 time=0.024 ms
64 bytes from xxx.xxx.xxx.xxx: icmp_seq=3 ttl=64 time=0.024 ms
64 bytes from xxx.xxx.xxx.xxx: icmp_seq=4 ttl=64 time=0.060 ms
^C
--- xxx.xxx.xxx.xxx ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.024/0.042/0.063/0.020 ms

```


Lookup is not slow:
```

william@Server:~$ time nslookup example.com
Server:		xxx.xxx.xxx.xxx
Address:	xxx.xxx.xxx.xxx#53

Non-authoritative answer:
Name:	example.com
Address: xxx.xxx.xxx.xxx


real	0m0.043s
user	0m0.000s
sys	0m0.000s

```
The system seems to stall on requests weird times, such as using squirrelmail or IMAP using the host name (works fine when IP is specified instead), this doesn't seem right and probably related.


Any ideas? Domain is held by Godaddy, DNS @ record is pointed at this server at xxx.xxx.xxx.xxx, and I'm doing all this from the server itself. It shouldn't take 20 seconds to ping itself 3 times. Issue is also replicated on another machine on the network. The server holds multiple domains so example.com is not set as the computer's host name.

Adding example.com to the hosts file on the server will improve ping time on the server, but only the server, not the other machine.


Also, seems to only be affecting those inside the network with the server.


Edit: Server seems to be doing this will all IPs

---

