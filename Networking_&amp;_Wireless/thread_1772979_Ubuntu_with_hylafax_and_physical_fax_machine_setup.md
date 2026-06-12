---
title: "Ubuntu with hylafax and physical fax machine setup"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by Gr8cong on 2011-06-01
Hello,

Please excuse me if i'm creating this thread in wrong place.

Recently, me and other partners had open our 1st business office.
 we got 1 phone line and what we want to do is the following:
 Ubuntu FAX (hylafax) to receive facsimile and forward to email
 physical fax machine to be used to send ONLY the facsimile.

I've already installed and configured the hylafax.
 the hylafax is set to receive and forward the faxes to our general mailbox
 the issue arise is when one wants to send a fax using physical machine. if i use the phone line spliter and connect the faxmachine and ubuntu server togheter i'm affraid that  both machines will end up picking up incoming faxes.
Do i need extra hardware or something to have the setup done correctly?

regards, 
Gr8cong

---

### Post by Redterp on 2011-08-05
Hey, If you are still trying to figure out how to use hylafax to pickup incoming faxes but still be able to use a fax machine on the same line for just outbound here's an idea.
Most fax machines have a number or rings before accepting fax option. For your outbound fax machine, set it to the highest incoming rings value you are allowed to.
Now on the hylafax config page set ModemRingsBeforeResponse to a number less than that (I'd say closer to 0).
I have not done this myself but figured it might be a painless method to try. Good luck.

---

