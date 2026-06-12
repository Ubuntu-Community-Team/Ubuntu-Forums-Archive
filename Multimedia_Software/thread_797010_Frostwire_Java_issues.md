---
title: "Frostwire Java issues"
date: 2008-05-16
forum: Multimedia Software
---

### Post by chefdeb on 2008-05-16
I'm having a problem getting Frostwire to work.  I have Sun Java 6 but the message I'm getting is, as follows:

Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)


I'm rather new at this and would appreciate any help I you could offer to solve this.  Frostwire simply won't launch.  Thanks!

ChefDeb

---

### Post by cor2y on 2008-05-17
[FONT=monospace]look here for the fix.
[http://ubuntuforums.org/showpost.php?p=4770978&postcount=11](http://ubuntuforums.org/showpost.php?p=4770978&postcount=11)
[/FONT]

---

### Post by gandaran on 2008-05-17
are you sure you have sun-java6-plugin installed? looks like you have open java installed not sun java!

---

### Post by domness on 2008-05-17
It seems that alot people are getting this error when trying to use Frostwire.

---

### Post by atomkarinca on 2008-05-17
First install jre6:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

then select it to be used:

```
sudo update-alternatives --config java
```

select the one with jre6.

---

### Post by chefdeb on 2008-05-17
Thank you so much, Atomkarinca! You are fabulous! It worked like a charm.  Thank you everybody who responded.  If you are having trouble with the new Frostwire in Hardy, Atomkarinca's solution is a winner!  Big smooch for you!

---

### Post by atomkarinca on 2008-05-17
No problem mate, glad I could help.

---

