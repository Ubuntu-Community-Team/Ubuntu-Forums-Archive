---
title: "can't access some websites"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by enimeizoo on 2011-06-27
Hello,
I don't know where the problem comes from, but I can't access a few website since this morning. But I can access them via any public web proxy.
Where can the problem come from? I happens with several computers, with different OS and browsers. 
(ubuntu 11.04, 10.04, w.vista, w.7)
(rekonq, IE, ff, opera, konqueror and arora)
When I try to access them I get a timeout.

I can't even ping them, packet are sent, but lost.

I use different dns servers (including google ones)

Would it help if I listed website I can't access? (among them : gmail, hotmail, [www.dyndns.com/accounts](www.dyndns.com/accounts), mostly pages I have to log in)

Next thing I'm gonna try is to set the router config back to default.

Thanks for any help.

---

### Post by bkratz on 2011-06-27
> **enimeizoo said:**
> Hello,
I don't know where the problem comes from, but I can't access a few website since this morning. But I can access them via any public web proxy.
Where can the problem come from? I happens with several computers, with different OS and browsers. 
(ubuntu 11.04, 10.04, w.vista, w.7)
(rekonq, IE, ff, opera, konqueror and arora)
When I try to access them I get a timeout.

I can't even ping them, packet are sent, but lost.

I use different dns servers (including google ones)

Would it help if I listed website I can't access? (among them : gmail, hotmail, [www.dyndns.com/accounts](www.dyndns.com/accounts), mostly pages I have to log in)

Next thing I'm gonna try is to set the router config back to default.

Thanks for any help.

You might want to check into MTU (maximum transmission units) 
 
[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

I have seen other threads where this being to high seemed to have the same symptoms.

---

### Post by enimeizoo on 2011-06-27
Is that setting a router setting? I can't believe that 5 laptops have the same problem the same day (with different OS), so I guess it is. But I can't find the setting.

Here the result of a traceroute :
```

traceroute to mail.google.com (74.125.230.151), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.790 ms  1.426 ms  1.955 ms
 2  92.49.115.254 (92.49.115.254)  30.226 ms  34.106 ms  37.788 ms
 3  naga.resot.net (217.175.160.97)  42.467 ms  46.134 ms  50.307 ms
 4  10.0.13.1 (10.0.13.1)  221.821 ms  224.484 ms  228.621 ms
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *                                                                                          
12  * * *                                                                                          
13  * * *                                                                                          
14  * * *                                                                                          
15  * * *                                                                                          
16  * * *                                                                                          
17  * * *                                                                                          
18  * * *                                                                                          
19  * * *                                                                                          
20  * * *                                                                                          
21  * * *                                                                                          
22  * * *                                                                                          
23  * * *                                                                                          
24  * * *                                                                                          
25  * * *                                                                                          
26  * * *                                                                                          
27  * * *                                                                                          
28  * * *                                                                                          
29  * * *
30  * * *

```

---

### Post by bkratz on 2011-06-27
> **enimeizoo said:**
> Is that setting a router setting? I can't believe that 5 laptops have the same problem the same day (with different OS), so I guess it is. But I can't find the setting.



I really don't know. I know Ubuntu usually sets it to automatic or 1500, but the router is supposed to control it in auto, I believe (not really sure though). If you do a search on googlUbuntu for MTU you will find the same threads. Often just reducing it to 1492 corrects a lot of problems. Googlubuntu is a really good tool!

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by enimeizoo on 2011-06-27
I didn't know about googlubuntu, it is a nice tool.
I changed my mtu to lower values, it didn't change anything. I tried 1492, 1000, 900 (from 1500), but still doesn't change a thing. Is there a way to find out what is my mtu from the outside? (something like whatsmyip). 

But I think I have a clue. I tried to get to mail.google.com via links (the only browser I had I didn't try btw), and it gets stuck at 'SSL negociation', and finally gets a timeout too.

And now it tells me that, I realise that most (if not all) of the websites I try to access are https. But that doesn't makes sense, I still should be able to ping them, right?

I double checked, and I have no way to change the mtu on the router.

(edit) I can connect via telnet on port 80. But I don't even know what page to request >.<
I usually access gmail using "https://mail.google.com"
which is the server name.
I'll try some and update.

OK, I can get it with telnet. 
What the **** is wrong?

---

### Post by enimeizoo on 2011-06-27
Sorry for the early bump, but I really need to check my mails.
There are sites I can access via http, but no via https.
Could that be a ISP problem?

---

### Post by bkratz on 2011-06-27
> **enimeizoo said:**
> Sorry for the early bump, but I really need to check my mails.
There are sites I can access via http, but no via https.
Could that be a ISP problem?

Have spent the time since last post looking. Most are old threads, but some suggest using a different DNS server than the one your router and isp use. I use google's public DNS myself

[http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)


Other posts suggested open DNS

(by the way it seems that mtu should be between 1400 and 1500)

[http://www.opendns.com/](http://www.opendns.com/)

both are free and may take care of your problems. The threads seemed to point to DNS problems.

---

### Post by enimeizoo on 2011-06-27
I really appreciate your help, but I did try to set my mtu to 1492, and use different DNS. This computer uses google's one, other use the one from the router.

I'm trying openDNS, but I don't think that is the problem.
Nope, that didn't work.

I really think that is a ssl problem.

---

### Post by enimeizoo on 2011-06-27
Also I can't use ssh outside of the local network. I can telnet the server on the port 22.

---

### Post by enimeizoo on 2011-06-27
It just fixed itself... right after I sent a mail to my ISP... (pretty sure it was it anyways)

Anyways, thanks for your help bktratz, at least I know about googlubuntu :p

---

### Post by enimeizoo on 2011-06-28
Well, the problem came back in the afternoon.

Is there any test I can do that would prove the problem comes from the ISP?
Some logs, some websites that would test my connection?

---

