---
title: "Enabling Sun Java in Firefox"
date: 2008-09-12
forum: Multimedia Software
---

### Post by sat_e_llite on 2008-09-12
Hi, I just joined and used Ubuntu for a few weeks now. I LOVE it!

But, how do I enable Sun Java in Firefox?

And is this in the right forum?

---

### Post by ju2wheels on 2008-09-12
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Also make sure that /etc/jvm lists java-6-sun as the first line.

Mines looks like this:

> more /etc/jvm
# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

---

### Post by sat_e_llite on 2008-09-12
But it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by ju2wheels on 2008-09-12
Make sure you have the correct repositories enabled... im not sure which ones they are in.

On your menu go to System-> Administration -> Software Sources .

Enable universe and multiverse repositories on the Ubuntu Software tab and then try again.

---

### Post by gandaran on 2008-09-13
> **sat_e_llite said:**
> But it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

are you running ubuntu 64-bits?
there is no sun-java6-plugin for 64-bits systems, this means you have to use open java and the icedtea plugin, look for the icedtea java plugin in synaptic package manager, mark for install and click the apply button, the rest of java dependencies will be installed too, and you can remove the sun java.

---

### Post by sat_e_llite on 2008-09-13
Yep, I have a 64-bit system.

And by the way, icedtea works fine. Now I can load java applets.

---

