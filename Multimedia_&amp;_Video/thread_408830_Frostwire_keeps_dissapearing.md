---
title: "Frostwire keeps dissapearing?"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by mikeaguilar1 on 2007-04-13
When i try to start up frostwire, Itll start up then juss dissapear. Whats the prob?

---

### Post by rsambuca on 2007-04-13
Try starting it from the terminal by entering```
frostwire
```

You will then be able to see the error messages and can post them here.

---

### Post by mikeaguilar1 on 2007-04-14
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharin

---

### Post by rsambuca on 2007-04-14
For some reason I had that exact same problem a while back. I just did a quick removal and reinstall of the java, and it worked fine after that.

Go to System -> Administration -> Synaptic Package Manager

Find the package called "sun-java5-jre"  and mark it for complete removal.  It will also remove  a package called sun-java5-bin.

Press apply to remove the java from your system.  Then you can just install it again through synaptic and hopefully frostwire will work after that.  At least it did for me.

---

### Post by mikeaguilar1 on 2007-04-14
> **rsambuca said:**
> For some reason I had that exact same problem a while back. I just did a quick removal and reinstall of the java, and it worked fine after that.

Go to System -> Administration -> Synaptic Package Manager

Find the package called "sun-java5-jre"  and mark it for complete removal.  It will also remove  a package called sun-java5-bin.

Press apply to remove the java from your system.  Then you can just install it again through synaptic and hopefully frostwire will work after that.  At least it did for me.

Problem solved, Thank you sooooo much.

---

