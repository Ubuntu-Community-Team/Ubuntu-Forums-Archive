---
title: "Software-center segmentation fault"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-03-12
Anyone else getting this?

```
$ software-center 
Segmentation fault (core dumped)
```This on a fully-updated Natty. I couldn't find an appropriate bug in Launchpad so I'll see if I get the same on my other machines.

---

### Post by mc4man on 2011-03-12
Affects certain hardware/driver combos, in progress
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219)

---

### Post by Rifester on 2011-03-12
It won't currently run for me either.   It is a bug.   And I am one of the lucky ones!

---

### Post by go7Ul1ai on 2011-03-12
I am also affected by this issue.

---

### Post by MadCow108 on 2011-03-12
many are affected by this and not only software center is broken.

the reason is known, there is currently somebody working on it, so just be patient its a very complicated issue

if you require the software to run use the workaround from the bugreport or revert to the older mesa version

---

### Post by coffeecat on 2011-03-12
> **mc4man said:**
> Affects certain hardware/driver combos, in progress
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219)

Interesting. It was on my Intel graphics machine that I discovered this. Also on my ATI graphics with the open-source driver, so that makes sense.

Glad it's been reported, which means I don't have to bother. :) When I searched this sub-forum, I couldn't find a mention of it here either. I don't suppose many alpha-testers use the software centre much, so I suppose it's hardly surprising.

> **MadCow108 said:**
>  so just be patient 

Eh? :-k

---

### Post by MadCow108 on 2011-03-12
> **coffeecat said:**
> Interesting. It was on my Intel graphics machine that I discovered this. Also on my ATI graphics with the open-source driver, so that makes sense.

Glad it's been reported, which means I don't have to bother. :) When I searched this sub-forum, I couldn't find a mention of it here either. I don't suppose many alpha-testers use the software centre much, so I suppose it's hardly surprising.



the bug has 96 duplicates, so very many noticed
also 2 threads here:
[http://ubuntuforums.org/showthread.php?t=1690717](http://ubuntuforums.org/showthread.php?t=1690717)
[http://ubuntuforums.org/showthread.php?t=1704714](http://ubuntuforums.org/showthread.php?t=1704714)

---

### Post by Cam! on 2011-03-12
This is VERY annoying. I can't open Software Center, or even any .DEB's. I made sure my Alpha 3, 32-bit 11.04 was up to date, too. I mean, I installed the thing, like **only an hour ago.**

Is there a terminal command I can do?

---

### Post by Eestlane on 2011-03-12
[http://ubuntuforums.org/showthread.php?t=1705605](http://ubuntuforums.org/showthread.php?t=1705605)

for manual deb install:
sudo dpkg -i mydeb.deb

workaround to open software-center:
LD_PRELOAD=/usr/lib/libstdc++.so.6 software-center

---

### Post by KrazyPenguin on 2011-03-12
ive been using synaptic to install things or terminal

Everything quite stable, using this on production machine lol

with all my important stuff on cloud (dropbox and evernote)

and I still have lucid on the other partition, but lucid works too good, so it is boring to use.

;-)

Forgot to mention that I installed Ubuntu Tweak and it works well in Natty for customizing and installing apps , etc

---

### Post by mc4man on 2011-03-12
If you absolutely want sc back, didn't want to revert libgl1-mesa-glx, and don't want to start from the cli you can modify the launch command. When sc updates the .desktop will be overwritten back to normal

```
gksudo gedit /usr/share/applications/ubuntu-software-center.desktop
```
Change this line
> Exec=/usr/bin/software-center %u to
```
Exec=env LD_PRELOAD=/usr/lib/libstdc++.so.6 /usr/bin/software-center %u
```

This will not allow the new 'feature' in dash to work, for that one would need to create a helper file in /usr/bin that exported the preload before calling the sc script.
(easily done, did here just because, not really needed, this should be fixed in due course

---

### Post by cariboo on 2011-03-12
Merged two threads on the same subject.

---

### Post by rbrick49 on 2011-03-12
software centre working ok on my machine
amd x64
asus motherboard 
dual coe processor
8 gb ram
6950 ati graphics

---

### Post by cdstravers on 2011-03-12
I also am experiencing the bug. The ticket that was quoted was for Ubuntu 7.04 beta, not natty.

---

### Post by mc4man on 2011-03-12
> The ticket that was quoted was for Ubuntu 7.04 beta, not natty.
look a bit closer

---

