---
title: "Connecting through command line via a Proxy Server"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by guessswh0 on 2010-03-02
Hey guys,

I could use some help.  I have  a VM of Ubuntu at work, and I am trying to update it and connect to things via the command line.  I do have a proxy server that I not only have to connect through, but I also have to authenticate myself to the proxy server.

What I've done:

I've entered the proxy information and my authentication information in System - Preferences - Network Proxy

I've also entered the information within the preferences of the synaptic package management.

When I try to connect to the internet via firefox, it still prompts me for my username and pass, but then it allows me to connect.  When I connect via Synaptic Package Management, it connects right away (since that also has my proxy and authentication information).

Howver, I am unable to do anything via the command line.  As odd as it may seem, really, it's the best thing that I know.  Just trying to do a sudo apt-get update returns an error saying "Proxy Authentication Required" and i can't connect.

So in the end, I can connect almost every way to the internet (that I've tested) except for the command line.  I could definitely use the help.

Thanks

---

### Post by guessswh0 on 2010-03-02
I just found the answer to my own question.  In case anyone else needs it, here is the link.

Thanks



[https://help.ubuntu.com/community/AptGet/Howto#Setting%20up%20apt-get%20to%20use%20a%20http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting%20up%20apt-get%20to%20use%20a%20http-proxy)

---

