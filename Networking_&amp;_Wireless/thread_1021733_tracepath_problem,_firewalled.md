---
title: "tracepath problem, firewalled?"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by mrgedman11 on 2008-12-25
tracepath is not producing any usable information.  i thought it used the same port as http, port 80 or whatever, so it should not be blocked/firewalled by my router.  running 8.04 hardy.  Below is tracepath output


```
me@eeepc:~$ tracepath www.google.com
 1:  eeepc.local (192.168.0.104)                       0.403ms pmtu 1500
 1:  192.168.0.1 (192.168.0.1)                              1.464ms asymm  2 
 1:  192.168.0.1 (192.168.0.1)                              1.425ms asymm  2 
 2:  no reply
 3:  no reply

```

What is the deal with this? it times out after reaching my router.  I am getting out of the router, as i am on the system writing this thread...

---

