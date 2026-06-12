---
title: "How to get mail out of queue?"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2012-08-03
I had temporarily set tls auth on and so some mail get deferred b/c it couldn't be authorized.

I corrected this and new mail is arriving correctly.

BUT the deferred mail is stuck in the queue!

I tried ```
postfix -f
``` but it doesn't retrieve the mail!

```
# mailq
``` shows the mail is in the queue.

How can I get it back?

Thanks

---

