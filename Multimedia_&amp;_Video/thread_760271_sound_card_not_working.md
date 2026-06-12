---
title: "sound card not working"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by agrab0ekim on 2008-04-20
my sound is not working in any program on ubuntu
how can i fix this (fyi, went through the sticky, did what it said and my card is found first step, but doesnt work)

---

### Post by xc3RnbFO8P on 2008-04-20
What are the specifications of your computer?

---

### Post by agrab0ekim on 2008-04-20
[http://global.acer.com/products/notebook/as7720.htm](http://global.acer.com/products/notebook/as7720.htm)

---

### Post by xc3RnbFO8P on 2008-04-20
First this:
> sudo apt-get install linux-backports-modules

---

### Post by agrab0ekim on 2008-04-22
> **Ringi said:**
> First this:


it comes back with this

[quote=terminal window]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules[/quote]

---

### Post by xc3RnbFO8P on 2008-04-22
In Synaptic Package Manager: Settings> repositories>  Ubuntu Software check all
uncheck **cd** (source code -)
**Reload** Synaptic Package Manager
Try again.

---

