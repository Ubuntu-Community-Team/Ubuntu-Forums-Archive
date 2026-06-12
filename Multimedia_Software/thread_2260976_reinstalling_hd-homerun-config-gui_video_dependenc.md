---
title: "reinstalling hd-homerun-config-gui video dependency failure problem?"
date: 2015-01-15
forum: Multimedia Software
---

### Post by JRinWV on 2015-01-15
Hi,

I reinstalled Ubuntu 14.04 last night and this morning when trying to reinstall HD-Homerun-config-gui (which we have used for years now) using Ubuntu Software Center it failed due to dependency problem. 

I did this on a leptop yesterday with no problems. 

The error message was "hdhomerun-config-gui: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed"

While I can poke around with xterm and sudo - I don't really know what to tell it to do for this. Any advice appreciated! Spouse wants to watch the old movies! Help   ;-)

---

### Post by mc4man on 2015-01-15
Try 
```
sudo apt-get update
```
Then see if it will install

---

### Post by JRinWV on 2015-01-15
Mc4Man:

Thanks!  That worked.  So simple, I ask what did "apt-get update" actually do inside my box. I watched many lines of ?downloads? fly by in the xterm window, was I downloading actual OS code, or what?

Anyways, thanks again!
JR

---

### Post by mc4man on 2015-01-15
> **JRinWV said:**
> Mc4Man:

Thanks!  That worked.  So simple, I ask what did "apt-get update" actually do inside my box. I watched many lines of ?downloads? fly by in the xterm window, was I downloading actual OS code, or what?

Anyways, thanks again!
JR
Right after a new install you need to update your sources once  before trying to install anything. So that's what the command did.

---

