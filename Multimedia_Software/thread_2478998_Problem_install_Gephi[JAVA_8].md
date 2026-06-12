---
title: "Problem install Gephi[JAVA 8]"
date: 2022-09-11
forum: Multimedia Software
---

### Post by dionatandiego11 on 2022-09-11
Hello friends.


I'm trying to install Gephi, but when running it returns the following error:

./gephi
Unrecognized option: --add-opens=java.base/java.net=ALL-UNNAMED
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.

when I run java -version
openjdk version "1.8.0_342"
OpenJDK Runtime Environment (build 1.8.0_342-8u342-b07-0ubuntu1~22.04-b07)
OpenJDK 64-Bit Server VM (build 25.342-b07, mixed mode)

But when I do java --version
Unrecognized option: --version
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.

---

### Post by Holger_Gehrke on 2022-09-11
What version of Gephi are you trying to use ? The current version at gephi.org (0.9.7) needs Java 11 and comes in a tarball that includes a jdk from the Eclipse Temurin project in version 11. You can configure it to use you own jre (either by using the switch '--jdkhome' with the directory in which a jre or jdk is installed or by setting jdkhome in gephi-0.9.7/etc/gephi.conf).

Holger

Edit: Besides the tarball from gephi org, there's also a snap; judging by the size of it, this should also come with a JDK ...

---

### Post by dionatandiego11 on 2022-09-12
First thanks for responding.


Installation by SNAP does not work gives error. So I normally downloaded version 0.9.7 from the site that comes with JAVA 11 installed, but when I run it gives a compatibility error in opengl. So I started trying to use JAVA 8 that this problem. I tried to put it inside the application and run it by changing the directory and the same error remains.


Now you've given me an idea, download an old version of Gephi.

---

