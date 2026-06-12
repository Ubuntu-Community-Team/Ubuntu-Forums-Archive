---
title: "Unable to Get Vuze BT Client to Run"
date: 2009-08-26
forum: Multimedia Software
---

### Post by CarlosinFL on 2009-08-26
I use apt-get to install 'vuze' the popular bittorrent client however when I try and run the application, nothing happens. I then open a terminal window and fun the command "vuze" and get the following error:

```
carlos@laptop:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found
carlos@laptop:~$ sudo apt-get install vuze
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vuze is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
carlos@laptop:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

```

I know I have Sun Java JDK and JRE all installed. I made sure myself...

Anyone know what the problem is and why this could be happening?

---

### Post by alastair mccracken on 2009-08-31
vuze looks for open java, so you need to go to your synaptic package manager and install open java. doesn't matter that you have sun java installed - just leave it alone as your default java installation. Vuze will find the files it needs in open java and away you go.

---

