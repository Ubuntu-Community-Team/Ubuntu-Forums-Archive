---
title: "pppoe problem"
date: 2005-02-28
forum: Networking &amp; Wireless
---

### Post by dplastico on 2005-02-28
Hi im from Chile , my english its not good, but i have a problem and i dont know how to fix

I have an ADSL internet connection , my modem is the speedtouch 500, it works by ethernet, not by USB, well... i installled the ubuntu dist. and i configured my ppp with pppoeconf everything goes fine, my inet status its correct the DNS are correct in fact i can ping all hosts, i can connect to msn with gaim, i can connec t to ftp, everything exept webpages, i cant connect to pages, its not a mozilla problem, because i tried with lunx and others

also when i configured the apt-setup i tried to connect by html but, nothing happend, only show "waiting for headers" 

i hope that you can understandme i know my english sucks xD, but im deperated :S

help please

---

### Post by svg on 2005-03-04
Looks like wrong DNS support...

Try some traceroute (apt-get install traceroute ; 
# traceroute <your_provider_gateway>
# traceroute <somewhere_in_the_web> )

and be aware of time responses...

---

