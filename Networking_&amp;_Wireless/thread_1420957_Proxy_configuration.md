---
title: "Proxy configuration"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by Tomasud on 2010-03-03
I have a ubuntu server box that ive been trying to turn into a proxy server for LAN-Gatherings. The idea is to have this box between the local network and the Internet
Accepting only those computers that have registered on my website thats run localy

I have allready made a Java applet that pulls the mac adress for their convinience.

So far i have installed and configured 

- Apache + Working website
- MySQL #It is working configured by-
- PhPMyAdmin
- vsftpd - working ish 

From what i can gather from reading lots of posts on google is that i should use Squid
But all the guides/refferances i can find to the subject are either not what im looking for or extreamly vauge. So my question is; Is squid the best way to do this, and if so how to get the squid to link eth0(internet) to eth1(Local Area Network), but only the mac addresses pulled from the sql server? 

Hope you can understand the gist of what im saying, if not ill try to elaborate more. 

All help is much appreciated! 

-Thomas

---

