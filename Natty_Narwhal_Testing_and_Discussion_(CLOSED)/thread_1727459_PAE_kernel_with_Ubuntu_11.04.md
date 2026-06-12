---
title: "PAE kernel with Ubuntu 11.04"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by petersonja on 2011-04-12
I installed today the lastest Ubuntu Natty daily Live CD. It is works well, I really love it. But it isn't install pae kernel by default and I can't use my 4 GB ram, just 3. Is there any solution? And I think it is should be default, right?

---

### Post by grubler on 2011-04-12
maybe just to build it with pae yet


cat /proc/meminfo

---

### Post by danjahner on 2011-04-13
This will install the PAE kernel: 

```

sudo apt-get install linux-generic-pae

```

---

### Post by zika on 2011-04-13
> **danjahner said:**
> This will install the PAE kernel: 

```

sudo apt-get install linux-generic-pae

```Not on 11.04.```
:~$ sudo aptitude install linux-generic-pae
Couldn't find any package whose name or description matched "linux-generic-pae"
Couldn't find any package whose name or description matched "linux-generic-pae"
No packages will be installed, upgraded, or removed.

```

---

### Post by danjahner on 2011-04-13
Try apt-get. I did it yesterday on Natty and it worked for me.

---

### Post by zika on 2011-04-13
> **danjahner said:**
> Try apt-get. I did it yesterday on Natty and it worked for me.Of course that I tried that also... I prefer aptitude's output...```
:~$ sudo apt-get install linux-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-generic-pae
```

---

### Post by sgage on 2011-04-13
My most recent install was Monday's daily Live CD build, and it installed the PAE kernel without any fuss.

Try apt-get or synaptic. The packages are there.

---

### Post by zika on 2011-04-13
> **sgage said:**
> My most recent install was Monday's daily Live CD build, and it installed the PAE kernel without any fuss.

Try apt-get or synaptic. The packages are there.Tried synaptic... Couple of weeks ago...
I's not me that need PAE, simply I was trying to find it for a friend of mine...

---

### Post by sgage on 2011-04-13
> **zika said:**
> Tried synaptic... Couple of weeks ago...
I's not me that need PAE, simply I was trying to find it for a friend of mine...

A couple of weeks ago! I believe that dinosaurs were roaming the earth a couple of weeks ago!  :KS

Time is curiously stretched during the development cycle...

---

### Post by Harry33 on 2011-04-13
Linux-generic-pae cannot be found from 64-bit repositories.
It is of course only in 32-bit repositories.
And yes there is
- linux-image-2.6.38-8-generic-pae_2.6.38-8.42 (image)
- linux-generic-pae_2.6.38.8.22 (complete kernel)

---

### Post by zika on 2011-04-13
> **Harry33 said:**
> Linux-generic-pae cannot be found from 64-bit repositories.
It is of course only in 32-bit repositories.
And yes there is
- linux-image-generic_2.6.38-8.42 (image)
- linux-generic-pae_2.6.38.8.22 (complete kernel)
:)

---

