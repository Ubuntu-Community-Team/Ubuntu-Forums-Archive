---
title: "how to I change ports of an application"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by mess110 on 2009-09-02
Ok so I got this game called babo violent.

The problem: I am in uni and I want to play it. The university blocks a lot of ports. The default port in babo violent is 3333

So this is how I see this:

BABO sends to port 3333
ubuntu catches info through port 3333 but the network can't send it
ubuntu catches info through port 3333 and sends it through port 80 to the server
I play babo happy

But how do I do this? And is this possible? (I can see some issues but I might be wrong)

---

### Post by aeiah on 2009-09-02
it could be if the babo server accepts that type of information through port 80. chances are, they dont. you'd need a machine outside of the university network that could translate the port 80 information back to port 3333. this is essentially what a proxy server does.

if you know the babo server will accept through port 80 or another port that you can use, you'd use iptables to port forward your internal traffic out through port 80 or whatever. id find a good tutorial through if i were you, i hear iptables can be a pain in the ***.

---

