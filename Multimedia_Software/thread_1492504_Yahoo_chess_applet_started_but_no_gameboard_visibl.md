---
title: "Yahoo chess applet started but no gameboard visible"
date: 2010-05-24
forum: Multimedia Software
---

### Post by savvavas on 2010-05-24
I wanted to play yahoo chess, but when I joined a chess game, i got a blank gray window with the words saying applet started and that is all. What do I need to do? I am using ubuntu 9.04 i think. On a system
76 computer.

---

### Post by Yellow Pasque on 2010-05-24
The classic Yahoo chess uses Java, so you can update your Java packages from: [https://launchpad.net/~jauntybleed/+archive/ppa/+packages](https://launchpad.net/~jauntybleed/+archive/ppa/+packages)
Even if you don't use Java for chess, it's a good idea to run the latest Java plugin for security reasons.

You can either add the PPA as a source following the directions on the page, or you can download the sun-java6 packages you need (-bin, -plugin, -jre, and maybe -fonts) individually.
```
cd <your download directory>
sudo dpkg -i sun-java6*
```

---

