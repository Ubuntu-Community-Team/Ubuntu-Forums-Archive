---
title: "Sound issues"
date: 2009-07-19
forum: Multimedia Software
---

### Post by sthrnpagan on 2009-07-19
I just installed Ubuntu and I am enjoying it. BUT, when i tested my sound all i heard was a lound continues sound. What is this and how do I fix?

---

### Post by khelben1979 on 2009-07-19
I recommend you take a look how your sound is configured through the [Alsa mixer]("http://en.wikipedia.org/wiki/Alsamixer") application.

```
sudo apt-get install alsamixergui
```
if it's not installed in the system.

---

### Post by sthrnpagan on 2009-07-19
> **khelben1979 said:**
> I recommend you take a look how your sound is configured through the [Alsa mixer]("http://en.wikipedia.org/wiki/Alsamixer") application.

```
sudo apt-get install alsamixergui
```
if it's not installed in the system.

I typed in the command you suggested and it returned:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixergui

is this a problem?

---

### Post by khelben1979 on 2009-07-19
Try to search for alsamixer in [Synaptic]("http://en.wikipedia.org/wiki/Synaptic_package_manager") instead to see if Ubuntu can find it.

---

