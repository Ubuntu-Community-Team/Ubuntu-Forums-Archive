---
title: "Why is there uncheckable items in update manager?"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by JimBuntu on 2010-09-07
Hello, I am currently running Ubu 10.10 64bit and have an item in my update manager called "The Ubuntu desktop system" version 1.205 that is uncheckable.I've tried right clicking and selecting check all but nothing works. Any thoughts? Also, this has happened with every release I've been on. I've always wondered why?

Thanks

---

### Post by plucky on 2010-09-07
Read the stickies in the [Maverick Meerkat Testing and Discussion Forum](http://ubuntuforums.org/forumdisplay.php?f=385)
 will explain.

Good Luck

p.s Also post in that forum for any problems with Maverick Meerkat.

---

### Post by JimBuntu on 2010-09-07
Why is there an item called "The Ubuntu Desktop System" version 1.205, in my update manager that I can not check to be installed. It's just there. Any thoughts?

---

### Post by JimBuntu on 2010-09-07
> **plucky said:**
> Read the stickies in the [Maverick Meerkat Testing and Discussion Forum](http://ubuntuforums.org/forumdisplay.php?f=385)
 will explain.

Good Luck

p.s Also post in that forum for any problems with Maverick Meerkat.

Thanks, I was looking for that...

---

### Post by dagrump on 2010-09-07
Better question. Why are you using update mangler? 
It would be reasonable to assume it has unmet dependences. So it can't be installed. Update mangler likes to offer partial updates, & some folks just can't resist.
As long as as it doesn't want to remove stuff it's safe, well most of the time.

---

### Post by Iowan on 2010-09-07
Threads merged.

---

### Post by cariboo on 2010-09-07
I had docky and the ubuntu-desktop meta package held back, I just marked them for installation in synaptic to install them. During a testing phase it is advised to use either the terminal or synaptic to do your upgrades, that way you can see what will be removed and what will be installed, it will also tell you why a package is held back.

---

### Post by JimBuntu on 2010-09-08
> **cariboo907 said:**
> I had docky and the ubuntu-desktop meta package held back, I just marked them for installation in synaptic to install them. During a testing phase it is advised to use either the terminal or synaptic to do your upgrades, that way you can see what will be removed and what will be installed, it will also tell you why a package is held back.

Ok, so what is the code to upgrade in terminal?

---

### Post by JimBuntu on 2010-09-08
> **dagrump said:**
> Better question. Why are you using update mangler? 
It would be reasonable to assume it has unmet dependences. So it can't be installed. Update mangler likes to offer partial updates, & some folks just can't resist.
As long as as it doesn't want to remove stuff it's safe, well most of the time.

I'm sure it's not that bad... Why would it be included in Ubuntu if it sucks so bad? Maybe it's not that they can't resist, but rather they don't know any better.

---

### Post by Peter09 on 2010-09-08
The code to update from a terminal is
 
```
sudo apt-get update
```
 
to update from the repositories
 
followed by
 
```
sudo apt-get upgrade
```
 
to upgrade your system to reflect the repository changes.

---

### Post by JimBuntu on 2010-09-08
> **Peter09 said:**
> The code to update from a terminal is
 
```
sudo apt-get update
```
 
to update from the repositories
 
followed by
 
```
sudo apt-get upgrade
```
 
to upgrade your system to reflect the repository changes.

Thanks, I knew that once before but kinda forgot all that stuff... Just trying to get back into it.

---

### Post by coffeecat on 2010-09-08
> **JimBuntu said:**
> I'm sure it's not that bad... Why would it be included in Ubuntu if it sucks so bad? Maybe it's not that they can't resist, but rather they don't know any better.

Did you find this?

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

Update Manager doesn't 'suck so bad'. All is explained in that sticky :)

---

### Post by JimBuntu on 2010-09-08
> **coffeecat said:**
> Did you find this?

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

Update Manager doesn't 'suck so bad'. All is explained in that sticky :)

Just glanced at it... Read the part that says the Update Manager is suppose to be used for stable releases... This is the first time im using a dev release... So, now i know. THanks

---

### Post by ranch hand on 2010-09-08
You should read all of the stickies, at least the first post in each.  We are not talking glancing through it here.  Read the buggers.

There is very important info in each of them that you will need at some point.

Synaptic is a very good place to go to find out exactly what is going to change and why.  Ubuntu desktop upgrade will remove  a file and install one.  It appears we are waiting for an upgrade for the one that this upgrade would remove so that every thing can work.

---

