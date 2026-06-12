---
title: "Postfix dropping mail messages"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by Paralab on 2009-11-12
Hello,

I am having a problem with Postfix dropping mail messages on receive. I am running Postfix and Dovecot on Ubuntu 9.10 Server Edition.

**Mail.log**
Nov 12 22:10:18 ubuntu postfix/qmgr[1938]: 4EBFF26980: from=<*hidden*+caf_=sam=*hidden*@gmail.com>, size=3209, nrcpt=1 (queue active)
Nov 12 22:10:18 ubuntu postfix/local[2082]: 4EBFF26980: to=<sam@*hidden*>, relay=local, delay=1.8, delays=1.8/0/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Nov 12 22:10:18 ubuntu postfix/qmgr[1938]: 4EBFF26980: removed


Any idea what the problem may be?

---

