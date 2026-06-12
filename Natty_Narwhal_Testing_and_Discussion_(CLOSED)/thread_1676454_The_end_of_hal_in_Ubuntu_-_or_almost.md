---
title: "The end of hal in Ubuntu - or almost"
date: 2011-01-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-27
Today Martin Pitt uploaded packages like Totem, Rhythmbox, Gimp and Nut.
The reason was to drop build dependencies to hal and libhal.
Also the libhal1 dependency of Gimp has now been dropped.

Only thing that needed to be done was to let nut-hal-drivers still depend on libhal1.
So in most setups libhal1 may now be removed.

---

### Post by dino99 on 2011-01-27
yes i've seen that too, cleaning the builds is a good idea, wonder how i can check all the packages still depending on hal (recursively if possible)

---

### Post by Harry33 on 2011-01-27
> **dino99 said:**
> yes i've seen that too, cleaning the builds is a good idea, wonder how i can check all the packages still depending on hal (recursively if possible)

Open synaptic, then mouse over hal (or libhal1 too), one click, then choose Properties buttons and select "Dependencies" tab and from there "Dependants".
Then you will see the list of all packages (from the sources.list) depending on selected package.

---

### Post by dino99 on 2011-01-27
> **Harry33 said:**
> Open synaptic, then mouse over hal (or libhal1 too), one click, then choose Properties buttons and select "Dependencies" tab and from there "Dependants".
Then you will see the list of all packages (from the sources.list) depending on selected package.

what i meant is: which package(s) still have "hal" as a dependency, so my initial question :) (not hal dependencies)

---

### Post by NCLI on 2011-01-27
> **dino99 said:**
> what i meant is: which package(s) still have "hal" as a dependency, so my initial question :) (not hal dependencies)

Yes, and that's what you get if you do as he said :p

---

### Post by dino99 on 2011-01-27
> **NCLI said:**
> Yes, and that's what you get if you do as he said :p

are you sure ? you might check first i think.

---

### Post by webme on 2011-01-27
> **NCLI said:**
> Yes, and that's what you get if you do as he said :p

You're right!!!

This is on Maverick, the point is the same on Natty, too!

---

### Post by Harry33 on 2011-01-27
> **webme said:**
> You're right!!!

This is on Maverick, the point is the same on Natty, too!

Exactly, but in Maverick the subtitle is "Dependent Packages" and in Natty it is "Dependants".

The point here is that Properties tab first lists "Dependencies", but you can select also "Dependants", "Dependencies of the latest version" and "Provided Packages".

"Provided packages" are so called "virtual packages", which are widely used to set ABI naming.

---

### Post by dino99 on 2011-01-27
sorry guys its to late on my end :( , i've finally seen this switch to get dependency of packages

---

### Post by webme on 2011-02-07
Network-manager ditched HAL, too.

---

### Post by t1497f35 on 2011-02-08
I installed yesterday's x64 daily build and libhal1 isn't even installed by default.

---

### Post by zika on 2011-02-08
> **t1497f35 said:**
> I installed yesterday's x64 daily build and libhal1 isn't even installed by default.No hal here, too...
(64 bit)

---

