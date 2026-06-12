---
title: "dsl connection only with cable but not with wireless"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by onelasttry84 on 2011-09-07
hi,
I hope someone around here is able to help me. 
Im using an asus eee-pc 1001p and ubuntu 10.10. usually i use an standard router without any problems, neiter for cable nor wireless connections. At the moment i'm in china where my landlady only provides a dsl modem. One where u can either connect via wireless or up to 3 computers via cable. What I did so far:

I used the network manager to set up a dsl connection. When I connect my netbook via cable I get a connection to the modem and the dsl connection shows up. Afterwords i chosse the dsl connection and some seconds later internet works like a charm.

The Problem is that i would like to go online using wireless. I get a connection through wireless to the modem without problems but then I'm not able to choose the dsl connection. It just doesn't show up in the network manager as a choosable option.

any suggestions?

---

### Post by Murukesh on 2011-12-26
I'm afraid you'll have to go to the command line for this. I'm in India, and my ISP, BSNL, also provides a wi-fi-capable DSL modem. I had to do two things to get my net connection to work through wireless:
a) Use pppoe-conf to setup a PPPoE (DSL) connection profile. If you know which device your wireless is, then use that when running pppoe-conf. Mine was eth1, so I ran ```
pppoe-conf eth1
```Start the connection using ```
pon dsl-provider
```b) Replace the DNS servers that the router assigned using DHCP with ones that the ISP provided after I logged in. I noticed that when Ubuntu dials the DSL connection over the wired connection, the settings from the router are  entirely replaced by those from the ISP, including IP and DNS servers. So I tried changing the DNS servers when I found that I could pon dsl-provider worked successfully, logging me in, but I couldn't access any site.
Then perhaps you could write a script to run pon dsl-provider whenever you connect to that wifi network.

---

