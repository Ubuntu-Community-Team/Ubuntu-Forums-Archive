---
title: "Website connection problems"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by plutonic on 2010-12-28
Hello,

I am having the strangest problem I have seen so far and after googling all over the net and not finding anything I will post my problem here.

I am a programmer for a casino-company running multiple domains on several dedicated servers.

I am constantly connected over ssh throughout the day to these servers but since some time I have problems opening the websites or making new connections.

The thing is, if the connection is already open it does not get dropped, but making a new connection on any port times out.. and after some minutes if I try again it suddenly works again and then suddenly stops working again.

The most strange is that in my network (behing NAT router) everybody can access the websites without problems, also at the time when I have connection problems. And in our office I am the only person working on ubuntu (10.10).

I found things on google talking about ICMP or MTU size and have tried some things with that but it did not solve my problem, also on our dedicated servers our office IP is listed as 100% trusted so firewalls are not messing with me as well.

Is there any way within Ubuntu to find out exactly why I am having these problems, and why only with our own dedicated servers?

Pinging and dns lookups work fine (even when I can not connect to the server).

traceroute works, tcptraceroute works, ping with large packets works, reverse dns lookups work (dig -x), all telnet fails (Like the ACK package never arrives back to me).

For me the problems did start to happen after managing some dns stuff on our dedicated environments, however since then other people have also looked at these configs and have not seen problems with the changes. And I am apparently the only person having problems establishing connections.

I hope someone can point me in the right direction with this problem so that I can get is sorted. If I need to post more info about the Ubuntu / configs I am using please let me know.

Thanks

---

