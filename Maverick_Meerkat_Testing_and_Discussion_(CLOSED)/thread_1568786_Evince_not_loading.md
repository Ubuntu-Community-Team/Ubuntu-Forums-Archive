---
title: "Evince not loading"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by up2early on 2010-09-05
I am unable to open pdf's as I was with Lucid using evince. When clicking on a pdf it does nothing and using Terminal:


mike@mike-laptop:~/Desktop$ evince main.pdf 

GLib-GIO-ERROR **: Settings schema 'org.gnome.Evince.Default' is not installed

aborting...
Trace/breakpoint trap (core dumped)

Thanks for any help.

---

### Post by ktp on 2010-09-05
> **up2early said:**
> I am unable to open pdf's as I was with Lucid using evince. When clicking on a pdf it does nothing and using Terminal:


mike@mike-laptop:~/Desktop$ evince main.pdf 

GLib-GIO-ERROR **: Settings schema 'org.gnome.Evince.Default' is not installed

aborting...
Trace/breakpoint trap (core dumped)

Thanks for any help.

There is open bug for this:

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/621507](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/621507)

---

### Post by up2early on 2010-09-05
Thanks, I confirmed the bug and subscribed to it.

---

### Post by up2early on 2010-09-06
Installing Empathy solves this issue. I had removed Empathy from my 10.04 as I prefer Pidgin. Adding it back to 10.10 has solved the problem with Evince.

---

### Post by roberto.tomas on 2010-09-25
> **up2early said:**
> Installing Empathy solves this issue. I had removed Empathy from my 10.04 as I prefer Pidgin. Adding it back to 10.10 has solved the problem with Evince.

```
sudo apt-get install --reinstall envince
sudo apt-get install --reinstall empathy
```does not resolve this issue for me

> **ktp said:**
> There is open bug for this:

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/621507](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/621507)

the error log in that bug report doesnt look like this one.

---

