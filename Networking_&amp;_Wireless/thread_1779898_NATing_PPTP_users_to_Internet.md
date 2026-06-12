---
title: "NATing PPTP users to Internet"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by mganji on 2011-06-11
Hi Folk

I've setup a PPTP server on my ubuntu 11.04. PPTP settings seem to be OK and I can connect to my machine from a Windows PPTP client. But then I dont have access to Internet from my Windows machine.
Authentication is successful and I can see GRE traffic to my PPTP interface on my Ubuntu, but I can't reach any host (including Internet) after my Ubuntu machine. 
I suspect this is a routing or NATing issue. 

I'm a newbie in Linux world, so please bare with me ;) I understand networking though

Thanks

---

### Post by novinick on 2011-06-11
hi

try to set lower priority  "network metric" for pptp interface on client machine
for example to 100 to be the last

or undo it , so that interface is not default gateway
(in some way ? )

(have not beeen conecting on pptp actualy , other conections have those parameters, pppoe for example )

multiple conections allways arises problems

---

