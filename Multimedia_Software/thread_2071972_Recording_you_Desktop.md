---
title: "Recording you Desktop"
date: 2012-10-16
forum: Multimedia Software
---

### Post by Larstpoint on 2012-10-16
Hi everyone,

I was wondering if you could record you desktop on Kubuntu like you can on Lubuntu? If you can how?

---

### Post by cottfcfan on 2012-10-17
Recordmydesktop is in the repos.
It will pull in a few gnome dependencies, but works well.

---

### Post by oldos2er on 2012-10-17
> **Larstpoint said:**
> Hi everyone,

I was wondering if you could record you desktop on Kubuntu like you can on Lubuntu? If you can how?

```
sudo apt-get update; sudo apt-get install recordmydesktop; recordmydesktop
``` If you want the Gnome GUI, install **gtk-recordmydesktop** instead.

---

