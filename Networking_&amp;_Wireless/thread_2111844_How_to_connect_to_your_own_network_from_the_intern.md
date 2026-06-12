---
title: "How to connect to your own network from the internet?"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by DeMus on 2013-02-03
Hi,

I like to connect to my Kubuntu 12.10 computer from wherever I am at the moment, meaning outside my own (wifi) network.
What do I need to do, to install, to setup, to make this possible from either a Windows PC (at work) or from my Android cell-phone?

I know my external IP-address, I know my computer's internal IP-address, I have a Sisco E4200 router.
Who can give me a manual how to do this in such a way that only I can make contact, and not the whole world.
Who can help?

Thanks.

---

### Post by sudodus on 2013-02-03
A simple way to do it is to use Teamviewer. It is commercial software, free for personal use. But it is rather slow.

A more complicated way is to open a port for internet access and use some faster remote desktop software or simply ssh.

Beware, you need to do it carefully, to avoid 'getting owned' by some attacker from the dark side of the internet. I am no expert to guide you, but maybe someone who knows better will read this thread and help you.

---

### Post by DeMus on 2013-02-03
> **sudodus said:**
> A simple way to do it is to use Teamviewer. It is commercial software, free for personal use. But it is rather slow.

A more complicated way is to open a port for internet access and use some faster remote desktop software or simply ssh.

Beware, you need to do it carefully, to avoid 'getting owned' by some attacker from the dark side of the internet. I am no expert to guide you, but maybe someone who knows better will read this thread and help you.

Thank you sudodus,

I tried Teamviewer and yes I can see my desktop on my cellphone, start and stop programs, do what I want, except I can do it here at home because I know and see the two things Teamviewer wants to know: Id and password.
When I am not at home I don't know them, except when I wrote them down before I go, which, knowing me, will probably not happen. Also Teamviewer has to run to be able to connect to.

I was thinking more about a vpn connection which should be safe, I guess. What do I need for that and how do I set it up?

---

### Post by sudodus on 2013-02-03
> **DeMus said:**
> Thank you sudodus,

I tried Teamviewer and yes I can see my desktop on my cellphone, start and stop programs, do what I want, except I can do it here at home because I know and see the two things Teamviewer wants to know: Id and password.
When I am not at home I don't know them, except when I wrote them down before I go, which, knowing me, will probably not happen. Also Teamviewer has to run to be able to connect to.

I was thinking more about a vpn connection which should be safe, I guess. What do I need for that and how do I set it up?

I'm glad Teamviewer works for you. At least sometimes you might foresee, that you need to connect to home, so you start it at home and write the pass key down (I think the id number will always be the same for that installation, so you need to write that one only once, or keep it in your cell-phone).

I dare not help you with VPN, because I'm not sure how enforce good security. But maybe these links would help to get started.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

[https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by DeMus on 2013-02-03
sudodus,

Have read your links and tried to set it up but it is too complicated for me. I better stick to Teamviewer.
Thanks.

---

### Post by sudodus on 2013-02-03
Good luck remembering to prepare for the connection in the morning ;-)

---

