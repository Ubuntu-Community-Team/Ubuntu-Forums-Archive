---
title: "ubuntu 10.04 and 2 ATI Radeon 4870 Cards"
date: 2010-06-11
forum: Multimedia Software
---

### Post by djwglpuppy on 2010-06-11
Hello,
I am trying to dual boot into Ubuntu and thus far everything works great on my machine.  There is one HUGE issue.

I am running 2 Radeon 4870 Cards.  Only one adapter will show at a time.  I am used to Having 4 monitors and the max amount of Monitors it will allow me to have are two.

It does recognise the Second Adapter when I go into the Catalyst Control (it shows the option for Cross Firing) and it shows both adapters when I do:

```
aticonfig --list-adapters
```


I have tried:

```
sudo aticonfig --adapter=all --initial

sudo aticonfig --adapter=0,1 --initial

```
with no success

The closest I had was that my main two monitors showed the splash page when the other two monitors on the other adapter were displayed.  So It did switch once... But I have yet get all four monitors to work.

Someone please help me!  I just bought a new SSD so I can be a linux user outside of just my VM and this is a huge sticking point since I rely on all four monitors.

---

### Post by djwglpuppy on 2010-06-11
bump...  (Sorry I hate bumping) but I have a feeling there is a solution.... I am just not finding it

---

### Post by djwglpuppy on 2010-06-13
Wow... I am shocked no one else has two ATI Radeon Cards on their desktop.  Please someone help.... I would really love to main boot into ubuntu instead of VMWare... any help / point of direction would be great

---

### Post by kc7rwx on 2011-01-25
Did you find a solution for this? I am having the same problem with a pair of Radeon HD 5500s.

---

