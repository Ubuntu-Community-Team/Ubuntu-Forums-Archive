---
title: "nvidia-common error..."
date: 2010-12-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2010-12-23
/etc/kernel/postinst.d/nvidia-common: line 8: [: too many arguments

---

### Post by miegiel on 2010-12-23
> **zika said:**
> /etc/kernel/postinst.d/nvidia-common: line 8: [: too many arguments

I don't have a nVidia card so I just
```
sudo apt-get purge nvidia-*
```
But that didn't help.

Next, assuming something went wrong downloading the packages, I did
```
sudo apt-get autoclean
```
```
sudo apt-get update
```
```
sudo apt-get dselect-upgrade
```
and the new kernel installed without a hitch.

---

### Post by zika on 2010-12-23
I do not have nvidia neither...
It is a piece of code that get invoked on everu kernel upgrade...
It's just a misspelling...
Thank You...

P.S. No, new kernel will not install OK, the same error will show up... But, it's not so important...
More important breakage is on the agenda for today, so...

---

