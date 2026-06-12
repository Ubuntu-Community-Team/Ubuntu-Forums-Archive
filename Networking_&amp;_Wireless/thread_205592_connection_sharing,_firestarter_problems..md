---
title: "connection sharing, firestarter problems."
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by funnyfraggle on 2006-06-28
I'm trying to set up a ubuntu box to kill some of the Internet traffic at my office. This is really just stopping people from going to certain URLs, but I also need to allow mail traffic to a specific IP on the network.

Right now we have a DSL modem that acts as a router. We aren't allowed to configure it in any way because of the service we have. It also acts as our gateway.

What I would like to do is set the ubuntu box between the router and our switch and let it kill all the traffic we don't want. Firestarter looked like a dream come true, but I can't get the connection sharing to work. The machine that has firestarter can access the Internet, but the computer behind it can't. (I tried a cross-over cable, but that didn't make a difference).

Our network uses Static IP addresses, and all the help I find seems to outline only DHCP. Can anyone help me out, or point me to a guide? Also, I'm not stuck on this solution. Pretty much anything that doesn't involve us having to buy a lot of hardware or software is probably going to be something I'm interested in.

Well, this is my first post, and I must say I haven't had any problems finding answers to my questions until now. I hope I have as much luck actually asking a question instead of just looking at others.

---

### Post by funnyfraggle on 2006-06-29
I don't think anyone is going to respond to this thread, but just in case I didn't want anyone to waste their time on this.

I'm now working on a solution using brctrl and shorewall. I've already got the bridge working, which was the biggest problem with my previous attempts.

---

