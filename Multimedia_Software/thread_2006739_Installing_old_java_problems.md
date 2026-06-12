---
title: "Installing old java problems"
date: 2012-06-19
forum: Multimedia Software
---

### Post by damien750 on 2012-06-19
Hey guys. I'm having trouble installing an old version of java.

I'm trying to run a program called CGoban. It's been cobbled together over several java updates. Long story short, the best way to get all the sound working on this program is to use Java 6 update 30. Iced-tea/open JDK don't work.

However, when I try to install java via terminal, it's not letting me.

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get update

```work fine, but when I try to install...

```
 sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate
codey@goban:~$ 


```So I did some digging and found that ubuntu isn't supporting java anymore. How can I install it?


-----
Ubuntu 10.04 LTS
Compaq Presario v5000

---

### Post by damien750 on 2012-06-19
Nevermind: Downloaded the bin file from the oracle archives and installed from terminal.

---

