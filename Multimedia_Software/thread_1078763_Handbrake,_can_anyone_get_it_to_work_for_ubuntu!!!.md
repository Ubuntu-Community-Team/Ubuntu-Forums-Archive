---
title: "Handbrake, can anyone get it to work for ubuntu???!!!"
date: 2009-02-23
forum: Multimedia Software
---

### Post by philidox on 2009-02-23
Nothing frustrates me more to see a open source software work perfectly for windows and mac then I install it for my main os Ubuntu and it does not work.  That is exactly what has happend with handbrake.  Why can't it work right outta the box like the other OS's, just because we use linux doesn't mean everything has to be a struggle.  Anyway is there anyone who has figured how to get it working for Ubuntu?  I installed the debian file and when I click on it ABSOLUTELY nothing happens.  Please help!!!

---

### Post by binbash on 2009-02-23
It works perfect on this notebook BUT on the other notebook i have same issue with you.

---

### Post by howefield on 2009-02-23
> **philidox said:**
> Why can't it work right outta the box like the other OS's,...

Well actually, it works perfectly, for most everybody I know.

Give us a clue as to what the problem is, maybe someone can help you.

Where did you get the file you are are trying to install ?

---

### Post by philidox on 2009-02-23
> **howefield said:**
> Well actually, it works perfectly, for most everybody I know.

Give us a clue as to what the problem is, maybe someone can help you.

Where did you get the file you are are trying to install ?

I installed it from [www.handbrake.fr](www.handbrake.fr).  Did you guys get it from else where?

---

### Post by howefield on 2009-02-23
> **philidox said:**
> I installed it from [www.handbrake.fr](www.handbrake.fr).  Did you guys get it from else where?

No, handbrake.fr is fine, it was just when you mentioned "debian file" I wondered because there is no debian file on handbrake.fr

Have you tried installing from terminal using dpkg, it usually gives you an idea of what is going wrong if that is the case ? 

```
sudo dpkg -i filename.deb
```

---

### Post by philidox on 2009-02-23
Ok tried that but I'm still left with the same thing.  I hit alt+f2 and type in handbrake apparently the command to execute handbrake is "**ghb**".  When I type that into the cli it get this in return

**ghb: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory**.  Any idea what ubuntu need to start handbrake?

---

### Post by howefield on 2009-02-23
Check with synaptic that libxcb-render-util0 is installed ?

---

### Post by philidox on 2009-03-02
SOLVED BABY!

To make a long story short just download and install the dependency from the ubuntu package website at this url
[http://packages.ubuntu.com/intrepid/i386/libxcb-render-util0/download](http://packages.ubuntu.com/intrepid/i386/libxcb-render-util0/download)

Here is the forum with the answer
[http://www.backports.ubuntuforums.org/showthread.php?p=6284308](http://www.backports.ubuntuforums.org/showthread.php?p=6284308)

---

