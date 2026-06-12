---
title: "Help me install Cinelerra"
date: 2011-10-19
forum: Multimedia Software
---

### Post by marer13 on 2011-10-19
It doesn't work on my Kubuntu.....

Here's the output I'm getting:

     Quote:
                                                 marer13@marer13-Studio:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cinelerra                                 
What shall I do?

---

### Post by wolfen69 on 2011-10-19
I'm not sure where software sources are in Kubuntu, (the gui) but you probably need to enable the proper repos. Post the output of:
```
sudo kate /etc/apt/sources.list
```

---

### Post by marer13 on 2011-10-19
marer13@marer13-Studio:~$ sudo kate /etc/apt/sources.list
[sudo] password for marer13: 
Error: "/var/tmp/kdecache-marer13" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-marer13" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-marer13" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-marer13" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-marer13" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-marer13" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-marer13" is owned by uid 1000 instead of uid 0.
kbuildsycoca4(14972) KConfigGroup::readXdgListEntry: List entry text/html in "/home/marer13/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 
Error: "/var/tmp/kdecache-marer13" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-marer13" is owned by uid 1000 instead of uid 0.

---

