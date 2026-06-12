---
title: "Restarting netgworking and computer isn't resolving my connection problem anymore"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by Klasanov on 2010-01-30
Hi. I was here awhile back and had some connection issues, which got resolved.

Now, anytime I had a connection issue I would type in

sudo /etc/init.d/networking restart ; sudo shutdown -r now
<password>

and this would fix the issue.

But now it's not working.

I believe I'm running Ubuntu 8.10.

Any ideas? Any more info I need to supply?

---

### Post by Klasanov on 2010-01-30
well, I got it working now. Checked my connections, and restarted networking and the computer again.  Although, I'd be curious to know why this happens.  Any ideas?

---

### Post by Iowan on 2010-01-30
Next time it quits, check **ifconfig -a** and **route -n**.

---

