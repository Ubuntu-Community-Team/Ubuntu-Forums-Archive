---
title: "All network connections start and then hang"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by krige on 2010-04-04
Hello,

all connections on my computer start loading and then hang: it happens when running apt-get update (a few repositories load successfully and then it hangs at a random one) and when loading web pages with the browser (it says "Connecting...", then "Waiting for....", sometimes some part of the page loads, and then it hangs).

This happens both with my wired and my wireless connection. It does not happen on Windows on the same computer.

Any idea on what it might be?

---

### Post by krige on 2010-04-04
This is what I get from running wget [www.ubuntu.com:](www.ubuntu.com:)

```
Resolving www.ubuntu.com... 91.189.90.40
Connecting to www.ubuntu.com[91.189.90.40]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15658 (15K) [text/html]
Saving to: 'index.html'

33%[===============>               ] 5,292 --.-K/s eta 5m 24s
```

Then hangs like that with eta increasing every second.

---

### Post by Iowan on 2010-04-04
One of my "favorite" villains is currently MTU. [Here]("http://ubuntuforums.org/showthread.php?t=1376506") is a thread that details checking MTU. It seems unlikely that wired and wireless would both suffer the same symptoms - but it won't hurt to check...

---

### Post by krige on 2010-04-05
Thank you Iowan.

I have run:

```
$ ping www.ubuntu.com -c 1 -s 1464 -M do
PING www.ubuntu.com (91.189.90.41) 1464(1492) bytes of data.
1472 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=1 ttl=47 time=94.3 ms
--- www.ubuntu.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 94.327/94.327/94.327/0.000 ms

$ ping www.ubuntu.com -c 1 -s 1465 -M do
PING www.ubuntu.com (91.189.90.41) 1465(1493) bytes of data.
From pippo.homenet.telecomitalia.it (192.168.1.2) icmp_seq=1 Frag needed and DF set (mtu = 1492)
--- www.ubuntu.com ping statistics ---
0 packets transmitted, 0 received, +1 errors
```

Then I have tried setting the MTU with the command "sudo ifconfig eth0 mtu X" both to 1464 and 1492, ensuring that it was properly set with "ifconfig | grep MTU", but I still have the same problem.

---

### Post by krige on 2010-04-05
I connected the computer to some other network and there Internet worked just fine. The problem I had on the other network must be related with the particular ADSL modem/router I was connected to.

---

### Post by Iowan on 2010-04-06
Not to abandon you... is the problem [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), or do we still need to work on "the other network"?

---

### Post by krige on 2010-04-07
Thanks :) the problem is not solved, but I can't access to the not working network at the moment. I will try again in one or two weeks.

---

