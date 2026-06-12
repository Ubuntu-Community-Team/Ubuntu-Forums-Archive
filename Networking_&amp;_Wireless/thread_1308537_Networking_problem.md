---
title: "Networking problem"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by bob brazie on 2009-10-31
Is there a known problem with wired and wireless networking in 9.10 and is it being worked on?

---

### Post by Iowan on 2009-10-31
There seems to be a DSL problem - and I've seen more than a few "Lost internet on upgrade" threads.

---

### Post by bob brazie on 2009-11-01
Thanks, I wonder if it's being worked on and when we might see a fix.

I will hate to go back to 9.04 for awhile and them upgrade again and not have it work.

Anyone know if it is being worked on? Bob.

---

### Post by tworthy on 2009-11-01
I lost my internet access upon upgrading to 9.10 and am also wondering if others have the same problem.  I can still use the Terminal Server app to connect to my Windows boxes, but Firefox can't find any internet addresses on one machine.  On one notebook I upgraded, the wireless connection seems to be working and I can access the internet, but Firefox is kind of flaky and not very stable.  How do I go back to the previous release????  Thanks for any help'

---

### Post by sandman42 on 2009-11-01
> **bob brazie said:**
> Is there a known problem with wired and wireless networking in 9.10 and is it being worked on?

There are also normal network problems: particulary, there are problems because of a strange behaviour of resolv.conf due to resolvconf.

Practically, I am not able to set name resolution and I have to edit manually /etc/resolv.conf at every boot.

There are bugs open for this and they are working on it. I hope they will solve it rsn.

Ciao

---

