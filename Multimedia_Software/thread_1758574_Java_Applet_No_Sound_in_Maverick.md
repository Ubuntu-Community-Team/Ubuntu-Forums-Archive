---
title: "Java Applet No Sound in Maverick"
date: 2011-05-14
forum: Multimedia Software
---

### Post by ggordon on 2011-05-14
I recently upgraded an ASUS netbook through a series of about 4 or so upgrades ending at Maverick (10.10).  Sound in Java applets worked fine before that, but I've been trying for about a week now to get it working again.

Here is what I have tried so far:

[LIST]
[*]Removed Sun Java and plugin, and installed Openjdk and icedtea
[*]Removed Openjdk and icedtea, and installed Sun Java and plugin
[*]Verified through about:plugins that FireFox plugin matched installed Java plugin
[*]Tried using padsp and aoss wrappers
[/LIST]

Along the way I have also tried other suggestions I have found through Google for configuring sound and setting file permissions, but nothing works.  No matter what I do, sound keeps working everywhere except in Java applets.

Here are some observations along the way.

Sound has worked everywhere I try except in Java applets.  It works with Flash.

Java applets work fine except for sound.  Java console indicates that sound files are being received and passed to applets.

My Java executable is located at /usr/lib/jvm/java-6-sun/jre/bin/java.  I have tried renaming it "java.real" and creating a shell script that wraps it with padsp or aoss.  When I do that Java works, but Java applets fail to start.  The Java console does not start up, so the wrappers appear to prevent applets from starting.

I am trying to run applets at [www.pogo.com](www.pogo.com).  They work fine for me on a 64-bit 10.04 system and a 32-bit 10.04 system.

Any ideas for something else to try?

---

### Post by ggordon on 2011-05-14
Here's some more information.

I just tested the same site with my other 32-bit system that had been working, but I had not actually tried it for awhile.  I just discovered that it is now longer able to get sound from those applets either.  However, sound is working on the 64-bit machine.

Here is some version information on the systems that are failing:

[INDENT]ASUS Netbook
Ubuntu 10.10
32-bit Sun Java 1.6.0.24[/INDENT]

[INDENT]Dell Inspiron laptop
Ubuntu 10.04
32-bit Sun Java 1.6.0.24[/INDENT]

Sound is working fine on this system:

[INDENT]Homebuilt tower with Intel motherboard
Ubuntu 10.04
64-bit Sun Java 1.6.0.24[/INDENT]

---

### Post by ggordon on 2011-05-15
Well, after working on this for another day I think I'm going to give up unless I get lucky and someone comes up with an answer.  I am now of the opinion that there is some sort of compatibility issue between Pogo and the latest Java plugin.  I'll just have to wait and hope that it gets resolved in a future version of one or the other.

What led me to this conclusion was that I discovered that on my 64-bit machine, even though I have Sun Java 1.6.0.24 installed, I had a link to an old Sun Java 1.6.0.12 plugin that was being used.  It's still working fine.  So I went to the Sun (Oracle) web site and downloaded and installed the 32 bit 1.6.0.12 JRE on one of the laptops.  But for some reason I just could not get it to load applets with that version even though FireFox showed that it was using that version.  So I've reverted to the current version and will just have to live with no sound in the games for now.

I'm going to post on the Pogo forum and see whether anyone there is having a similar problem.  If I'm not the only one with this problem, I might be able to get the people at Pogo to look into it.

---

