---
title: "When I type my external ip address my router console pops up"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by Fertech on 2011-12-25
I'm using Ubuntu 10.10 on a Desktop, got D-link dir-651 wireless router
I also got a SG-200-26 Port Gigabit Smart Switch.

So the way I got this setup is, I got my comcast modem to my wireless router, my wireless router to my switch and my switch to my desktop.

If I remove the wireless router I can see my web server, it's only when I add the wireless route. 

I can see it my site when I type localhost or 192.168.0.102 the problem is only external not internal.

---

### Post by Doug S on 2011-12-25
You need to add settings in the wireless router to forward TCP port 80 requests to 192.168.0.102. There is a section in the manual for the listed router (under section 3 - configuration) called "Port Forwarding".
Hope this helps.

---

### Post by Fertech on 2011-12-25
I did Fwd port 80, I know it's something in the wireless router console settings but what?

---

### Post by Fertech on 2011-12-25
Here is an attachment, is there anything else im missing?

---

### Post by Fertech on 2012-01-14
No luck yet,

---

