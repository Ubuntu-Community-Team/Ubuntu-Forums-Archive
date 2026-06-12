---
title: "SSH'ing into my network"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2010-07-28
Hi there.

I have SSH on my main desktop at home which I SSH into to grab files, use it as a proxy, browse the web safely from afar, etc. I use a non-default port to SSH nto this box.

I also want to SSH into my "server" computer which I'm slowly building. 

Do I just need to set my router up to direct another port to the second box? Both boxes have fixed IP addresses on the internal network.

---

### Post by v1ad on 2010-07-28
if you are sshing from the web to the server you are allowed to only open port 22 for 1 machine, or you will have conflict. see if you can set up shh to listen to another port or something and try it that way. 

another option is ssh into machine 1. and from machine 1 shh through local  network to machine 2.

---

### Post by Nostalos on 2010-07-28
> **Whisp3r said:**
> 
Do I just need to set my router up to direct another port to the second box? Both boxes have fixed IP addresses on the internal network.

Yes.  Or as the user above stated. SSH into box 1, then from there ssh to box 2.

---

### Post by Whisp3r on 2010-07-29
Many thanks.

---

