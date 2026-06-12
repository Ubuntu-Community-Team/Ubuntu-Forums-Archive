---
title: "What happened to the xswat ppa ?"
date: 2011-02-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2011-02-20
Hi

According to this page , [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

there doesnt seem to be any new fglrx driver yet though catalyst 11.2 is out.11.1  also didnt come through if i remember correctly.

I have been downloading from the Amd site directly last 2 releases.

---

### Post by Harry33 on 2011-02-20
> **rajeev1204 said:**
> Hi

According to this page , [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

there doesnt seem to be any new fglrx driver yet though catalyst 11.2 is out.11.1  also didnt come through if i remember correctly.

I have been downloading from the Amd site directly last 2 releases.

I believe the X Updates PPA is OK.
Concerning those proprietary drivers, they are perhaps waiting for AMD to release a version that supports xserver 1.10 (at least rc2).
And for NVidia (nvidia-current) i think it is about the same business. However, the version in that PPA (270.26) is the latest there is around.

---

### Post by rajeev1204 on 2011-02-20
> **Harry33 said:**
> I believe the X Updates PPA is OK.
Concerning those proprietary drivers, they are perhaps waiting for AMD to release a version that supports xserver 1.10 (at least rc2).
And for NVidia (nvidia-current) i think it is about the same business. However, the version in that PPA (270.26) is the latest there is around.


It is not there for maverick either, check fglrx date of latest package it is 18 december which is even before 10.12.

That is why i was wondering.

---

### Post by Harry33 on 2011-02-20
> **rajeev1204 said:**
> It is not there for maverick either, check fglrx date of latest package it is 18 december which is even before 10.12.

That is why i was wondering.

You are right about that.
But not even the latest fglrx from AMD does support xserver 1.10.

---

### Post by rajeev1204 on 2011-02-20
> **Harry33 said:**
> .
But not even the latest fglrx from AMD does support xserver 1.10.


Yes true that.Iam waiting for amd to release support for it soon so i can try unity.Iam sure they are testing with unity currently so as to make sure they have a working fglrx with this new shell for ubuntu.

Unity could present a new challenge to the proprietary drivers.

---

### Post by Harry33 on 2011-02-20
> **rajeev1204 said:**
> Yes true that.Iam waiting for amd to release support for it soon so i can try unity.Iam sure they are testing with unity currently so as to make sure they have a working fglrx with this new shell for ubuntu.

Unity could present a new challenge to the proprietary drivers.

Unity will challenge at least AMD/ATI proprietary drivers.
This is because of Compiz.

---

