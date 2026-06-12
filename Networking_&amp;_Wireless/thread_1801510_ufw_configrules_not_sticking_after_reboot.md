---
title: "ufw config/rules not sticking after reboot"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by kilowhisky on 2011-07-10
For some reason after i add a certain number of rules into ufw any subsequent config changes stop carrying over each restart. 

For example i typed:

ufw allow 9080/tcp 

Then i check "iptables -L" and the entry is listed there. 

When i reboot iptables does not have the entry anymore but ufw still has it listed when i type "ufw status." 

When i try and remove the entry in ufw i get this error:

```


iptables: Bad rule (does a matching rule exist in that chain?).

Rule deleted


```

This not only happens with ports but with logging and enabling and disabling the firewall itself. For instance i'll disable the firewall only to have it running on the next restart. 

computer info:

Linux MythTV 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux



Can anyone help?

---

### Post by leetkrew on 2013-03-25
i got the same problem too

its almost half a year since you posted this problem.. i guess no one knows the real solution for this problem :(
i hope i'm wrong

this is my workaround
add this on your cronjob (when system boots)

```

ufw delete allow 9080/tcp; ufw allow 9080/tcp

```

---

