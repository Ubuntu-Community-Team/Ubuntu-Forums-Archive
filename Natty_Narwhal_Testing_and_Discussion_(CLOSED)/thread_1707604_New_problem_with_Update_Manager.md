---
title: "New problem with Update Manager ?"
date: 2011-03-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jennybrew on 2011-03-15
Has anyone else seen this problem?

---

### Post by Harry33 on 2011-03-15
> **jennybrew said:**
> Has anyone else seen this problem?

Does this happen with the latest update:
update-manager 1:0.146.5 ?

---

### Post by jennybrew on 2011-03-15
> **Harry33 said:**
> Does this happen with the latest update:
update-manager 1:0.146.5 ?
Im still on the case here ..but yes its the latest update.
I will post back once I have a fix but Im not there yet :)

---

### Post by Harry33 on 2011-03-15
> **jennybrew said:**
> Im still on the case here ..but yes its the latest update.
I will post back once I have a fix but Im not there yet :)

Sorry forgot to mention, the update v. 146.5 is not yet in repos.
You can download the packages from Launchpad and then install them locally with dpkg (64-bit example):
```
sudo dpkg -i update-manager-core_0.146.5_amd64.deb update-manager_0.146.5_all.deb

```

Here:
[https://launchpad.net/ubuntu/natty/+source/update-manager/1:0.146.5](https://launchpad.net/ubuntu/natty/+source/update-manager/1:0.146.5)

---

### Post by jennybrew on 2011-03-15
Absolutely no clues available in var/log/apt/term.log  which is where I would have expected to see any issues.
However, a forced update && upgrade has done the trick and I suspect something was awry following my earlier "safe-upgrade"
Sorry I cant be more helpful if anyone else encounters this problem.

---

