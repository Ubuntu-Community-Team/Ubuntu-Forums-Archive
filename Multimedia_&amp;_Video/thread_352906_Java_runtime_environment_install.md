---
title: "Java runtime environment install"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by RDUBBALO on 2007-02-03
Yeah I need to install the java runtime environment I DL it and i dsont know what to do I read the help file for linux but when i put in the code in the terminal it doesnt work. Say to type su the put in adminpassword. i put in my password and it says login failed i dont know what to do here. Thanks for the help

---

### Post by taurus on 2007-02-03
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by RDUBBALO on 2007-02-03
> **taurus said:**
> [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Wow thanks alot you really are a huge help. that was it perfect.

---

### Post by RDUBBALO on 2007-02-03
ok now how do i get it to work. I am trying to play the games in yahoo and I have the jave 5.0 runtime now what do i do. i I also did the other one you suggested but i dont know what that did. it still says i nee dit

---

### Post by taurus on 2007-02-03
You need to copy the java plugin from wherever you installed java to /usr/lib/firefox/plugins.  What's the output of this command from a terminal?

```
locate java
```

---

### Post by phossal on 2007-02-04
I like this one too:
```
ls -l $(type -path -all java)
```

---

### Post by RDUBBALO on 2007-02-05
/etc/alternatives/java

---

### Post by RDUBBALO on 2007-02-05
well it says this~  lrwxrwxrwx 1 root root 22 2007-01-26 17:05 /usr/bin/java -> /etc/alternatives/java

---

### Post by phossal on 2007-02-05
```
ls -l /etc/alternatives/java
```
That should tell you where the base folder of the java you're using is. Once you know that, you should be able to go to that folder, find the /jre/plugin folder, and then you'll make a link in the /usr/lib/firefox/plugins directory to the plugin.

---

### Post by bpro on 2007-02-07
> **taurus said:**
> [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

This document says that amd64 users need to use Blackdown 1.4.2 as their Firefox plugin, but when I select that in Add/Remove Applications I get a popup that that can't be installed on amd64's?!?  Am I misunderstanding something, or is there really no option other than to install a 32-bit version of Firefox?

---

### Post by RDUBBALO on 2007-02-08
yeah I just found all the ones in add/remove programs i needed the firefox plugin. Thanks all for help.

---

