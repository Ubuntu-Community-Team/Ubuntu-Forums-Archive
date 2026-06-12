---
title: "nat between 2 netcards"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by StarF on 2009-02-26
Hi

I am trying to setup a squid proxy server, with some nat, first i will try and explain what i am trying to do.

I have setup up a squid proxy server, and it seems to be working.

I need to get nat working, so that trafic works this way:

eth1 is used for internal trafic
eth0 is user for external trafic

the catch is, that both netcards can acces the internet, but i only wanna use eth0 for it, so i can see how much trafik is saved by comparing eth1 with eth0.

this means that eth1 shouldent be able to go on the internet, and all trafic from internal computers has to go through eth1 and out of eth0.

any guides, advice or other help in how to resolv this, is apriciated.

also is there a way to see if the proxy cache is working?

---

