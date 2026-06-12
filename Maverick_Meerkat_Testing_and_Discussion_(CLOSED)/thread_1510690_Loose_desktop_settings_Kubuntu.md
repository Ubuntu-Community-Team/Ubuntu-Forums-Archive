---
title: "Loose desktop settings Kubuntu"
date: 2010-06-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by caryb on 2010-06-15
Was wondering if I'm on my own or does Kubuntu not save desktop settings? This started about a week ago after upgrades. When I log on it does not remember the last person to logon as well.



Cary

---

### Post by Reiger on 2010-06-15
The last person to log on thing, is in fact a bug in the package (you'll find errors about not being able to open a certain file in the logs). I've reported that here: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/588090](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/588090)

To fix that, the following should do:

```

sudo chown kdm:kdm -R /var/lib/kdm

```

As for the other thing... works for me? Perhaps you are past that high point as described in a signature: “if it ain't broke you haven't tweaked it enough”?

---

### Post by caryb on 2010-06-16
Thanks Reiger that fixed 1/2 my problems, I will report the other.

Cary

---

