---
title: "Plusnet and ubuntu 10.4"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by paul_h_ward on 2010-09-24
This is for anyone who is having trouble with UBUNTU 10.4 and using PLUSNET in the UK

This has been going on for some time now - I have a PC and a laptop both using Ubuntu 10.4. At least three time a day, at varying times. the connection just drops.

Now - if it was just the connection that dropped - would it just not connect again? I think it would - BUT what happens is, it looses it ability to resolve DNS, I can see the THOMSPSON Router OK and it checks out fine. It take about 4 minutes to regain internet access, SMTP and POP come back a bit quicker.
PLUSNET deny it is their problem, but I have tried two different routers and the seam thing happens.
I have even tried re-installing UBUNTU, the only thing I havent done it tried running Window$ - and I wont coz I ant got a license :P.
The wireless drivers are a BROADCOM and INTEL, which both install and run fine in install. (a HP 6715b laptop and an HP pavillion 6721uk desktop)
Has anyone got an ideas if it could be UBUNTU or does this sound like an ISP trying to pass the buck.
BTW - This ran fine for months when I first had it installed.

Many thanks

Paul

---

### Post by SteveDee on 2010-09-24
Yes, I'm on PlusNet and use a Netgear DG834 box. I do get occasional internet loss and have just extracted this from the log:-

```

Sat, 2010-09-18 13:28:40 - LCP down.
Sat, 2010-09-18 13:28:46 - Initialize LCP.
Sat, 2010-09-18 13:28:46 - LCP is allowed to come up.
Sat, 2010-09-18 13:29:47 - Initialize LCP.
Sat, 2010-09-18 13:29:47 - LCP is allowed to come up.
Sat, 2010-09-18 13:30:47 - Initialize LCP.
Sat, 2010-09-18 13:30:47 - LCP is allowed to come up.
Sat, 2010-09-18 13:31:47 - Initialize LCP.
Sat, 2010-09-18 13:31:47 - LCP is allowed to come up.
Sat, 2010-09-18 13:32:47 - Initialize LCP.
Sat, 2010-09-18 13:32:47 - LCP is allowed to come up.
Sat, 2010-09-18 13:33:47 - Initialize LCP.
Sat, 2010-09-18 13:33:47 - LCP is allowed to come up.
Sat, 2010-09-18 13:34:47 - Initialize LCP.
Sat, 2010-09-18 13:34:47 - LCP is allowed to come up.
Sat, 20110-09-18 13:34:51 - CHAP authentication success

```

...so I guess this means that I lost the service for about 6mins last Saturday.

I've no idea how to determine if this is a service provider problem or a glitch at my end.

Maybe if several users have the same log entries (with the same timestamps) it would confirm that the service was down?

---

### Post by paul_h_ward on 2010-09-24
At least that comforting to know I'm not suffering alone. 
I wouldn't really mind the occasional drop in service, but when its 3x or more per day it gets a bit annoying.

---

### Post by SteveDee on 2010-09-24
A few people on the internet claim that dropping the router mtu down to 1400bytes can eliminate this problem.
I'm sceptical, but will keep checking my Netgear log to see how often I lose service, and maybe then try it.

---

### Post by paul_h_ward on 2010-09-25
Right - just tried that on my interface - i'll monitor it - many thanks for the advice

---

### Post by VeganDavid on 2011-06-19
Try going into the router wireless settings and changing to b/g or g instead of b/g/n.

I had the same problem and this fixed it for me.

---

