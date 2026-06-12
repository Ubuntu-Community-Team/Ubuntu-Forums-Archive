---
title: "Redirect IIS to Ubuntu"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by [_Tech_] on 2011-04-07
Hello guys,
I don't know if I'm posting in the right section of right forum, but I'm kind of desperate, because I can't google any information on the case I'm having.

I've got Ubuntu virtualized with VirtualBox from Sun, under a Windows 2003 Server with IIS.

Is there any configuration that can be done to Ubuntu in order for it to reply to an entry in my IIS Server?
Or maybe I'm thinking it wrong ans it's something else that I'm not seeing right now...

Thanks in advance for any help.
Best regards.

---

### Post by crispy_420 on 2011-04-08
What is your ultimate goal? Get all web traffic to go to Apache on a virtualized Ubuntu VM?

If that is the case, in VirtualBox don't use NAT and let it get a "real" network address. Then use router to forward appropriate ports to virtualized Ubuntu.

Did I misunderstand what you wanted?

---

