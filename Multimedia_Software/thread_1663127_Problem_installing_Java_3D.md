---
title: "Problem installing Java 3D"
date: 2011-01-09
forum: Multimedia Software
---

### Post by riddix on 2011-01-09
Hello everybody,

i'm trying to play around with java 3d, but having troubles to get some example to run.

NetBeans don't likes the line "import javax.vecmath.*;", it tells me that "package javax.vecmath does not exist",...

```
$java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.2) (6b20-1.9.2-0ubuntu2)
OpenJDK Server VM (build 19.0-b09, mixed mode)
```

```
/usr/lib/jvm/java-6-sun/jre/lib/ext$ ls
dnsns.jar                j3dutils.jar         sunpkcs11.jar
j3dcore-1.5.2+dfsg.jar   localedata.jar       **vecmath-1.5.2.jar**
j3dcore.jar              meta-index
j3dutils-1.5.2+dfsg.jar  sunjce_provider.jar
```

..., but here it is,...

etc/environment holds following:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

dunno whats wrong.

greets rid

---

### Post by lykeion on 2011-01-09
I think the vecmath jar-file needs to be in the classpath. I'm not very familiar with NetBeans but this page from a google search says you can add jars via Tools > Library Manager:
[http://www.jguru.com/faq/view.jsp?EID=1303662](http://www.jguru.com/faq/view.jsp?EID=1303662)

Hope it helps

---

