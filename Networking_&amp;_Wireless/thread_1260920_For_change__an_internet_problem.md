---
title: "For change : an internet problem"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by pierrot_bobo on 2009-09-08
Hi everybody.

Here is my problem. i installed ubuntu on my eeepc and it firste worked very well. Suddenly, after having installed some applications i dont remember, impossible to go back on internet.
I connect to the network with wifi or ethernet (everything on auto, set by default, as it worked before) and it's ok but no way to surf with firefox or download packages.
I dont understand. I think this might be a software problem more than a hardware problem.

Thanks for helping

---

### Post by pierrot_bobo on 2009-09-09
Hi there again,

I was wondering, might this be a problem caused by some kind of firewall or proxy server ?
Thanks

---

### Post by Claus7 on 2009-09-09
Hello there,

and welcome to the forums. Is it that you have jaunty installed? There might be two problems. Either a dns issue or an ipv6 issue.

Can you ping any address (ping ....with numbers)?

Regards!

---

### Post by pierrot_bobo on 2009-09-18
Hi thanks to reply,

Yeah i got jaunty jackalope installed.

When i ping to 192.168.0.1 i get :

ping: sendmsg: Operation not permitted

What does that mean ?

---

### Post by Iowan on 2009-09-18
I've seen that message in a few other threads - but not a solution. One "fixed itself", two others were unanswered.  *Might* be firewall issue...

---

### Post by jward3010 on 2009-09-18
This might sound strange but worth the experiment. Try:
```
sudo ping -c 5 208.67.222.222
```
And tell us what you get.

---

