---
title: "Latest weekly fixes reset my backend and database address"
date: 2008-09-26
forum: Mythbuntu
---

### Post by Lindsay.Mathieson on 2008-09-26
I have my combined FE/BE and MySQl set on a public ip rather than the default local host so that I could run the FE up on my desktop PC occasionally and watch TV.

However the last weekly fixes update reset the BE setting to 127.0.0.1 for DB and mythtv-backend server address. No big deal to reset them but it was a little concerning.

Is this normal for weekly fixes update behaviour?

Thanks,

Lindsay

---

### Post by superm1 on 2008-09-26
> **Lindsay.Mathieson said:**
> I have my combined FE/BE and MySQl set on a public ip rather than the default local host so that I could run the FE up on my desktop PC occasionally and watch TV.

However the last weekly fixes update reset the BE setting to 127.0.0.1 for DB and mythtv-backend server address. No big deal to reset them but it was a little concerning.

Is this normal for weekly fixes update behaviour?

Thanks,

Lindsay
No it's not.  That's particularly odd..

---

### Post by ian dobson on 2008-09-26
Hi,

I've seen that happen afew times when the Mythtv-database package is updated. I've fixed the problem by running the dpkg-reconfigure to reconfigure the password/ip.

Regards
Ian Dobson

---

### Post by Lindsay.Mathieson on 2008-09-26
> **ian dobson said:**
> Hi,

I've seen that happen afew times when the Mythtv-database package is updated. I've fixed the problem by running the dpkg-reconfigure to reconfigure the password/ip.

Thanks, I'll remember that for future reference.

---

