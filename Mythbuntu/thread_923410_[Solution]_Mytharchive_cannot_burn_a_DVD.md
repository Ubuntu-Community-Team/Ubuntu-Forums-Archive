---
title: "[Solution] Mytharchive cannot burn a DVD"
date: 2008-09-18
forum: Mythbuntu
---

### Post by barney_1 on 2008-09-18
Recently I watched a program that I wanted to share with a friend.  I have in the past used Mytharchive to copy it to a DVD and pass along.  Unfortunately it didn't work this time giving me an error along these lines:

```
ERROR: Failed while running growisofs. Result 130
```

After further investigation it seems that the python script is looking for my DVD burner at /dev/dvd but that doesn't exist.  Instead I have /dev/dvd2 but that is just a symlink pointing to the actual drive at /dev/scd0.

So, in my case I was able to fix this by adding a symlink:

```
sudo ln -s /dev/scd0 /dev/dvd
```

Fixed it right up.  I hope others will find this info helpful!

---

