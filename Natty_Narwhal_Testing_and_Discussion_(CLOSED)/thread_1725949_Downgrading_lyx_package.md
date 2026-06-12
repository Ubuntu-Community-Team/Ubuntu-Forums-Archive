---
title: "Downgrading lyx package"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by baytuni on 2011-04-10
I upgraded to Ubuntu 11.04 Natty Narwhal 4 days ago and Lyx which is the most frequent package I use came with its 2.0 RC1 version. But unfortunately the scrolling has a major bug causes scrolling using too much cpu and it makes the software impossible to use.I reported the bug [here]("https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/756671") 

So my question is: is there any way to downgrade the lyx package to 1.6.x. I tried to uninstall it and to install the older package with some deb file but it has failed. I believe it is because lyx depends on a large amount of other packages which is related to latex. So if anyone knows any way to downgrade please tell me how to.

---

### Post by fredericthewise on 2011-04-27
I also have issues with lyx and want to downgrade: how?

---

### Post by Harry33 on 2011-04-27
You have to take into account the dependencies differencies to be able to downgrade.
So, first install the dependencies that the older lyx (1.6.7-1) has but the newer lyx (2.0.0~rc3-1) does not have.
It appears that the older lyx (1.6.7-1) depends on:
 - libaiksaurus-1.2-0c2a (>= 1.2.1+dev-0.12)
while the newer lyx (2.0.0~rc3-1) does not depend on it anymore.

First, install libaiksaurus-1.2-0c2a with Synaptic to cope with dependencies.
This pulls in also libaiksaurus-1.2-data.

Then install the deb package (here 64-bit version):
lyx_1.6.7-1_amd64.deb
You can download it from here:
[https://launchpad.net/ubuntu/natty/amd64/lyx/1.6.7-1](https://launchpad.net/ubuntu/natty/amd64/lyx/1.6.7-1)
Install it with dpkg. Open terminal and go to the directory where the package lyx is.

Then run this:
```

sudo dpkg -i lyx_1.6.7-1_amd64.deb

```

---

