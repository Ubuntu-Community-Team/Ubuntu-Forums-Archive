---
title: "Ubuntu 10.04 internet problems"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by prodigyaj on 2010-06-01
Hi,

I download ubuntu 10.04 yesterday. I have already been using ubuntu 9.04 without any problems all the while. I have broadband connection ADSL router for internet connectivity , which would be completely auto initialized and configured in 9.04. However in 10.04 the connectivity although seems to be configured and initialized , the browser does not seem to reflect the web pages. On hitting a a given site , the status message changes immdeiately from looking ... to connecting ... and it stays that way.

Any inputs ? ? 

Regards 

AJ

---

### Post by dineshs on 2010-06-01
what do you get when you ping open DNS and google?
```
ping 4.2.2.1 -c5
```
```
ping google.com -c5
```

---

### Post by prodigyaj on 2010-06-01
Below is what I get !! 

PING google.com (209.85.153.104) 56(84) bytes of data.
64 bytes from google.com (209.85.153.104): icmp_seq=1 ttl=58 time=10.2 ms
64 bytes from google.com (209.85.153.104): icmp_seq=2 ttl=58 time=10.2 ms
64 bytes from google.com (209.85.153.104): icmp_seq=3 ttl=58 time=9.85 ms
64 bytes from google.com (209.85.153.104): icmp_seq=4 ttl=58 time=10.0 ms
64 bytes from google.com (209.85.153.104): icmp_seq=5 ttl=58 time=9.85 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 9.852/10.065/10.277/0.213 ms
ubuntu@ubuntu:~$ ping 4.2.2.1 -c5
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=245 time=145 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=245 time=146 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=245 time=144 ms
64 bytes from 4.2.2.1: icmp_seq=4 ttl=245 time=145 ms
64 bytes from 4.2.2.1: icmp_seq=5 ttl=245 time=145 ms

--- 4.2.2.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 144.915/145.729/146.011/0.533 ms

---

### Post by dineshs on 2010-06-02
Everything looks normal.Please check the configurations under EDIT-PREFERENCES-NETWORK-CONNECTION SETTINGS .Tick only `use system proxy settings'
Or
Can you try a different web browser?

---

### Post by Iowan on 2010-06-02
MTU might cause similar problems. Unfortunately, I don't have a link available at the moment, but theres a thread that discusses checking/changing MTU values.

---

### Post by bkratz on 2010-06-02
> **Iowan said:**
> MTU might cause similar problems. Unfortunately, I don't have a link available at the moment, but theres a thread that discusses checking/changing MTU values.

I think post 2 is your link to the original thread referenced.

[http://ubuntuforums.org/showthread.php?t=1376506](http://ubuntuforums.org/showthread.php?t=1376506)

---

