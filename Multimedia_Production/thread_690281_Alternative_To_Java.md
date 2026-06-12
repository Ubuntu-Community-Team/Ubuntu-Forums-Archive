---
title: "Alternative To Java"
date: 2008-02-07
forum: Multimedia Production
---

### Post by tcoffeep on 2008-02-07
I don't even know if this is the right section for this, but I guess I'll find out.

I've been looking for quite some time for a 'free' alternative (free in the R. Stallman sense) to Java. Has it been done yet or are we still working on that?

---

### Post by PmDematagoda on 2008-02-07
Have you had a look at Iced Tea? I think Iced Tea would be free in the "R. Stallman sense" since it is made from OpenJDK.

---

### Post by tcoffeep on 2008-02-07
Would you possibly have a link to it's software page? I've just tried looking for it, and I can't seem to find it.

---

### Post by tcoffeep on 2008-02-07
Never mind. I found it. Has anyone ever tried it yet?

---

### Post by PmDematagoda on 2008-02-07
I have tried it out, it works well on general, but it does have it's problems.

Also since you have Gutsy, you should be able to install Iced Tea using:-
```
sudo apt-get install icedtea-java7-jre
```

---

### Post by meho_r on 2008-02-07
Working for me flawlessly (64bit Ubuntu). Keep in mind that some guys suggest that sun's java should be removed before installing IcedTea

---

### Post by tcoffeep on 2008-02-07
I'm guessing conflicts or something?

---

### Post by meho_r on 2008-02-07
It seems that Sun's java has some kind of  "preference" over IcedTea. So, if Sun's java doesn't work and you install IcedTea nothing will happen, java might not work. I personally didn't test it, simply trashed Java and install IcedTea :)

---

### Post by PmDematagoda on 2008-02-07
> **meho_r said:**
> Working for me flawlessly (64bit Ubuntu). Keep in mind that some guys suggest that sun's java should be removed before installing IcedTea

Actually Iced Tea works well, even with Sun Java installed. But one thing you have to do to use Iced Tea for Java is:-
```
sudo update-alternatives --config java
```

---

### Post by eye208 on 2008-02-07
> **tcoffeep said:**
> I've been looking for quite some time for a 'free' alternative (free in the R. Stallman sense) to Java.
Java is free.

[http://en.wikipedia.org/wiki/OpenJDK](http://en.wikipedia.org/wiki/OpenJDK)

---

### Post by tcoffeep on 2008-02-07
The link you gave me printed this out ::::

> Because of the still encumbered components in the Class library, it is not yet possible to build OpenJDK only with free software components. In order to be able to do this before the whole class library is made free, and to be able to bundle OpenJDK in Fedora and other free Linux distributions, a project called IcedTea has been started by Red Hat. It is basically a OpenJDK/GNU Classpath hybrid that can be used to bootstrap OpenJDK using only Free Software

So, OpenJDK is not completely free yet.

---

