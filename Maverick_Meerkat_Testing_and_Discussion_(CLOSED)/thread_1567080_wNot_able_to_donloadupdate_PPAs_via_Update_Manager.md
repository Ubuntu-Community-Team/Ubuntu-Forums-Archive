---
title: "wNot able to donload/update PPAs via Update Manager"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2010-09-03
Since installing the beta yesterday, I havent been able to download ppa I've set in. Also, when I try to update via the terminal, all my PPA are ignored. Pretty much it outputs all of my PPA and reads:
```
N: Ignoring file [insert PPA NAME HERE] as it has an invalid filename extension
```
How can I solve this issue? It also gets in the way of updating beta packages.

EDIT: OMG, not only did I screw up the thread title, I just did a quick search and fount another thread after searching for the same input. Damn, again. Sorry. Good Morning to everyone :(

---

### Post by tjeremiah on 2010-09-03
to solve for people that may need the same help.

put this in your terminal 

```
sudo sh -c "echo 'Dir::Ignore-Files-Silently:: \"(.save|.distupgrade)$\";' > /etc/apt/apt.conf.d/99ignoresave"
```

---

