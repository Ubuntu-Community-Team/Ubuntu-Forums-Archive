---
title: "SSH Adding a New Non-Local User"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by Chrissd on 2011-01-05
Hi,

Trying to add my wife as a user to my computer, only to log on through SSH, not locally. Only problem is I use keys for logging in.

I've gone through the guide on the ubuntu website, created a key, copied to through a pen drive, put it in her .ssh folder on my computer, but it still comes up with the error:

```
Agent admitted failure to sign using the key.
Permission denied (publickey).

```

Can anyone give me an idea what I might be doing wrong? Is there a group I need to add her to, or add her public key to a different file somewhere?

Thanks

---

### Post by Chrissd on 2011-01-05
Solved it myself, just needed to run:
ssh-add

---

