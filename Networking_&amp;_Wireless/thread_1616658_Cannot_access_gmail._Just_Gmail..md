---
title: "Cannot access gmail. Just Gmail."
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by cracker89 on 2010-11-08
My college internet providers shifted to a different setting.. defined in the changing lan proxy settings on the user end. I.e.ip - 192.168.0.200 and port  to 3000. This to reduce misuse of the net connection .. :rolleyes:

The thing is, since then, every other website is working, except GMail. It isnt blocked, the Nebero page shows up for blocked sites. When attempting to open gmail, the default internet page shows up for unavailability of page owing to no or slow response from the server, or the firewall or proxy settings not appropriately configured. 

I cannot open gmail, the connection on empathy im. I cant ping gmail either. No response. What can be the problem. Help is appreciable. My internships depend on it. 

Some people can, and some people cannot access gmail. I am using firefox. Is this even a problem related to my end of the connection?

---

### Post by puppywhacker on 2010-11-08
sounds like a misconfiguration of the proxy. gmail uses the same ip addresses as for google, so if you can access that, you should be abled to reach gmail.

---

### Post by cracker89 on 2010-11-09
Ok. the thing is, I have gotten gmail to work. We recieve our net connectio through a proxy address on port set to 3000. If i allow it to connect directly, i can access everything but gmail. turing it on lets me access gmail. 

Can something be done about this?

Windows users are nt facing such a problem. Could this be OS related?

---

### Post by cracker89 on 2010-11-10
Help? Anyone? And additional to gmail, i cannot access [https://help.ubuntu.com/](https://help.ubuntu.com/) as well, as i discovered today.

Ideas? Anything to share?

---

### Post by cracker89 on 2010-11-10
bump...

---

### Post by endotherm on 2010-11-10
can you 
```
nslookup www.google.com
```?

---

### Post by cracker89 on 2010-11-10
Yes.. I can run succesful nslookups on both gmail and google.com... 

```

Server:        192.168.0.200
Address:    192.168.0.200#53

Non-authoritative answer:
www.google.com    canonical name = www.l.google.com.
Name:    www.l.google.com
Address: 209.85.231.104


```

but i still cant open it.

---

### Post by endotherm on 2010-11-10
> **cracker89 said:**
> Yes.. I can run succesful nslookups on both gmail and google.com... 

```

Server:        192.168.0.200
Address:    192.168.0.200#53

Non-authoritative answer:
www.google.com    canonical name = www.l.google.com.
Name:    www.l.google.com
Address: 209.85.231.104


```but i still cant open it.
can you ping the gmail address?
are you using any javascript or address blockers in firefox?

---

### Post by cracker89 on 2010-11-10
welll, the gmail ip is same as the gogle.com one. dnslookup is successful, pinging is not
```
kakar@Cracker:~$ ping 209.85.231.104
PING 209.85.231.104 (209.85.231.104) 56(84) bytes of data.



.
.
.

```
and it stays at that. for pretty much forever.. nope, i havent changed anythng, no java anything, the uni's switched to a new server or settings for providing wireless internet. could this be os related, like i said, windows users arent facing the problem. another campus ubuntu user i kno is also facing the problem..

---

### Post by endotherm on 2010-11-11
interesting. won't even ping by ip. lets try a trace route, as this is seeming more and more like a raw networking issue, than a browser problem. 

```

sudo apt-get install traceroute
traceroute  www.google.com

```
and llets see where it is failing.

do you have a firewall configured, or are you using an IP block list tool like IPBlock or MoBlock/Mobloquer? have you configured any IP based blocks in your routers firewall?

---

### Post by cracker89 on 2010-11-11
Yes it was a network issue. thank u endootherm. It was a small problem with the network config, wherein i had to further add an ignored host, the proxy ip, to the ignored hosts list. its all up and working now... do u have any  idea wat mammoths my college might be trying to set loose here
?

---

### Post by endotherm on 2010-11-11
> **cracker89 said:**
> Yes it was a network issue. thank u endootherm. It was a small problem with the network config, wherein i had to further add an ignored host, the proxy ip, to the ignored hosts list. its all up and working now... do u have any  idea wat mammoths my college might be trying to set loose here
?
interesting. my guess is that they are trying to funnel certian sites through a cacheing proxy to reduce bandwidth on the wan. they probably have hardware from google to help localize stuff as much as they can, but that does little good unless everyone is forced to use it. there are all kinds of reasons they might have chosen to restrict access through their proxy, but half of them are annoying and the other half are creepy. is yours a research institution? if so, check to see what grants they get from the DHS.
glad you got everything worked out, and happy ubuntuing!

---

