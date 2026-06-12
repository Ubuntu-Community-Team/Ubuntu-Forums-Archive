---
title: "Java/Frostwire"
date: 2008-12-31
forum: Multimedia Software
---

### Post by blackdog423 on 2008-12-31
Hey,

I tried to install Frostwire and it said that Java was not installed and I needed to update to Java 1.5+.

I figured I already had Java installed, but I tried anyhow.  

I tried via java.com, and I couldn't open the file.  Then I tried it through the terminal and java wouldn't come up under:  sudo apt-get install java.  It states it couldn't find package java.

I then went into Syntapic Package Manager and tried to install Java there.  It is saying that I have two broken packages and to fix it.  I don't know where the program is that the computer is telling me to fix it with.

How can I get frostwire working?  Is there another program that works as well as frostwire that doesn't use java for downloading music?

---

### Post by bumanie on 2008-12-31
Try > sudo dpkg --configure -ain terminal. That is the standard way to fix broken packages. The packages restart where they were interrupted.

---

### Post by jamesstansell on 2009-01-01
Also, in a terminal, what does this command return?

```
$ java -version
```

---

### Post by weirdfate on 2009-01-08
mine is acting all funky!!!!
cant min/max it at all cause it just stops going and i cant even close it with th X in the top corner....

this is hapening on ubuntu 8.10 all new updates
with java 6

---

### Post by jamesstansell on 2009-01-10
> **weirdfate said:**
> mine is acting all funky!!!!
cant min/max it at all cause it just stops going and i cant even close it with th X in the top corner....

this is hapening on ubuntu 8.10 all new updates
with java 6

The X in the top corner not closing a window sounds familiar; I think it might be fixed in later builds.

---

### Post by weirdfate on 2009-01-12
> **jamesstansell said:**
> The X in the top corner not closing a window sounds familiar; I think it might be fixed in later builds.

this never happened before i dont know why it is now???

its a fresh install and i might just have to go back to microsuck :(

---

### Post by white3911 on 2009-01-15
I installed Frostwire, rebooted and tried to open the application. When I click the icon, nothing appears. No splash screen or errors. Nothing. So I went into terminal and...


When I enter java -version, I get:

white@white-laptop:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)

However when I enter 'Frostwire' in the terminal, it returns:

Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)


If I am running Java 1.6.0_0, then it seems like it would be compatible considering Frostwire works with Java 1.4+.


You help is appreciated.

---

### Post by jamesstansell on 2009-01-17
> **white3911 said:**
> 
If I am running Java 1.6.0_0, then it seems like it would be compatible considering Frostwire works with Java 1.4+.

You help is appreciated.

Yes, it does seem like it should be compatible, doesn't it?  I personally don't understand why it wouldn't be.  I count it as a frostwire bug.

To get frostwire working for now, install the sun-java6-jre package, and have frostwire use that version.  The simplest way may be to just set it as the default system version:

```

$ sudo update-java-alternatives -s java-6-sun

```

---

