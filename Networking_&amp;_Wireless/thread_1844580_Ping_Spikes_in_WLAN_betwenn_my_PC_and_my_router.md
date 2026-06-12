---
title: "Ping Spikes in WLAN betwenn my PC and my router"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by Roig on 2011-09-15
Hello all!

I'm having experiencing continued lag spikes betwen my router and my PC using WLAN. 

My router is a Linksys wrt54gl with dd-wrt firmware. I'm using ubuntu 10.04.3 and you can see what's happening there:

```
**64 bytes from 192.168.1.1: icmp_seq=5898 ttl=64 time=22.3 ms**
64 bytes from 192.168.1.1: icmp_seq=5899 ttl=64 time=0.926 ms
64 bytes from 192.168.1.1: icmp_seq=5900 ttl=64 time=0.892 ms
64 bytes from 192.168.1.1: icmp_seq=5901 ttl=64 time=0.910 ms
64 bytes from 192.168.1.1: icmp_seq=5902 ttl=64 time=0.879 ms
64 bytes from 192.168.1.1: icmp_seq=5903 ttl=64 time=1.73 ms
64 bytes from 192.168.1.1: icmp_seq=5904 ttl=64 time=0.902 ms
64 bytes from 192.168.1.1: icmp_seq=5905 ttl=64 time=0.919 ms
64 bytes from 192.168.1.1: icmp_seq=5906 ttl=64 time=0.880 ms
64 bytes from 192.168.1.1: icmp_seq=5907 ttl=64 time=0.897 ms
**64 bytes from 192.168.1.1: icmp_seq=5908 ttl=64 time=23.7 ms**
64 bytes from 192.168.1.1: icmp_seq=5909 ttl=64 time=0.900 ms
64 bytes from 192.168.1.1: icmp_seq=5910 ttl=64 time=0.891 ms
64 bytes from 192.168.1.1: icmp_seq=5911 ttl=64 time=0.893 ms
64 bytes from 192.168.1.1: icmp_seq=5912 ttl=64 time=0.898 ms
64 bytes from 192.168.1.1: icmp_seq=5913 ttl=64 time=0.889 ms
64 bytes from 192.168.1.1: icmp_seq=5914 ttl=64 time=0.897 ms
64 bytes from 192.168.1.1: icmp_seq=5915 ttl=64 time=0.905 ms
64 bytes from 192.168.1.1: icmp_seq=5916 ttl=64 time=0.907 ms
[B]64 bytes from 192.168.1.1: icmp_seq=5917 ttl=64 time=1.52 ms
64 bytes from 192.168.1.1: icmp_seq=5918 ttl=64 time=22.2 ms[/B]
64 bytes from 192.168.1.1: icmp_seq=5919 ttl=64 time=0.909 ms
64 bytes from 192.168.1.1: icmp_seq=5920 ttl=64 time=0.915 ms
64 bytes from 192.168.1.1: icmp_seq=5921 ttl=64 time=0.925 ms
64 bytes from 192.168.1.1: icmp_seq=5922 ttl=64 time=0.915 ms
64 bytes from 192.168.1.1: icmp_seq=5923 ttl=64 time=0.900 ms
64 bytes from 192.168.1.1: icmp_seq=5924 ttl=64 time=0.910 ms
64 bytes from 192.168.1.1: icmp_seq=5925 ttl=64 time=0.926 ms
64 bytes from 192.168.1.1: icmp_seq=5926 ttl=64 time=0.908 ms
64 bytes from 192.168.1.1: icmp_seq=5927 ttl=64 time=0.899 ms
**64 bytes from 192.168.1.1: icmp_seq=5928 ttl=64 time=22.3 ms**
64 bytes from 192.168.1.1: icmp_seq=5929 ttl=64 time=0.926 ms
```

I have to say that in Windows XP/seven my ping is ALWAYS <0 to the router, so I think this has to be a problem with the Linux driver of my WLAN card. Anyone can give some instructions in how to know which driver i'm using and how to contact with a developer of that driver to try to fix it? 

Thank you :)

P.D. And yes when i'm playing online.. I can feel when the lag spike is happening.

---

