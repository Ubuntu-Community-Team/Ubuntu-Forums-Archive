---
title: "need to install evidia on 8.04.."
date: 2008-06-25
forum: Multimedia Software
---

### Post by Mia_tech on 2008-06-25
after updating my system the nvidia driver is gone, but the tutorial I've seen are for versions up to 7.10...has anyone know how could I install in hardy?...

any help appreciated

thanks

---

### Post by Tux Aubrey on 2008-06-25
Hi Mia-tech

I use EnvyNG-gtk which is now in the repos.  Use Synaptic or just:

```
sudo apt-get install envyng-gtk
```

This will also give you the ability to install, reinstall and tweak your nvidia driver (the official one) settings from a gui.

You will probably need to uninstall your existing nvidia driver first.  You can read about it [here]("http://www.albertomilone.com/envyngfaq.html").  A real life saver!

---

### Post by chewearn on 2008-06-25
I find that, unless you are looking the latest/greatest driver, or faced some sort of problems, the one from the repositories is easier to maintain.  To install:
System > Administration > Hardware Drivers

.

---

### Post by Mia_tech on 2008-06-25
> **AstalaVista said:**
> I find that, unless you are looking the latest/greatest driver, or faced some sort of problems, the one from the repositories is easier to maintain.  To install:
System > Administration > Hardware Drivers

.

That's the one, I had installed, but after updating my system it disappear...now I installed the nvidiang-gtk, and got it working again, what is the difference one from the other?

thanks

---

