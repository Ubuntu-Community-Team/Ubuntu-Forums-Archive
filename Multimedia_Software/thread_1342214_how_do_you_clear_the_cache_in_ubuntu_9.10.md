---
title: "how do you clear the cache in ubuntu 9.10"
date: 2009-11-30
forum: Multimedia Software
---

### Post by handyman510a on 2009-11-30
How do I clear the cache I use ubuntu 9.10

---

### Post by diaa on 2009-11-30
> **handyman510a said:**
> How do I clear the cache I use ubuntu 9.10

What cache do you mean?
Usually most of the cache-type files are stored in /var/cache however you shouldn't be modifying these files on your own.
As for the package cache(also known as apt cache) which holds the packages you download, you can clear it by running
```
sudo apt-get clean
```

---

### Post by handyman510a on 2010-03-30
thank you for your reply i take your point

---

