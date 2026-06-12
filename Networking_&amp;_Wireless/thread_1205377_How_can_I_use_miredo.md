---
title: "How can I use miredo?"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by arita on 2009-07-05
hello I install miredo (its running now) but I can't conect with anywhere, I don't have any response from the server please help me what can I do ](*,)

---

### Post by sanderj on 2009-07-06
Did you get a teredo interface with an IPv6 address? Check with "ifconfig teredo". This is mine:

```

ubuntu@ubuntu:~$ ifconfig teredo
teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: fe80::ffff:ffff:ffff/64 Scope:Link
          inet6 addr: 2001:0:53aa:64c:18e:a61:a55:f0d/32 Scope:Global
          UP POINTOPOINT RUNNING NOARP  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:144 (144.0 B)


```

If so, can you ping6 ipv6.google.com? Here's mine:

```

ubuntu@ubuntu:~$ ping6 ipv6.google.com
PING ipv6.google.com(ey-in-x68.google.com) 56 data bytes
64 bytes from ey-in-x68.google.com: icmp_seq=1 ttl=56 time=37.6 ms
64 bytes from ey-in-x68.google.com: icmp_seq=2 ttl=56 time=36.5 ms
64 bytes from ey-in-x68.google.com: icmp_seq=3 ttl=56 time=50.9 ms
64 bytes from ey-in-x68.google.com: icmp_seq=4 ttl=56 time=46.8 ms
^C
--- ipv6.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 36.572/42.991/50.921/6.090 ms
ubuntu@ubuntu:~$


```

If the ping6 does not work, what does 'mtr ipv6.google.com' show you?



If things do not work,  which 'miredo' messages are in /var/log/syslog? Here's mine:


```

ubuntu@ubuntu:~$ grep -i miredo /var/log/syslog

Jul  5 23:40:13 ubuntu miredo[5388]: Starting...
Jul  5 23:40:13 ubuntu miredo[5391]: Cannot resolve Teredo server address "teredo-debian.remlab.net": No address associated with hostname
Jul  5 21:42:02 ubuntu miredo[5391]: New Teredo address/MTU
Jul  5 21:42:02 ubuntu miredo[5391]: Teredo pseudo-tunnel started
Jul  5 21:42:02 ubuntu miredo[5391]:  (address: 2001:0:53aa:64c:18e:a61:a55:f0d, MTU: 1280)


```


FYI: teredo / miredo does not work over a certain kind of NAT:

"Teredo works well over cone and restricted NATs. Teredo in Windows XP SP2, Windows XP SP1 and the Advanced Networking Pack for Windows XP, and Windows Server 2003 Service Pack 1 cannot work over symmetric NATs."


And it is my experience that teredo does not work if you have an "agressive" firewall, which IMHO you don't need if you're behind NAT ...

---

