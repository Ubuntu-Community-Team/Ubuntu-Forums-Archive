---
title: "mythbackend will not start on boot"
date: 2007-12-12
forum: Mythbuntu
---

### Post by ebike on 2007-12-12
Hi All,

I am having problems with mythbackend not starting on boot. It used to work, but not any more.

I have to run it manually once my machine has booted.

I cannot find where mythbackend is started, there does not seem to be an entry in /etc/init.d/

Can someone tell me where it is started and where to look for an error message?

It starts fine manually, so have no idea why it does not start on boot.

Thanks

---

### Post by ebike on 2007-12-12
Found the problem. I had a stale nfs lock file in my recordings directory. Deleted that and it booted up fine.

---

### Post by pteri498 on 2008-01-09
I also had a similar problem when I put the recordings directory on its own partition.

Mythbuntu puts recordings by default in /var/lib/mythtv/recordings. Offsetting this to its own partition messes with the ownership, so just make sure that the mythtv group becomes the owner.

```

chown username:mythtv /var/lib/mythtv

```

---

