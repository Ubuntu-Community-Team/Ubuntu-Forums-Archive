---
title: "Iriverter on Feisty"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by ggaaron on 2007-04-21
Hi,
how do I run iriverter under ubuntu feisty? I've installed it using apt-get, and it is what i get when trying to run it:

!!! An unhandled exception occured: class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
---
--- Settings:
---
---
!!! no swt-pi-gtk-3236 in java.library.path
!!!
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1517)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:788)
!!! java.lang.System.loadLibrary(System.java:834)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
!!! org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:28)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!!
Exception in thread "main" java.lang.NoClassDefFoundError
        at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:675)

Thanks in advance.

Aaron

---

### Post by dgoodwin on 2007-04-22
I have the exact same message on a new install of Fiesty. Did you find a fix?

---

### Post by ggaaron on 2007-04-23
Unfortunately not... But I assume it's some java, not iriverter error. And I couldn't get java to work on Edgy either, so I don't know what to do=(

Aaron

---

### Post by aderby on 2007-04-23
I've got this issue too. I see somebody has reported this issue but it's only just started to be looked into.

[https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/91237](https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/91237)

I've just order a Cowan D2, so I really hope this gets sorted soon

---

### Post by ggaaron on 2007-04-24
Someone there stated that iriverter works on feisty, strange=/ I'll boot from liveCD and see whether it works...

---

### Post by ggaaron on 2007-04-24
I don't know why, but Iriverter works on liveCD, after updating all available packages it works too, so why doesn't it work on my installed ubuntu?

---

### Post by aderby on 2007-04-24
Yes, that's the question. The machine I was trying it on is a recent upgrade from Edgy. I have a desktop that has only ever run Fiesty - since early rc's. When I get home I'll try iriverter on it. If it works I'll try to see if I can spot any differences that might explain the problem.

---

### Post by aderby on 2007-04-24
OK, making progress. As suspected it's a java environment thing. If you do the following in a terminal before launching iriverter 

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jni

it launches correctly. Now if somebody knows the 'correct' way to do this automatically, we'd be sorted.

Andrew.

---

### Post by ggaaron on 2007-04-25
Wow, great job - it works. But still it is some bug that should be fixed.

Aaron.

---

### Post by aderby on 2007-04-25
I didn't get a chance to test it beyond launching and I see on the bug thread that it still may not be working fully. I've burnt a live CD to see what I get if I do a "echo $LD_LIBRARY_PATH". I'm out this evening so I may not be able to do this for a while. If you get a chance before I do, let me know the result. If you get a response and there are additional paths, try adding them to the export command.
Andrew.

---

### Post by aderby on 2007-04-25
Seems I spoke a bit soon. I've just successfully converted a movie. So I guess it works for me now.

---

### Post by ggaaron on 2007-04-26
I've tried running iriverter, not only starting and it works, at least for me...

---

### Post by rts on 2007-05-01
Wow, Java seems a little messed up on Feisty (or rather, Java is messed up, period).

I have the following options for java:

```

$ sudo update-alternatives --config java


There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/j2sdk1.5-sun/bin/java
          2    /usr/lib/j2re1.5-sun/bin/java
          3    /usr/bin/gij-wrapper-4.0
          4    /usr/bin/gij-wrapper-4.1
 +        5    /usr/lib/jvm/java-gcj/jre/bin/java
*         6    /usr/lib/jvm/java-6-sun/jre/bin/java

```


If I set it to 6, I get the errors you report.

If I set it to 5, this application works but then other applications break.

So much for write once run everywhere.  :(

---

### Post by moopoo on 2007-05-02
Hi,

someone found a solution: ["_iriverter on ubuntu breezy_"]("http://pawnee.wordpress.com/2006/02/25/iriverter-on-ubuntu-breezy/"). I think that this also applies to feisty.

> 
Then I got the following error:
Exception in thread &#8220;main&#8221; java.lang.UnsatisfiedLinkError: no swt-pi -gtk-3139 in java.library.path

The problem was that iriverter doesn&#8217;t found the swt-pi-gtk3139.so library.
To fix this, open /usr/local/bin/iriverter with a text-editor like vi

    vi /usr/local/bin/iriverter

and change the java.library.path from

    $LD_LIBRARY_PATH:${exec_prefix}/lib

to

    /usr/lib/jni

Now, iriverter should run. If not, post a comment.


The thing is, that I don't have  "/usr/local/bin/iriverter". So, if someone here could tell me, where I should apply the described changes on the feisty-deb-version, I would be very grateful.

---

### Post by aderby on 2007-05-02
It's /usr/bin/iriverter on my PC. I appended it to the path statement (to be on the safe side). So I end up with this -

java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib:/usr/lib/jni 

and it now works without setting the environmental variable manually.

---

### Post by moopoo on 2007-05-04
Great. It works! Thanks.

---

### Post by pkjunction on 2008-01-16
I tried all of the suggestions and what found worked was adding the line; export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jni
before the line; java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar org.thestaticvoid.iriverter.ConverterUI $*
in /usr/bin/iriverter.

It worked for me, anyone else try this?

I'm running 7.10 on AMD64.

---

### Post by firefeather on 2008-03-07
> **aderby said:**
> It's /usr/bin/iriverter on my PC. I appended it to the path statement (to be on the safe side). So I end up with this -

java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib:/usr/lib/jni 

and it now works without setting the environmental variable manually.

This worked for me on 7.10 amd64.

---

### Post by ghostofcain on 2008-07-19
> **firefeather said:**
> This worked for me on 7.10 amd64. Yep works for me, too! just a shame this isn't working out the box

---

