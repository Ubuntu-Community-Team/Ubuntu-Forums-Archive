---
title: "Java and mvpod"
date: 2008-08-08
forum: Multimedia Software
---

### Post by abelianjeff on 2008-08-08
Hi all,

I followed all of the instructions for installation on the mvpod website. However, when I go to run it, I get this message:

```
jeff@jeff-laptop:~/bin/bin$ ./mvpod
ERROR!
Java executable not found in /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
Please add java to your PATH environment variable, or specify it in file /home/jeff/bin/bin/mvpod.properties

```

Any thoughts on how to fix this?

Thanks!

---

### Post by yeehawjared on 2008-08-18
```
JAVA_HOME=/usr

```

from [http://iphone.teamroot.net/faq/content/6/9/en/how-do-i-encode-iphone-videos-on-linux-.html](http://iphone.teamroot.net/faq/content/6/9/en/how-do-i-encode-iphone-videos-on-linux-.html)

---

### Post by yeehawjared on 2008-09-01
by the way, you don't even need to change anything with the more recent builds.  Use the latest nightly build - nothing to comiple, just extract and execute.

by far the best way to encode video.  great for ipod, psp, iphone, etc.

They even ported it to windows, great, great app.

[http://mvpod.sourceforge.net/nightly/latest/](http://mvpod.sourceforge.net/nightly/latest/)

---

### Post by bikodog on 2008-11-17
Please help an Ubuntu newb install mvpod.

As far as I can tell I have gpac, mencoder, and JRE 1.6+ installed. I can run mvpod from the /bin. When I try to add a video file I get the following

One of MPlayer's components is missing: %s

Any help would be appreciated.

---

