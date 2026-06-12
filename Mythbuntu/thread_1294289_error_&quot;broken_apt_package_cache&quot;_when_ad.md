---
title: "error &quot;broken apt package cache&quot; when adding frontend role"
date: 2009-10-18
forum: Mythbuntu
---

### Post by otanger on 2009-10-18
Hi,
I installed mythbuntu and could set up a "backend role" for my PC (ubuntu jaunty already was installed before). I now want to setup a "frontend role" and get the warning 
> broken apt package cache
Check your package list for universe, multiverse and main.
Perform a package list update as well.
The details below say:

> E:Kann Probleme nicht korrigieren, Sie haben gehaltene defekte Pakete.
translated by me to EN: "E: cannot correct problems, you have defect packages")
I have updated my package list, and a synaptic "repair broken packages" does not help.
Thanks,
Ole

---

### Post by ian dobson on 2009-10-18
Hi,

Maybe try:-

apt-get clean
apt-get autoclean
apt-get purge

This should cleanout your apt cache.

Regards
Ian Dobson

---

