---
title: "[HELP] redirect traffic to spesific port based on Traffic Content using iptables"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by topimiring on 2009-06-22
Hi , I'm new to iptables , and I need to redirect all incoming traffic to port 21 in my localhost which contains of string "abcdefgh" to another server at port 21
Is this correct ?:

> iptables -t nat -A PREROUTING -p tcp --dport 21 -m string --string "abcdefgh" -j DNAT --to-destination <ipaddress:21>  

I tried to run it , but it didn't redirect at all.

Thank you

---

### Post by jonobr on 2009-06-22
bumping for you,

Im interested in this one, and hoping someone answers it.......

---

### Post by Polaris96 on 2009-06-22
I can't answer your question.

I tried doing this awhile ago and was told that using iptables to filter by packet contents is not smart.  I was also told a SQUID server could do what you are attempting to do.  I never tried it because life got in the way.

I do know SQUID is available in the repository and can do what you're attempting.  I don't know how to set it all up, though.

For what it's worth, I could never get iptables to do content based traffic control, although I have it working great for source priorities and such.  I'm going to follow this thread, as well.  Thank you for posting it.

---

### Post by topimiring on 2009-06-23
I don't have any idea how can squid do what i am attempting to do. I actually get this idea from [http://www.linuxsecurity.com/content/view/117370/49/](http://www.linuxsecurity.com/content/view/117370/49/) , but I don't want to DROP the traffic , just need to redirect it to another host :confused:

---

