---
title: "Networking keep stop after nothing to do for few minutes"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by jij on 2012-12-17
Hi, All. 
I've got serious netwworking problem that is stop after few minutes if i do not working at terminal.
 
I just installed ubuntu 12.04(Server)
And I use static ip address. not dhcp. so, i configured eht0 and it works as expected. 
 
but when i do nothing with terminal for few minutes, then networking stop. 
I can make networking start again with '/etc/init.d/networking restart'.
but it's not solution that i want. 
because it's for web server working 24hrs.
 
Is there any solution for me??TT
 
Please leave reply for my problem.
Thanks. all.

---

### Post by synapsys on 2012-12-18
Maybe there is a known issue with your network card. Please post the output of this command:

```
lspci | grep -i eth
```

---

### Post by jij on 2012-12-18
Thanks for your reply.
 
The results are as follows:
02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
03:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection

 
 
> **synapsys said:**
> Maybe there is a known issue with your network card. Please post the output of this command:
 
```
lspci | grep -i eth
```

---

