---
title: "Java"
date: 2013-01-21
forum: Multimedia Software
---

### Post by captjack on 2013-01-21
[FONT=Comic Sans MS][COLOR=Purple][SIZE=2]I am trying to put "Java" [SIZE=2]on both my Dell [SIZE=2]laptop and Dell desktop. I have Lubuntu on both[SIZE=2].  I go to the Java site and I download what I believe is the correct Java for Linu[SIZE=2]x. I [SIZE=2]find the dow[SIZE=2]nload on the computer but I don't[SIZE=2] know how to install it. There is no install package. I am confused. Now I have these Java programs on both machines but I can't open either one of them. If they are wrong, then how do I delete the files. 

[SIZE=2]Thanks[/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/FONT]

---

### Post by ajgreeny on 2013-01-21
Have you tried the openjdk versions of java rather than the oracle versions?  I have not had oracle-java (previously sun-java) for a long time and find that everything works just as well.

The openjdk-7 and 6 versions are in the repos so can be installed just like any other package.

---

### Post by jerome1232 on 2013-01-21
If it's Oracles Java that you need, then follow this strikingly simple method.

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)


Unfortunately due to Oracles restrictions, Oracle can't be packaged and included in the Ubuntu repos. But that method adds a ppa that runs a script to download, install it, and keep it updated via the package manager.

---

### Post by captjack on 2013-01-27
I have the program on the lap top. I see it in the files. But i don't know how to install it. I am NOT computer savvy, so I need instructions that are easy to follow. Thank you

---

### Post by claracc on 2013-01-27
Here, [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java), you have a comprenhensive guide to install different java packages (oracle, openjdk,..).

Here, [http://askubuntu.com/questions/48468/how-do-i-install-java](http://askubuntu.com/questions/48468/how-do-i-install-java), you have a step by step guide to install openjdk java as you have been advised.

---

### Post by jerome1232 on 2013-01-27
From the page I linked:

First open a terminal, (press ctrl+alt+t)

Copy and pase the code below into your terminal. Enjoy.

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

