---
title: "Ubuntu won't start with my wireless pci card"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by Valestrom on 2011-04-22
I'm using ubuntu 10.10 I recently had problems with my 10.04 install with the card but I could at least start it. Now I cannot start it, even after a fresh install of 10.10 it works fine if I don't have the card in, but as soon as I put it in I just get a blank blue/black screen like he screen right before it goes to desktop. I have tried to disable my onboard network card and a bunch of other hinge with no avail. Please, any help would be helpful. Card is: Zonet ZEW1605

---

### Post by Valestrom on 2011-04-22
.

---

### Post by josephmills on 2011-04-22
if I was to put a new lung in your body would it work alright?

---

### Post by Valestrom on 2011-04-22
Good point. I have a cd with a driver but it's in an exe file which I would have to have wine to use correct? So any help on how I could get it to recognize it or whatever would be helpful.

---

### Post by Valestrom on 2011-04-22
So while going through the log viewer I found some more info that could be helpful.

Valestrom modem-manager: (tty/ttys2): ports parent platform driver is not whitelisted
Valestrom modem-manager: (tty/ttys3): ports parent platform driver is not whitelisted
Valestrom modem-manager (tty/ttys0): could not get ports parent device
Valestrom modem-manager (tty/ttys0): could not get ports parent device
Valestrom kernel: [ 27.024039] eth0: no IPv6 routers present.



So any help would be greatly appreciated.

---

### Post by josephmills on 2011-04-22
ok if you want to use a native windows driver you have to use ndiswrapper ive got an idea. make sure all of you pci cards are in and Please put in a ubuntu live cd in and run from boot. then open the terminal and type in ```
sudo lshw -C network 
```
it takes a bit to load but if it dosen't load then try 
```

lspci

```
could we also see a 
```

free -m 

```
and 
```

cat /proc/cpuinfo 

```
Thanks and sorry about the late response ohh make sure that you post all the things here and welcome to Ubuntuforums

---

