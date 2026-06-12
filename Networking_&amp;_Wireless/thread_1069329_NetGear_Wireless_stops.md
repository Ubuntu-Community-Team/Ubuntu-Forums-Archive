---
title: "NetGear Wireless stops"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by sailthesea on 2009-02-13
Hi Guys 
 I,ve been having a problem maintaining the connection with Netgear wireless network When I start up in Ubuntu most of the time it connects just fine but after a few minutes I lose the connection. It works fine if I reboot in windows, the network and the dongle are ok I,m dual booting 8.10 with Windows 2000 on an old Dell C640. Maybe it's pushing the system too far but the thing doesn't seem to working too hard. It has worked properly in the past I'm just abit puzzled now. Any suggestions?
 Thanks

---

### Post by joelgrrr on 2009-02-14
I have exactly the same problem.

I'm using Heron, on a laptop, with an Atheros 5k chipset wireless card (a,b & g wifi compatible). It all works perfectly at work, but at home I am only able to connect for a short while before the network connection slows to a crawl, or stops completely. Occasionally it restarts again, only to stop shortly afterwards.

I'm still trying to figure out what's different between work and home, to make the difference, I've tried with and without securing the wireless connection, this makes no difference.

I have a netgear router, which is b & g compatible (If I boot into Vista, it all works fine).
I have tried explicitly setting the max tranmission speed, from 54Mb to 11Mb, but this makes no difference.

---

### Post by superprash2003 on 2009-02-14
when you feel that your connection isnt working.. go to the terminal and type **ping google.com** and post output here

---

### Post by joelgrrr on 2009-02-14
When it ceases to work and I ping some server the responses take seconds to arrive, if at all.

---

### Post by sailthesea on 2009-02-14
Just tried your suggestion this is what I get:

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=10 ttl=240 time=125 ms
 
Which doesn't mean a lot to me, at the moment things are a little slow but working, it seems to doing it about 50% of the time
Maybe this info will help 
 Other than this problem I'm having really good experience being new to Ubuntu
Cheers

---

### Post by joelgrrr on 2009-02-15
See this post: [URL="http://ubuntuforums.org/showpost.php?p=6737895&postcount=3"]http://ubuntuforums.org/showpost.php?p=6737895&postcount=3

[/URL]it might help.

---

### Post by superprash2003 on 2009-02-15
you could try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220

---

