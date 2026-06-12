---
title: "Specific e-mail not being sent"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by PenguinLust on 2011-07-26
For some reason I'm able to send out lots of e-mails, except this specific one that I'm trying to send to my Member of Parliament. My ISP has blown me off and tells me it's a problem of a firewall or antivirus program on my computer (I also can't rule out my router, but I seriously doubt it has that level of sophistication).
When I try to send, after about a minute I get "4.4.2 Timeout while waiting for command" which is why my ISP says this is my problem. I've looked in /var/log/messages and it doesn't give any indication that this system is blocking the e-mail. I don't think it's a firewall but how can I tell? Or what else can I try?
I'm running Ubuntu 10.04 and the Thunderbird client that goes with: 3.1.11.

---

### Post by PenguinLust on 2011-07-26
Nevermind. It looks like it *was* the router. Rather than block specific signature e-mails I think it might have been somehow dropping the ball when I had to transfer data of a certain size out. That would be a more rational explanation for why it was blocking certain e-mails, letting some through, and letting everything download. Am I able to mark this solved?

---

