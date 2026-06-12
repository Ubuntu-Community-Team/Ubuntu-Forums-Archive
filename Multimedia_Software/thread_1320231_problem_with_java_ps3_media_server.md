---
title: "problem with java ps3 media server"
date: 2009-11-09
forum: Multimedia Software
---

### Post by Arminius on 2009-11-09
hey, I've been using mediatomb, and it was working fine. until there was a .mp4 that my ps3 couldn't even see.

so I thought I would try java ps3 media server out.

and it can see the .mp4 but it says it's corrupted, meanwhile the same video file plays just fine on my PC.

in fact most videos won't play on ps3 through java ps3.

I'm hoping my settings are just a bit off.

any suggestions?

---

### Post by thebrandon on 2009-11-17
I have the same problem.  The way to get it to transcode is to move all of the pms files to /tmp/javaps3media including most importantly the /linux directory with the tsmuxer file.  All of the transcoding for mp4 and mkv files works as well as accessing the web functions although none of them work.  The problem is that whenever you reboot that tmp directory gets wiped and you have to move everything again!  Oh, also I belive you have to chown +x PMS.sh and launch it in the terminal ./PMS.sh  I gave up on this method since everything I watch doesnt require it.  I have posted here and on the PMS forum but I cant get any help.  Let me know if you figure a better solution out!

---

### Post by xc3RnbFO8P on 2009-11-17
Read this:
[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4253]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4253")

---

### Post by thebrandon on 2009-11-18
Thanks, that worked perfectly!  I dont suppose you know of any websites that the streaming function works with do you?

---

### Post by Arminius on 2009-11-19
did not work for me
says "Perhaps JAVA_HOME does not point to the JDK."

but I've been very careful over and over

---

### Post by thebrandon on 2009-11-20
Ok so what exactly isnt working, PMS  or the streaming of the mp4?

---

### Post by Arminius on 2009-11-20
cd ps3mediaserver-read-only/ps3mediaserver
ant

after I hit ant it fails, it comes up with

BUILD FAILED
/home/User/ps3mediaserver-read-only/ps3mediaserver/build.xml:31: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK.
It is currently set to "/usr/lib/jvm/java-6-sun-1.6.0.16/jre"

---

### Post by thebrandon on 2009-11-20
Well if you just did this recently you need to change it to :

JAVA_HOME=/home/YOURUSERNAME/downloads/jdk1.6.0_17/jre

The tutorial was for an earlier release of jdk

---

### Post by Arminius on 2009-11-20
just says Error: JAVA_HOME is not defined correctly.
  We cannot execute /home/user/downloads/jdk1.6.0_17/jre/bin/java

---

### Post by Notorious1 on 2009-11-20
Very useful link.

---

### Post by thebrandon on 2009-11-20
After you typed :

JAVA_HOME=/home/YOURUSERNAME/downloads/jdk1.6.0_17/jre

try :

export JAVA_HOME

see if that helps

---

### Post by Arminius on 2009-11-23
followed those instructions.

and still came up with Error: JAVA_HOME is not defined correctly.
  We cannot execute /home/user/downloads/jdk1.6.0_17/jre/bin/java

---

### Post by thebrandon on 2009-11-23
hmmm I really dont know at this point.  Im sorry I cant be of more help!

---

### Post by silentknyght on 2009-11-23
> **Arminius said:**
> hey, I've been using mediatomb, and it was working fine. until there was a .mp4 that my ps3 couldn't even see.

so I thought I would try java ps3 media server out.

and it can see the .mp4 but it says it's corrupted, meanwhile the same video file plays just fine on my PC.

in fact most videos won't play on ps3 through java ps3.

I'm hoping my settings are just a bit off.

any suggestions?

Wouldn't the best suggestion be to reformat the .mp4 into a file that the PS3 can see, or to edit the ~/.mediatomb/config.xml file to include .mp4 capability?  Based on your description, that appears to be the primary problem.

I've found this guide to be particularly resourceful.  Try using snippits from his code in your config file. I can't guarantee that this will be the perfect solution for you, but perhaps it can point you in the right direction.

[http://juliensimon.blogspot.com/2008/12/mediatomb-012-on-ps3-video-thumbnails.html]("http://juliensimon.blogspot.com/2008/12/mediatomb-012-on-ps3-video-thumbnails.html")

---

### Post by thebrandon on 2009-11-23
So with mediatomb you can stream youtube and apple trailers?  Is there a way to stream hulu?  I tried it but I couldnt figure out how to use it so I gave up.

---

