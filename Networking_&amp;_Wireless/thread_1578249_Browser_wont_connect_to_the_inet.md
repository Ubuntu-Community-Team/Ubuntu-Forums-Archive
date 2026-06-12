---
title: "Browser wont connect to the inet"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by Rigoz on 2010-09-20
I have checked similar posts but can't find a solution to my problem...

I recently moved home and I'm having problems to connect to the internet with the new router. 
I connect normally to the internet with windows but I can't get firefox to work under ubuntu, neither wired or wireless.

Ubuntu software center downloads ok though.
The pings seem to go and come back ok as well.
The chat and browser in Nicotine works ok also.

I am a nob so I don't really know what to do.

Someone can help, please?. Thanks.

---

### Post by dineshs on 2010-09-20
What do you get when you ping 4.2.2.1?pl post results of
```
ping -c5 4.2.2.1
```and
```
ping -c5 google.com
```

---

### Post by Rigoz on 2010-09-20
ping -c5 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=241 time=16.9 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=241 time=16.8 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=241 time=15.4 ms
64 bytes from 4.2.2.1: icmp_seq=4 ttl=241 time=17.2 ms
64 bytes from 4.2.2.1: icmp_seq=5 ttl=241 time=16.9 ms

--- 4.2.2.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 15.473/16.681/17.203/0.628 ms

ping -c5 google.com
PING google.com (173.194.37.104) 56(84) bytes of data.
64 bytes from google.com (173.194.37.104): icmp_seq=1 ttl=52 time=16.4 ms
64 bytes from google.com (173.194.37.104): icmp_seq=2 ttl=52 time=17.7 ms
64 bytes from google.com (173.194.37.104): icmp_seq=3 ttl=52 time=16.4 ms
64 bytes from google.com (173.194.37.104): icmp_seq=4 ttl=52 time=17.5 ms
64 bytes from google.com (173.194.37.104): icmp_seq=5 ttl=52 time=16.4 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 16.461/16.948/17.708/0.599 ms

---

### Post by Iowan on 2010-09-20
Have you tried disabling IPv6? [Here]("http://ubuntuforums.org/showpost.php?p=9863952&postcount=3") is one link-to-a-link.

---

### Post by Rigoz on 2010-09-20
wow... that was easy, and worked!! Thanks so much to both of you.

---

