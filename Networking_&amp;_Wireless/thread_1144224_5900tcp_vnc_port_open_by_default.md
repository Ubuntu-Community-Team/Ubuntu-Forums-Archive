---
title: "5900/tcp vnc port open by default?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by sashaK on 2009-04-30
Hi,
I have 5900/tcp vnc port open on my ubuntu 8.04. I don't access my system remotely. I have not set anything up on it to do with vnc.
Is this port left open at initial installation of ubuntu by default?
Is it safe to leave it open, or should I close it down? In case I have to close it down, I'd appreciate some guidelines on how to do it, as googling it didn't shed much light on the situation.
Thanks in advance.

---

### Post by dmizer on 2009-04-30
"Open" does not mean "actively listening". If there is no VNC server installed/configured on your system, then there is nothing to respond to VNC requests.

Having a router between your computer and the internet is also helpful.

---

### Post by sashaK on 2009-04-30
Thanks.

---

