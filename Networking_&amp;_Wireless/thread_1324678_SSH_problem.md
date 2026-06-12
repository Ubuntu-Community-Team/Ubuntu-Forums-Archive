---
title: "SSH problem"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by rawoo on 2009-11-12
I have three computers behind a linksys router. Each computer is assigned its own static internal IP address and has the ssh server installed. How do I ssh to a specific computer/or all of them separately from outside the network? I know about using port forwarding on the router to a specific IP address/computer within the network, but how can an ssh connection be established without having to assign different ssh ports to each system?

---

### Post by Iowan on 2009-11-12
Forwarding different SSH ports seems the most straight forward, but if it would allow it, you *might* SSH into the router, then SSH from there to the individual machines...

---

### Post by falconindy on 2009-11-12
Easiest solution is setting a different SSH port on each computer and forwarding that port to the assigned IP. Using your router as an intermediary isn't a realistic solution without spending large amounts of money.

---

### Post by rawoo on 2009-11-12
> **Iowan said:**
> Forwarding different SSH ports seems the most straight forward, but if it would allow it, you *might* SSH into the router, then SSH from there to the individual machines...

Okay. Sound interesting. Question: How do I SSH into the router? This may be a silly question, but I'm serious. I am able to currently SSH into one of the three computers, but that is because I have forwarded port 22 on the router to that system.
Thanks for your help.
Richard

---

### Post by Iowan on 2009-11-13
It may/not be possible - depending on the router.  I built a [Freesco]("http://www.freesco.org/support-forum/") router/firewall that could be set up that way. Again, even an SSH port can be a security risk.

---

### Post by emkamau on 2009-11-15
AFAIK the only way you can do what you want is through port forwarding as suggested by others above.

Why not just ssh into the one box and then from there into the others? I have the same set up as you and thats what I do. I have a server thats always running so I just get into that and then into the other boxes.

SSH into the router is possible depending on the router. It should be a config option. You could do this with DD-WRT installed on a suitable router.

emk

---

