---
title: "GPG error (meerkat)"
date: 2010-05-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Loxx on 2010-05-27
meerkat development build:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BEFailed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead

---

### Post by wayneericgouin on 2010-05-27
that sounds as if the maverick source for that repo isn't available yet, have you tried editing it to say Lucid instead?
That;s the same error I get if I try a repo which isn't up for Maverick yet, so I just edit it to say Lucid and it's fine.

---

### Post by wojox on 2010-05-27
Import the key:

```
gpg --keyserver keyserver.ubuntu.com --recv 247510BE
```

```
gpg --export --armor 247510BE | sudo apt-key add - && sudo apt-get update
```

---

### Post by Loxx on 2010-05-27
many thanks wojox :D

---

### Post by wojox on 2010-05-27
Your welcome. :P

---

