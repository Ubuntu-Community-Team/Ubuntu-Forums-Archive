---
title: "Must be run as root.  What?"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by saxofoner on 2006-08-18
I downloaded NVIDIA-Linux-x86-1.0-8762-pkg1.run and tried the "sh" command as the site (nvidia site) instructed me to.  But it said "must be run as root".  I looked up "running as root" and that sounds like something I'm too newbish to do.  Are there alternatives?

---

### Post by christhemonkey on 2006-08-18
Root account is disabled on ubuntu by default.
But you can temporarily obtain root privileges using "sudo":
```
sudo sh ./BLA.sh 
```
Obviously replacing BLA.sh with the real name and path.

---

### Post by saxofoner on 2006-08-18
Eeek... Is there an alternative way to have drivers?

---

### Post by christhemonkey on 2006-08-18
```
sudo apt-get install nvidia-glx
```

Or go into synaptic and search for it.
That worked fine for me, although, there is probably better other ways scattered all over this forum and the wiki.

Particulalry see:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://ubuntuguide.org/wiki/Dapper#installnvidiadriver](http://ubuntuguide.org/wiki/Dapper#installnvidiadriver)

---

### Post by saxofoner on 2006-08-18
Heh.  That worked.  Thanks.

---

