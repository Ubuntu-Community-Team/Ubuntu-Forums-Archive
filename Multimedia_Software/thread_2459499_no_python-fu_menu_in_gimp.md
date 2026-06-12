---
title: "no python-fu menu in gimp"
date: 2021-03-19
forum: Multimedia Software
---

### Post by bjlockie on 2021-03-19
I'm trying to write a gimp plugin in python.
There is supposed to be a Filters/Python fu menu but I don't have that.

---

### Post by deadflowr on 2021-03-20
What version of Lubuntu, and what version of gimp?

---

### Post by bjlockie on 2021-03-20
lubuntu 20.10
GIMP 2.10.18

---

### Post by bjlockie on 2021-03-20
lubuntu 20.10
GIMP 2.10.18

I think it is a Python3 thing but I don't know why it still should be. :-(
[https://discuss.pixls.us/t/gimp-python-not-available-in-ubuntu-20-04/17769/10](https://discuss.pixls.us/t/gimp-python-not-available-in-ubuntu-20-04/17769/10)

---

### Post by bjlockie on 2021-04-03
Does anyone know why I'm missing the python-fu menu?

---

### Post by deadflowr on 2021-04-03
I've come to realize I have not used the apt version of gimp for sometime, and have installed either the snap or flatpak versions.
Both of which have the python-fu option.
I guess a 3rd option is the appimage option, but I've never used that one.

In terms of the apt version you might look into the franken-fix posted here:
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1881684/comments/3]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1881684/comments/3")
from this report: [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1881684]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1881684")


That said, you might look at the alternatives,

If you want to try the snap version just install it like
```
snap install gimp
```

If you want to try the flatpak version look over this: 
[https://flathub.org/apps/details/org.gimp.GIMP]("https://flathub.org/apps/details/org.gimp.GIMP")
Follow the flatpak setup guide here: [https://flatpak.org/setup/Ubuntu/]("https://flatpak.org/setup/Ubuntu/")

Or if you want to see what appimage is about look here: [https://appimage.github.io/GIMP/]("https://appimage.github.io/GIMP/")

And there are probably other options too, but these are the more known and common options.

Hope it helps.

---

