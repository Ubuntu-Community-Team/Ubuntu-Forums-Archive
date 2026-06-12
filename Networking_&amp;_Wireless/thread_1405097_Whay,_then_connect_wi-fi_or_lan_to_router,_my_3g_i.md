---
title: "Whay, then connect wi-fi or lan to router, my 3g internet stop working?"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by Sylslay on 2010-02-12
Useing gnome network manger.\

I thught that is DNS resolve problem, and wrote in linksys router the same DNS as 3g huaweii modem use.

Steel the some result. NO INTERNET.

Change for static ip in router and try use the same gatway , but steell can't use connected at the same time to internet with 3g and local router.

Only one devace at the same time,
Router have no any acces to internat.

SO why 3g internet stoping working after connecting router to LAN ports?

Has it some thing to do with subnet or ip range and routing table?

---

### Post by Sylslay on 2010-02-18
Meaby got answer.

Whan switched off DHCP on router and set static Ip for eth0. 

Than have two gatways, and one gatway actualy hasn't acces to network.
and one gatway from 3g modem.
So DNS are fine,

When live gatway in router as 0.0.0.0 or blank.
my internet working again :-)

---

