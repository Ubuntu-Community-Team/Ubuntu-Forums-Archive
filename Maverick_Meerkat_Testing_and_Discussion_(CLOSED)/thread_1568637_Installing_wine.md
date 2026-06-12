---
title: "Installing wine"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by SteveS1949 on 2010-09-05
Hi
I am trying to stall wine. I have added the PPA but when I run an apt-get update; It fails to add download the link to the wine installer.

Therefore, when I run sudo apt-get install wine1.3 it cannot find the file.

I think this may have something to do with the 'Partial Upgrade' I am being offered??

---

### Post by cariboo on 2010-09-05
What happens if you just try wine eg:

```
sudo apt-get install wine
```

It looks like it is a transitional package to help install it from the ppa.

---

### Post by IanW on 2010-09-06
The wine PPA doesn't support maverick yet. You have to use the lucid version.
That is:-
1: Add the ppa as normal with ppa:ubuntu-wine/ppa
2: Edit both repo lines to use lucid instead of maverick

---

