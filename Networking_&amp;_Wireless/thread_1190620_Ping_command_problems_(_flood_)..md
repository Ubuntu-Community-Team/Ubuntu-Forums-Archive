---
title: "Ping command problems ( flood )."
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by ActiveFrost on 2009-06-18
```
dainis@bytehood:~$ ping google.lv -f
PING google.lv (72.14.221.104) 56(84) bytes of data.
ping: cannot flood; minimal interval, allowed for user, is 200ms
```

How can I fix this so I would be able to flood-ping ?

---

### Post by Lampi on 2009-06-18
> **ActiveFrost said:**
> How can I fix this so I would be able to flood-ping ?
Use an interval:

```
man ping

       -f     Flood ping. For every ECHO_REQUEST sent a period &#8216;&#8216;.&#8217;&#8217; is printed, while for  ever  ECHO_REPLY
              received  a backspace is printed.  This provides a rapid display of how many packets are being
              dropped.  If interval is not given, it sets interval to zero and outputs packets  as  fast  as
              they  come  back  or one hundred times per second, whichever is more.  Only the super-user may
              use this option with zero interval.

       -i interval
              Wait interval seconds between sending each packet.  The default is  to  wait  for  one  second
              between  each  packet normally, or not to wait in flood mode. Only super-user may set interval
              to values less 0.2 seconds.
```

---

### Post by ActiveFrost on 2009-06-18
Thanks, however .. why I don't get any output ?

```
dainis@bytehood:~$ sudo ping -f -i 0.1 google.lv
[sudo] password for dainis: 
PING google.lv (216.239.59.104) 56(84) bytes of data.
..
```

---

### Post by Lampi on 2009-06-18
try to increase the interval, I guess google.lv has better things to do than accepting ping floods on a high interval level?

---

### Post by ActiveFrost on 2009-06-18
> **Lampi said:**
> try to increase the interval, I guess google.lv has better things to do than accepting ping floods on a high interval level?

Yeah, now I even don't get these 2 dots at the end :D
```
dainis@bytehood:~$ ping -f -i 5 izzi.lv
PING izzi.lv (195.244.128.8) 56(84) bytes of data.
```
That's all .. no dots, no output. Any ideas ? Btw, izzi.lv is my ISP and I've done a lot of pinging from my Win32 box !

---

### Post by Lampi on 2009-06-18
What if you use verbose output? Then again: it is host dependend. If I where google or ISP I wouldn't accept ping floods either.

---

### Post by ActiveFrost on 2009-06-18
> **Lampi said:**
> What if you use verbose output? Then again: it is host dependend. If I where google or ISP I wouldn't accept ping floods either.

Verbose output still gives me an empty line.
You say, you wouldn't accept ping floods .. Flood means what ? What's the difference between doing flood with 1sec. intervals and ping with 1 sec intervals ?

---

### Post by Lampi on 2009-06-18
> **ActiveFrost said:**
> Flood means what ? What's the difference between doing flood with 1sec. intervals and ping with 1 sec intervals ?
[http://en.wikipedia.org/wiki/Ping_flood](http://en.wikipedia.org/wiki/Ping_flood)

If the server you are ping flodding is not properly configured to deal with that amount of data you request, it will cause the server to hang up - it's a simple form of DOS (denial of service) attack. As you can see google knows well how to ignore ping floods, as does your internet service provider :) Most servers should have protection against ping flodding, I hope apache servers have it enabled by default as well ;)

Just use ping without flood on google and the server will reply.

---

### Post by rnbrady on 2010-08-18
You need to be root. 

As the man page states: "Only super-user may set interval to values less 0.2 seconds."

---

