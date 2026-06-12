---
title: "Use ssh as phone"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by abandonedthe_mulletator on 2009-03-14
I am far away from home and I am having trouble using skype and ekiga because the network here blocks a lot of ports.  They do however have ssh open and I can log into my wife's computer using it.  Is there a way I can have a voice conversation directly from computer to computer over ssh?
Thanks in advance.

---

### Post by nelskurian on 2009-03-14
Your idea was good.But i dont think that was existing...If it,then HurraaH..Anybody their..

---

### Post by puppywhacker on 2009-03-14
ssh has the possibility of port tunneling, which is basically what you want. The problem is that many VoIP protocols use many and random ports. So what you need to solve is how to get this through your tunnel.

A possible solution is to use 2 Asterisk servers and use IAX to connect them via your ssh tunnel. But I admit it is a rather cumbersome setup

---

### Post by abandonedthe_mulletator on 2009-03-15
I will explore VPN I've heard a lot about it but I have never used it.

---

