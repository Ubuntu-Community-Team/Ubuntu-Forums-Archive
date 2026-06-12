---
title: "could somebody check my firewall settings based on this info? slsk port forward"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by isconnor@uforums on 2009-03-06
hey all, longtime reader first time caller here :D

i've got a problem with nicotine+ that is driving me bonkers, and i've been trying everything-- maybe too many things. i'm a little worried that i've screwed things up while trying to connect to slsk; could one of you jedis please tell me if this output for

sudo netstat -plantu

is as abnormal as it seems to me? 

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:45794           0.0.0.0:*               LISTEN      7045/python     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      5759/exim4      
tcp        0      1 192.168.1.100:56239     92.131.78.61:2234       SYN_SENT    7045/python     
tcp        0      1 192.168.1.100:59437     217.159.130.116:26719   SYN_SENT    7045/python     
tcp        0      0 192.168.1.100:37326     208.76.170.50:2240      ESTABLISHED 7045/python     
tcp        0      0 192.168.1.100:34938     96.49.51.235:22306      ESTABLISHED 7045/python     
tcp        0      0 192.168.1.100:38825     68.184.192.169:15129    ESTABLISHED 7045/python     
udp        0      0 0.0.0.0:68              0.0.0.0:*                           6634/dhclient   
udp        0      0 0.0.0.0:39764           0.0.0.0:*                           5027/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5027/avahi

```

i've got ubuntu 8.10 running with the new version of nicotine+, but I can't make connections. i've also got a problem with firestarter, if we get that far.. i'm watching this thread closely so please request any further information that might be interesting. thanks!


[edit] this output is from when I am running nicotine+, and i've got the proper ports (none of which appear above) forwarded from my router through it's firewall.

---

### Post by yeats on 2009-03-06
Well, I'm not familiar with nicotine+, but I can see that it is Python-based and I see 5 Python connections on different ports:

```
tcp        0      1 192.168.1.100:56239     92.131.78.61:2234       SYN_SENT    7045/python     
tcp        0      1 192.168.1.100:59437     217.159.130.116:26719   SYN_SENT    7045/python     
tcp        0      0 192.168.1.100:37326     208.76.170.50:2240      ESTABLISHED 7045/python     
tcp        0      0 192.168.1.100:34938     96.49.51.235:22306      ESTABLISHED 7045/python     
tcp        0      0 192.168.1.100:38825     68.184.192.169:15129    ESTABLISHED 7045/python     

```

If you have this many connections open and are still not "connecting" it sounds to me that the firewall would be related.  I'm just a Padawan learner though - perhaps a Jedi master can enlighten us more :-)

---

### Post by isconnor@uforums on 2009-03-06
hey, thanks for the response. 


it's odd; none of those ports correspond to the range that I opened, hoping that they would work. I love soulseek, though, you should try it, it's great when its working.

---

