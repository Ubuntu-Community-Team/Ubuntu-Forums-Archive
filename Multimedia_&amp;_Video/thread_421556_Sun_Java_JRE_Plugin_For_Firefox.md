---
title: "Sun Java JRE Plugin For Firefox"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2007-04-24
Guys - I need to do some training that requires Sun Java JRE enabled however I installed this via APT.

```
 sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-bin
```

It installed fine however I don't know how to enable the Firefox plugin for my browser.

Any advice?

Here is what my system currently shows for Java

```
cwilliams@cwilliams:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)

```

[IMG]http://img235.imageshack.us/img235/6496/screenshotpluginfinderszx6.png[/IMG]

---

### Post by finite9 on 2007-04-24
there is no firefox plugin with x86_64 builds of Java.  This applies to Java 1.5 and 1.6.  Very weird and makes you start thinking conspiracy theory.  Only Blackdown Java has a firefox plugin with the x86_64 build but this is Java 1.4.2.

My opinion is; if Sun can supply a firefox plugin with 32bit Java 1.5 and 1.6 then why can't they supply it with x86_64!?

---

