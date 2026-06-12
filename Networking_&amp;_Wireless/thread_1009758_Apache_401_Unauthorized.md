---
title: "Apache 401 Unauthorized?"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by dwieeb on 2008-12-13
So I have installed Apache, PHP and MySQL. I go to [http://localhost/](http://localhost/) and it says "It works!", as it should. But, when I get my ip from [http://whatismyip.com](http://whatismyip.com) ([http://75.100.81.209/](http://75.100.81.209/)), it says 401 Unauthorized. Did I miss a step?

---

### Post by Iowan on 2008-12-13
I must have missed a step... You're not getting "401 Unauthorized" *from* [http://whatismyip.com](http://whatismyip.com) - are you?  I presume that message pops up when you try to access your machine from outside your network.

In brief, your router (assuming you have one) will need to forward ports to your machine.  It's also possible your ISP blocks port 80.  Can you **ping** the machine from outside?

---

### Post by dwieeb on 2008-12-13
Yeah, sorry for the misunderstanding, the only 401 error I'm getting is with my IP address. I only used whatismyip.com to get the IP address.

Your second sentence was a foreign language to me, sorry O_o. I'm only a web designer skilled with CSS/HTML/PHP. I'm completely new to Ubuntu and setting up Apache.

---

### Post by dragonny on 2009-02-07
> **Iowan said:**
> I must have missed a step... You're not getting "401 Unauthorized" *from* [http://whatismyip.com](http://whatismyip.com) - are you?  I presume that message pops up when you try to access your machine from outside your network.

In brief, your router (assuming you have one) will need to forward ports to your machine.  It's also possible your ISP blocks port 80.  Can you **ping** the machine from outside?

I am having that problem.
My website is visible from outsite ([http://123.123.123.123/](http://123.123.123.123/)) but when I do from my computer it says error 401 (unauthorized access).
And yes, I forwarded ports to my PC.
Can someone help me with this?

---

