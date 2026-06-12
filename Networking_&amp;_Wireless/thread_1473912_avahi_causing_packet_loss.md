---
title: "avahi causing packet loss?"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by gregnorc on 2010-05-05
So I got a new X201 which is running Ubuntu 10.04. While at home, everything is fine, at work, I encounter some issues with wireless.

Specifically, the signal cuts in and out repeatedly.

Here's the output of ping... I set it to ping a server every 90 seconds, 10 times. So this is a snapshot of 15 minutes of network activity...

```
PING (REDACTED) bytes of data.
64 bytes from (REDACTED): icmp_seq=1 ttl=252 time=1.50 ms
64 bytes from (REDACTED): icmp_seq=2 ttl=252 time=2.13 ms
64 bytes from (REDACTED): icmp_seq=3 ttl=252 time=1.38 ms
64 bytes from(REDACTED): icmp_seq=5 ttl=252 time=1.42 ms
64 bytes from (REDACTED): icmp_seq=6 ttl=252 time=16.9 ms
64 bytes from (REDACTED): icmp_seq=7 ttl=252 time=1.79 ms
64 bytes from (REDACTED): icmp_seq=9 ttl=252 time=3.15 ms

--- (REDACTED) ping statistics ---
10 packets transmitted, 7 received, 30% packet loss, time 810458ms
rtt min/avg/max/mdev = 1.388/4.055/16.988/5.310 ms
```

Also I tried this (from a 2 year old thread which was most relevant solution I could find):
```
Changing AVAHI_DAEMON_DETECT_LOCAL=1 to AVAHI_DAEMON_DETECT_LOCAL=0  in /etc/default/avahi-daemon has got rid of the irritating pop-up.
```

Basically, every 5 minutes or so, for a solid 60 seconds or so I get no signal.

I've tried updating the kernel, and doing apt-get remove avant-daemon, but still have problems. 

Apparently this can be caused by having a poorly set up network that uses .local domains which would cause avant to freak out.

Has anyone encountered a similar issue/found a fix?

---

### Post by gregnorc on 2010-05-06
Anyone? I can post more info if needed...

---

