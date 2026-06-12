---
title: "iPod nano 8GB (need help)"
date: 2008-12-31
forum: Multimedia Software
---

### Post by bottosai88 on 2008-12-31
OK i just purchased the new iPod nano 8GB yesterday and was wondering what programs would be suggested. I downloaded frostwire and it works, WINE to run the itunes but am having problems with that so i was wondering whether I should use Banshee or Amarok. I have them both but before loading em with music whitch should i use? IS there a place i can get vids for the ipod also and all those so i mean any info that i could use that you guys would mind giving me. Any help would be much appreciated.

---

### Post by AlanR8 on 2008-12-31
I've had success with Amorak with both the older Nano and my Son's iPod Touch. I'm using Kubuntu but I believe Amorak, a KDE program, will run in Gnome.

---

### Post by bottosai88 on 2008-12-31
Those programs run but i now cannot get FrostWire to open up. I tried to reinstall the package but it wont work. Banshee and Amarok work and i am not running in gnome, i am running in the default way. I just tried gnome and i still cannot get frostwire up and running. Any ideas? or alternate programs?

---

### Post by Rickyk on 2008-12-31
you can dl frost wire for linux you dont need wine for it

---

### Post by jacob01 on 2008-12-31
i think you need java rte or some sort of java to run it.

go into your terminal after frostwire is installed and run it from there by typing 'frostwire' and it should tell you what it needs then you should be able to get the java you need from the repository.

---

### Post by bottosai88 on 2009-01-01
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

This is what i got and i have no idea which file to download and it downloads as .bin

---

### Post by cozmicharlie on 2009-01-01
You need to install the Sun Java6 JRE.  It is available in Synaptic.  Make sure you install the Sun Java6 JRE (also install the Sun Java6 JRE fonts).  I would recommend you install the entire "Ubuntu Restricted Extras" package".  It will include Sun Java6 JRE and other codecs you will need for music and video.  Add the medibuntu repository first ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) then in synatic search for "ubuntu restricted extras" and install.  You will have to accept the license for Java.

---

