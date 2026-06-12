---
title: "Autoremove in Maverick?"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Madspyman on 2010-08-31
Not sure if this has been reported, but apt-get autoremove doesn't seem to be working.

---

### Post by dino99 on 2010-08-31
what issue exactly, seem normal here.

---

### Post by simbloke on 2010-08-31
I no longer see any auto-removable packages in Synaptic, even if I set all but the ubuntu-desktop/standard/minimal to auto installed.

Also, every update sets the updated packages to manually installed.

Sim

---

### Post by mc4man on 2010-08-31
possibly this bug
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/616407](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/616407)

---

### Post by simbloke on 2010-08-31
> **mc4man said:**
> possibly this bug
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/616407](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/616407)

Yes that's it. Didn't see that when I was looking through bug reports.

---

### Post by MacUntu on 2010-08-31
Here's a workaround (NOT a fix):
```
echo "APT::NeverRemove { \"dpkg\"; };" | sudo tee /etc/apt/apt.conf.d/99autoremovebug
```
Once this is fixed, just remove the file '/etc/apt/apt.conf.d/99autoremovebug'.

---

### Post by Madspyman on 2010-09-01
Aptitude still seems to work, so I'll just use that for the time being.

---

### Post by simbloke on 2010-09-01
> **MacUntu said:**
> Here's a workaround (NOT a fix):
```
echo "APT:NeverRemove { \"dpkg\"; };" | sudo tee /etc/apt/apt.conf.d/99autoremovebug
```
Once this is fixed, just remove the file '/etc/apt/apt.conf.d/99autoremovebug'.

Shouldn't there be two colons after APT?

---

### Post by MacUntu on 2010-09-01
Thought I typed two. Thanks for the hint!

---

### Post by simbloke on 2010-09-01
> **MacUntu said:**
> Thought I typed two. Thanks for the hint!

I've just tried it and removed plenty of old packages so thanks!

---

### Post by jppr on 2010-09-01
> **Madspyman said:**
> Not sure if this has been reported, but apt-get autoremove doesn't seem to be working.

I have installed Bleachbit, that is easy and works well

---

