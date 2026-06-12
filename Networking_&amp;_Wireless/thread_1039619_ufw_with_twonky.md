---
title: "ufw with twonky"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by Dumbestcrayon on 2009-01-14
I like twonky media server. I Use it for my Xbox.
I like UFW. For other reasons.


I need to know what ports Twonky Media Server uses so I can allow them to be used in UFW.

Or if there is an easier/other way.

---

### Post by albinootje on 2009-01-14
> **Dumbestcrayon said:**
> 
I need to know what ports Twonky Media Server uses so I can allow them to be used in UFW.

Seems to be port 9000, or perhaps 9001 :
[http://www.progressiveav.com/ts109install/](http://www.progressiveav.com/ts109install/)

But try with ethereal, or a similar program.

---

### Post by Dumbestcrayon on 2009-01-14
Yeah I tried those. Still doesn't seem to work. This might help..

```
tcp        0      0 192.168.1.101:9003      0.0.0.0:*               LISTEN      26239/twonkymediase
tcp        0      0 127.0.0.1:9004          0.0.0.0:*               LISTEN      26239/twonkymediase
tcp        0      0 192.168.1.101:9013      0.0.0.0:*               LISTEN      26239/twonkymediase
tcp        0      0 127.0.0.1:9014          0.0.0.0:*               LISTEN      26239/twonkymediase
```



I tried adding all of those 9XXX ports but I'm thinking the 127.0.0.1 might have something to do with it.

---

### Post by albinootje on 2009-01-14
> **Dumbestcrayon said:**
>  I tried adding all of those 9XXX ports but I'm thinking the 127.0.0.1 might have something to do with it.

With the more recent Ubuntu releases there's also 127.0.1.1 in /etc/hosts but I don't know whether that matters.

With the command tcpdump you should be able to check the ports.
Assuming that you're using eth0, try these two :
```

sudo tcpdump -vvv -n -i eth0
sudo tcpdump -vvv -i eth0

```
The -n is without the protocol name, so you can see the port name.

---

### Post by Dumbestcrayon on 2009-01-14
> **albinootje said:**
> With the more recent Ubuntu releases there's also 127.0.1.1 in /etc/hosts but I don't know whether that matters.

With the command tcpdump you should be able to check the ports.
Assuming that you're using eth0, try these two :
```

sudo tcpdump -vvv -n -i eth0
sudo tcpdump -vvv -i eth0

```
The -n is without the protocol name, so you can see the port name.



What am I looking for in all of the mess that I get back from those two codes?

---

### Post by albinootje on 2009-01-14
> **Dumbestcrayon said:**
> What am I looking for in all of the mess that I get back from those two codes?

You're looking for which port numbers are in use by twonky.
It can be messy, but try to only let the traffic with twonky be active, to find out more.

---

