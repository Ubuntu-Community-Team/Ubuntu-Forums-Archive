---
title: "VNC between PCs behind different firewalls"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2011-01-28
[SIZE=2]Hi,[/SIZE]
[SIZE=2]I want to make my screen visible to somebody on a remote site. I[/SIZE][SIZE=2]s there any way of VNCing between two PCs that are behind 2 different firewalls and are protected by VPN? [/SIZE]

[SIZE=2]From outside, user1 and user2 have to establish a VPN connection to their respective network in order to access. Either 1 or 2 would thus needs to know the password of his/her respective partner (?)[/SIZE]

[SIZE=2]I first thought of trying a reverse connection via an ssh tunnel, but even this might not be possible since access to the listening viewer will be blocked as well. [/SIZE]

[SIZE=2]Is it possible that both connect to a PC outside the firewalls and run a tunnel over this one? [/SIZE]
[SIZE=2]Thanks for hints![/SIZE]

---

### Post by YesWeCan on 2011-01-29
I don't understand your question.
What do you mean by "protected by VPN"?

---

### Post by dieter-erich on 2011-02-01
Well, one PC is behind a firewall and you only can access it via VPN (e.g. using a Cisco client and the necessary credentials). The second is behind a different firewall and you can also only access it via another VPN (again by using other credentials). So, you need to know your partner's VPN password to access his/her network. I think that this scenario is not very uncommon! There appears a possibility to connect by using a PC in between that is accessible by both because it is not part of any VPN-protected network! So, what to do?

---

### Post by pricetech on 2011-02-01
The short answer would be to consult with your respective IT departments.  Anything else is probably not allowed, especially sharing your credentials.

---

### Post by YesWeCan on 2011-02-01
Is it the case that neither PC can access the Internet? Is this why both have to have external communications initiated externally?
If so you are out of luck aren't you?

---

