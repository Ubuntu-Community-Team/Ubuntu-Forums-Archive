---
title: "need help installing Cinelerra on ubuntu computer"
date: 2011-01-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mattgeb84 on 2011-01-22
please someone help me, i really want to install cinelerra on my ubuntu computer but i cant for the life of me figure out how, ive been to there website and have tried following there instructions but it just doesnt seem to work. im a novice user i have no idea how to update the repositories or anything like that, can someone please help me figure out how to install this software on my computer 
i went to  "about ubuntu" under my system menu and it says im using ubuntu 11.04 Natty Narwhal

please help

---

### Post by zvacet on 2011-01-23
Let be sure that you are running Natty,because it is still in development and it is not recommended for every day use (yet).In applications>accessories>terminal type

lsb_release -a

and you will see witch version you are running.For adding ppa read on [this page]("https://launchpad.net/~cinelerra-ppa/+archive/ppa") Read about installing (blue letters) and after that Technical details about this PPA (green letters) and you will know how to add repo.

---

### Post by Script Warlock on 2011-01-23
> **mattgeb84 said:**
> please someone help me, i really want to install cinelerra on my ubuntu computer but i cant for the life of me figure out how, ive been to there website and have tried following there instructions but it just doesnt seem to work. im a novice user i have no idea how to update the repositories or anything like that, can someone please help me figure out how to install this software on my computer 
i went to  "about ubuntu" under my system menu and it says im using ubuntu 11.04 Natty Narwhal

please help

cinelerra is working fine in 10.10...

---

### Post by coldraven on 2011-01-23
In case you don't know, Ubuntu releases use the year and month and a nickname.
So release 10.10 means it was the 2010 October release (Maverick Meerkat)
8.04 would be 2008 April (Hardy Heron)
It follows that 11.04 (Natty Narwhal) is going to be released next April and is only for experienced hackers for testing until it is eventually ready for regular users.
I recommend that you use 10.10 in the meantime.

---

### Post by overdrank on 2011-01-23
Moved to Natty Narwhal Testing and Discussion

---

### Post by mattgeb84 on 2011-01-23
i actually just figured it out i have it installed and working,
also i dont know how i ended up with 11.04 installed, i had originally downloaded 10.10 x86 and burnt it to a bootable disk i installed it, one day when i upgraded it through the ubuntu upgraded i ended up with 11.04 installed

---

### Post by coffeecat on 2011-01-23
> **mattgeb84 said:**
> i had originally downloaded 10.10 x86 and burnt it to a bootable disk i installed it, one day when i upgraded it through the ubuntu upgraded i ended up with 11.04 installed

Maybe not. There is a bug that sometimes causes an updated 10.10 to be wrongly identified as 11.04 in 'About Ubuntu'.

Please run the terminal command that zvacet suggested:

```
lsb_release -a
```

---

