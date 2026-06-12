---
title: "installing skype"
date: 2009-01-17
forum: Multimedia Software
---

### Post by Aneta on 2009-01-17
Hi,
I have just installed Ubuntu. I have no idea about computers and that stuff, I've been always using windows but decided to switch after my friend's advice. I wanted to install skype on my computer, but I get a message I don't understand, here it is: Error dependency is not satisfiable libqt4-core. I have 8.10 Ubuntu version. Can anybody help me with this? Thanks in advance. 

Aneta

---

### Post by ibutho on 2009-01-17
Hi and welcome to the forum.

Run System -> Administration -> Synaptic and search for libqt4-core and select it for installation. An alternative would be to go to Applications -> Accessories -> Terminal and enter
```
sudo apt-get update
sudo apt-get install libqt4-core
```

---

