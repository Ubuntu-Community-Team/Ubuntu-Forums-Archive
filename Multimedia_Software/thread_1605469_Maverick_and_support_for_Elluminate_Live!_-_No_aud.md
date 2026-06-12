---
title: "Maverick and support for Elluminate Live! - No audio"
date: 2010-10-25
forum: Multimedia Software
---

### Post by karel_novotny on 2010-10-25
Hello,

I have been successfully using Elluminate Live online meeting space (Java-based) on previous releases of Ubuntu.

By upgrading to Maverick 10.10., all audio features of that application became dysfunctional. Obviously, the Java application that is used to connect to Elluminate Live doesn't recognize audio devices (audio setup wizard of the same application doesn't list any devices).

Anyone has had the same problem? Any solution? 

Contacting Elluminate's support didn't help because accoring to them Ubuntu 10.10 is not a supported distro for Elluminate.

thanks

karel

---

### Post by JeffRheault on 2011-04-10
Hi,

I had a similar problem. I tried to run elluminate live on ubuntu and it was not showing at all.

First, i had to install java from oracle website.

After, you need the pulse audio plugin that is provided by openjdk and copy it in your new jre folder

[SIZE=2]
sudo cp /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libpulse-java.so
/usr/lib/jvm/java-6-sun/jre/lib/i386/

sudo cp /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
/usr/lib/jvm/java-6-sun/jre/lib/ext/

Hope it helps.
[/SIZE]

---

