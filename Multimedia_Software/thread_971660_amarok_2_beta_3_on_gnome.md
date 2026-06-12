---
title: "amarok 2 beta 3 on gnome?"
date: 2008-11-05
forum: Multimedia Software
---

### Post by xboxbman on 2008-11-05
I've been using amarok for some time and love it.  I recently saw that there is a new beta of amarok 2, and would like to install it.  Unfortunately, I can't figure it out.  Amarok is native to KDE, and I use GNOME.  I've tried to compile it using the given instructions, but no dice.  If anyone could give me some pointers, that'd me greatly appreciated.

---

### Post by RobotJox on 2008-11-05
i would like to know too - tried following these instructions: [http://www.kubuntu.org/news/amarok-2-beta-3](http://www.kubuntu.org/news/amarok-2-beta-3) - but they don't seem to work for Ubuntu. I can't find amarok2 in synaptic even after adding the suggested repository?

---

### Post by xboxbman on 2008-11-05
> **RobotJox said:**
> i would like to know too - tried following these instructions: [http://www.kubuntu.org/news/amarok-2-beta-3](http://www.kubuntu.org/news/amarok-2-beta-3) - but they don't seem to work for Ubuntu. I can't find amarok2 in synaptic even after adding the suggested repository?

my exact problem

---

### Post by polyopath on 2008-11-06
Hello,

The repository are:

      - For Gusty Gibbon 7.10 :

```
deb http://ppa.launchpad.net/project-neon/ubuntu gutsy main
```

      - For Hardy Heron 8.04 :

```
deb http://ppa.launchpad.net/project-neon/ubuntu hardy main
```

      - For Intrepid Ibex 8.10 :

```
deb http://ppa.launchpad.net/project-neon/ubuntu intrepid main
```


Do:

```
$sudo apt-get update
```

And the package is:

```
amarok-nightly
```

See-ya...

---

### Post by Yellow Pasque on 2008-11-06
You should be able to run amarok2 in Ubuntu/GNOME if you have kdelibs5 package.

---

### Post by olavjunior on 2008-11-10
The instructions here [http://www.kubuntu.org/news/amarok-2-beta-3](http://www.kubuntu.org/news/amarok-2-beta-3) worked fine for me!

---

