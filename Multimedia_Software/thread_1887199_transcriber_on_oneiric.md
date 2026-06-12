---
title: "transcriber on oneiric"
date: 2011-11-26
forum: Multimedia Software
---

### Post by Sixtease on 2011-11-26
Hello all,

I'm trying to get transcriber running on my 64bit oneiric. I tried to compile from source, and after a little resistance, I succeeded. However, now when I run it, it says it can't find tcLex. And, indeed, when I type "package require tcLex" in tclsh, I get "can't find package tcLex". I have the tclex package installed though (I mean the Ubuntu package). Any idea where the problem could lie?

Of course I'd love to just apt-get install transcriber, but it looks like it's not yet published for oneiric ocelot (no idea how long it could take).
The binary Linux version doesn't work either, I presume it's because of 64bitness of my Linux.

Thanks for any insight.

**Update:** As discussed on [comp.lang.tcl]("http://groups.google.com/group/comp.lang.tcl/browse_thread/thread/01acfe214f4b50fa#"), the problem was with tcLex requiring TCL version less than 8.5. Downgrading TCL to 8.4 solved the problem.

---

### Post by narcisgarcia on 2012-06-30
I've built a .deb package for TranscriberAG 2.0.0-b1 following and adapting instructions in [TranscriberAG installation guide]("http://transag.sourceforge.net/index.php?content=install") and some [Bastien Busson indications for good compiling]("http://sourceforge.net/mailarchive/forum.php?thread_name=4E35D2B5.4020104%40vista.se&forum_name=transag-general")

Here the downloadable file:
[http://repos.actiu.net/sound-video/](http://repos.actiu.net/sound-video/)

I had't used anytime this application, but freezes at any action (Ubuntu 11.04 i386).

---

### Post by SanglierDesBois on 2013-01-28
Hi Narcis,

Many thanks for your work !
I was not able to install it under amd64, would you be able to tell me what you've done to compile successully under ubuntu ? So I could make it for amd64

---

### Post by narcisgarcia on 2013-01-28
I'm sorry because I didn't write the exact steps followed to build the package.

You can try to install my published package with a command like this:
```
dpkg --force-architecture --install transcriberag_2.0.0-b2_i386.deb
```

(I thought that TranscriberAG was an speech recognition software, but it's only a helper to user writes manually while listening an audio).
I also remember that it gave some problem to run.

---

