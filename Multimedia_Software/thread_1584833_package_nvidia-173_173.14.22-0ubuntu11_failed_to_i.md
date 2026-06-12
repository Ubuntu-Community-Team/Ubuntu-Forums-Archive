---
title: "package nvidia-173 173.14.22-0ubuntu11 failed to install/upgrade: subprocess installe"
date: 2010-09-29
forum: Multimedia Software
---

### Post by jonny_bowes on 2010-09-29
Hi,
After a fresh install of Lucid my Nvidia drivers wont install.

package nvidia-173 173.14.22-0ubuntu11 failed to install/upgrade: subprocess installed post-installation script returned error exit status 10

I have submitted the following Bug

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/646449](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/646449)

No help as of yet so I was Hoping someone here can save me

---

### Post by jonny_bowes on 2010-09-30
Bump :-)

---

### Post by jonny_bowes on 2010-10-01
Can someone please help??

How long should I expect to wait for my Bug submitted to be looked at?

---

### Post by sikander3786 on 2010-10-01
Hi.

Can you actually successfully update for now?

```

sudo apt-get update

```

Post the errors encountered, if any.

---

### Post by jonny_bowes on 2010-10-05
> **sikander3786 said:**
> Hi.

Can you actually successfully update for now?

```

sudo apt-get update

```

Post the errors encountered, if any.

I can update my system but the nvidia drivers wont install.

Ive started some trouble shooting in the bug report with another person.I would like if you can help me too:)

In this link is the full list of whats been done so far

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/646449](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/646449)

---

### Post by jonny_bowes on 2010-10-08
I FIXED IT!!! Woooohoooo

the package was failing on the 2.6.32-24-generic kernel so I installed the 2.6.32.25.27 one and then removed the failing one and fixed....so far as i can see.

YEAY ME!!

---

