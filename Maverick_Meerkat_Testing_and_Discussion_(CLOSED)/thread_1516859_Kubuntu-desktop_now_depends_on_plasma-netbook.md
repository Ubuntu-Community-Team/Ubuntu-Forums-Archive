---
title: "Kubuntu-desktop now depends on plasma-netbook??"
date: 2010-06-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xebian on 2010-06-24
While Ubuntu is trying to get rid of some stuff Kubuntu is trying to add more to the bloat.

It doesn't make sense to install netbook* stuff on a desktop???  What are they thinking?

In todays update
```


The following NEW packages will be installed:
  blogilo{a} kanagram{a} kdeedu-kvtml-data{a} kdegames-card-data{a} kdegames-mahjongg-data{a} kdiamond{a} 
  kmahjongg{a} kmines{a} kpat{a} kreversi{a} krosspython{a} ksudoku{a} ktouch{a} 
  kubuntu-netbook-default-settings{a} libkdeedu4{a} libkdegames5{a} lskat{a} parley{a} plasma-netbook{a} 
The following packages will be upgraded:

```

---

### Post by descendent87 on 2010-06-25
The only thing I can think of is that they're trying to combine the desktop and netbook versions so that it's a single image that can detect the system it's running on and switch to the correct version

---

### Post by michaelmartin007 on 2010-06-26
> **xebian said:**
> While Ubuntu is trying to get rid of some stuff Kubuntu is trying to add more to the bloat.

It doesn't make sense to install netbook* stuff on a desktop???  What are they thinking?

In todays update
```


The following NEW packages will be installed:
  blogilo{a} kanagram{a} kdeedu-kvtml-data{a} kdegames-card-data{a} kdegames-mahjongg-data{a} kdiamond{a} 
  kmahjongg{a} kmines{a} kpat{a} kreversi{a} krosspython{a} ksudoku{a} ktouch{a} 
  kubuntu-netbook-default-settings{a} libkdeedu4{a} libkdegames5{a} lskat{a} parley{a} plasma-netbook{a} 
The following packages will be upgraded:

```

I have the same problem. I have kubuntu-desktop but just today if I want to update the kubuntu-desktop package it shall install all of that packages.
Is it a bug in kubuntu-destop by installing plasma-netbook?
Is it the way kubuntu shall work from now on by installing kubuntu-desktop and kubuntu-netbook together?

---

### Post by seeker5528 on 2010-06-26
> **michaelmartin007 said:**
> I have the same problem. I have kubuntu-desktop but just today if I want to update the kubuntu-desktop package it shall install all of that packages.
Is it a bug in kubuntu-destop by installing plasma-netbook?

Most of the new stuff are recommends, when choosing not to treat recommends as dependencies, the plasma-netbook stuff was the only new stuff installed, and seems not to take up much room.

> Is it the way kubuntu shall work from now on by installing kubuntu-desktop and kubuntu-netbook together?

That would be my guess, since the changelog said something about starting plasma-netbook automatically if a smaller screen was detected.

Later, Seeker

---

### Post by michaelmartin007 on 2010-06-26
> **seeker5528 said:**
> Most of the new stuff are recommends, when choosing not to treat recommends as dependencies, the plasma-netbook stuff was the only new stuff installed, and seems not to take up much room.



That would be my guess, since the changelog said something about starting plasma-netbook automatically if a smaller screen was detected.

Later, Seeker

Thanks for the reply.

---

