---
title: "Two default gateways - which one is used?"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2006-04-26
I had 10.0.0.10 as my default gateway, but our working place has three Intenet connections on three different users. I downloaded a Gnoppix CD today, and I was told I could use the other router, 10.0.0.1 for this, because it has a faster Internet access. So I did:

sudo route add default gw 10.0.0.1

I thought this would replace the old default gw, but it added a new one, so I had TWO default gateways. Which one is being used now?

Well I had the idea - to get even more downloading performance - could I somehow tell Ubuntu to use both or even all three routers IN PARALLEL to download something even faster? Or could there at least be some kind of load balancing, e.g. when I download something with wget, and send a large email with Evolution?

Tom

---

### Post by tomski on 2006-04-26
you can do that theoreticaly,
 but to get a true performance gain you would be better off having:
 a seperate pc in front of your pc acting as a main gateway 
and then have 4 net cards eth0 - 4 
where eth0 is the feed to your pc and the others 1,2,3 are the feeds from each gateway 
and then install some loadbalancing software on the main gateway 
this will then combine all of the avaliable bandwidth from the 3 connections to one connection to your pc.


     3 feeds from gateways 10.0.0.1, 10.0.0.10, other 3rd 10.0.0.xxx
     | | |
   ------
   |      |  pc with load balancing 10.0.0.250
   ------
       |
       |
  -------
  |        | your pc   10.0.0.50
  -------


 otherwise you set up the loadbalancing software on your pc and tell it the ip of each gateway and then watch your cpu go through the roof

---

