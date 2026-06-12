---
title: "Natty install Hangs at Timezone selection"
date: 2011-01-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by deancasino on 2011-01-07
So I'm trying to install Natty Alpha (7th Jan release) in virtualbox to give it a go, but it keeps freezing at time-zone selection.

Any known work workarounds?

---

### Post by VMC on 2011-01-07
> **deancasino said:**
> So I'm trying to install Natty Alpha (7th Jan release) in virtualbox to give it a go, but it keeps freezing at time-zone selection.

Any known work workarounds?

I had the same issue. I'll try again tomorrow before reporting a bug.

---

### Post by donniezazen on 2011-01-07
Yeah Ubiquity crashes.

Update:-> I updated/upgraded the live usb and was able to install natty without any problem.

---

### Post by cariboo on 2011-01-08
The bug has already been reported, bug# [lpbug]699829[/lpbug].

---

### Post by Harry33 on 2011-01-08
> **cariboo907 said:**
> The bug has already been reported, bug# [lpbug]699829[/lpbug].

That one has been marked as fixed already.

---

### Post by cariboo on 2011-01-08
> **Harry33 said:**
> That one has been marked as fixed already.

Fix committed doesn't necessarily mean that ubiquity with the fix has been released yet.

---

### Post by keypox on 2011-01-08
> **soham_1207 said:**
> Yeah Ubiquity crashes.

Update:-

no fix for me, i tried usb install.  Doesnt work in virtual box or live desktop install (unetbootin created usb).

---

### Post by Harry33 on 2011-01-08
> **cariboo907 said:**
> Fix committed doesn't necessarily mean that ubiquity with the fix has been released yet.

Yes I know, but still the fix has been released for the bug #699289.
The fix is in the version 2.5.8 in the repos:
Here:
[https://launchpad.net/ubuntu/natty/+source/ubiquity/2.5.8](https://launchpad.net/ubuntu/natty/+source/ubiquity/2.5.8)

---

### Post by VMC on 2011-01-08
Using todays (Jan 8th) daily-live, I can now install without problems.

---

### Post by deancasino on 2011-01-09
> **VMC said:**
> Using todays (Jan 8th) daily-live, I can now install without problems.

Thanks for the update

---

