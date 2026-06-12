---
title: "Getting &quot;connection refused&quot; on ssh"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by scorchgeek on 2010-07-19
I'm trying to set up a webserver and am receiving connection refused errors when attempting to ssh into it. I followed the directions in this tutorial: ```
http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/
```

This has you install and configure a firewall called "shorewall". After following the directions (unless I missed something), I could connect through the internet and download web pages, but the ssh fails to work. I tried stopping the firewall service with sudo /etc/init.d/shorewall stop, and got a message to the effect that it was shutting down, but that didn't help.

I'm running the ssh through my local network (so the router isn't the problem), and I can ssh from the server to my desktop, just not the other way around.

Is there some other firewall configuration I'm missing?

---

### Post by scorchgeek on 2010-07-19
Another note: I'm getting a connection refused when I try an
```
ssh [username]@localhost
``` on the server as well. So something in the server configuration must be messed up, I'd assume.

---

### Post by scorchgeek on 2010-07-19
I'm an idiot--the SSH server wasn't installed. Thanks for looking if you did.

---

### Post by Praetor77 on 2010-07-28
Glad you solved your problem.

Maybe you should consider deleting the thread, as it shoudln´t provide useful info to anyone visiting it?

---

### Post by Iowan on 2010-07-28
[SOLVED] will do nicely - thanks!

---

### Post by Paddy Landau on 2010-07-29
> **Praetor77 said:**
> Maybe you should consider deleting the thread, as it shoudln´t provide useful info to anyone visiting it?
It helped me! I didn't even know that it needed installing.

---

