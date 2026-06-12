---
title: "Nothing works anymore?"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by movieman on 2010-12-22
So, as of last week I was able to boot up my laptop, ls an automounted NFS directory, and it would configure an IPSEC tunnel to the server, mount the directory and... everything just worked.

Now that works... sometimes. But more typically, setkey isn't run on startup so the IPSEC tunnel can't be configured, and portmap isn't started so NFS doesn't work. After logging in I have to run setkey, start portmap, restart racoon and restart autofs before I can access the remote directory.

Anyone know what might have changed in the last few days that almost completely screwed my network config?

---

