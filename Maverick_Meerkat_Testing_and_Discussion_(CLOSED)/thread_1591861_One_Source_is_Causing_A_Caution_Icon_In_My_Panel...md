---
title: "One Source is Causing A Caution Icon In My Panel..."
date: 2010-10-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Lucradia on 2010-10-10
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

See above error.

---

### Post by ktp on 2010-10-10
See this thread:
[http://ubuntuforums.org/showthread.php?p=9912525#post9912525](http://ubuntuforums.org/showthread.php?p=9912525#post9912525)

Solution is:
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

---

### Post by teh603 on 2010-10-10
> **ktp said:**
> See this thread:
[http://ubuntuforums.org/showthread.php?p=9912525#post9912525](http://ubuntuforums.org/showthread.php?p=9912525#post9912525)

Solution is:

+1. Solution also works in Kubuntu.

---

### Post by Lucradia on 2010-10-10
> **ktp said:**
> See this thread:
[http://ubuntuforums.org/showthread.php?p=9912525#post9912525](http://ubuntuforums.org/showthread.php?p=9912525#post9912525)

Solution is:

Thanks, works now. :D

---

