---
title: "Java Iriverter crash"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Sonja on 2008-05-20
I get this error:

```
sonja@sonja:~$ iriverter
!!! An unhandled exception occured: class java.lang.StringIndexOutOfBoundsException
--- iriverter 0.16
--- 
--- Settings:
--- videoBitrate=
--- audioBitrate=
--- currentProfile=d2
--- frameRate=
--- dimensions=
--- autoSplit=
--- splitTime=
--- autoSync=true
--- audioDelay=0
--- 
!!! String index out of range: -1
!!! 
!!! java.lang.String.substring(String.java:1949)
!!! org.thestaticvoid.iriverter.Dimensions.<init>(Dimensions.java:12)
!!! org.thestaticvoid.iriverter.Profile.getDimensions(Profile.java:72)
!!! org.thestaticvoid.iriverter.ConverterUI.profileChanged(ConverterUI.java:502)
!!! org.thestaticvoid.iriverter.ConverterUI.setupMenus(ConverterUI.java:275)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:41)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!! 

```

---

### Post by Sonja on 2008-05-20
[https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/91237](https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/91237)

Typing "export LD_LIBRARY_PATH=/usr/lib/jni/" does not fix the bug for me.

---

### Post by MaindotC on 2008-05-20
Did you install it via apt-get and if so did all those dependencies install as well?  Seems like there's a variable with the incorrect data type.  If apt-get has no answers you may want to try downloading the source and installing manually - especially if it's a matter of a variable.

---

### Post by Sonja on 2008-05-20
I tried reinstalling Iriverter in Synaptic, and it does not fix the bug. Maybe I have to reinstall Java somehow?

---

### Post by MaindotC on 2008-05-20
You could do that - could be some development files that are necessary.  I compile java programs on my machine using the javacc package (java compiler).  Another suggestion that I think has nothing to do with this but I'll just throw this out there - ubuntu-restricted-extras package?  It includes the java runtime environment.

---

### Post by roy.b on 2008-09-30
Is there a solution for this.

I also am getting a StringIndexOutOfBoundsException when trying to run iriverter.

It originally worked when installed and i have converted DVDs for my zen many times. Just recently it started giving this error.

I have tried all suggestions from above, but alas no success

~$ iriverter
!!! An unhandled exception occured: class java.lang.StringIndexOutOfBoundsException
--- iriverter 0.16
---
--- Settings:
--- currentProfile=zvwC
--- videoBitrate=
--- audioBitrate=
--- frameRate=
--- dimensions=
--- autoSplit=
--- splitTime=
--- panAndScan=true
--- volumeFilter=volnorm
---
!!! null
!!!
!!! java.lang.String.substring(libgcj.so.81)
!!! org.thestaticvoid.iriverter.Dimensions.<init>(Dimensions.java:12)
!!! org.thestaticvoid.iriverter.Profile.getDimensions(Profile.java:72)
!!! org.thestaticvoid.iriverter.ConverterUI.profileChanged(ConverterUI.java:502)
!!! org.thestaticvoid.iriverter.ConverterUI.setupMenus(ConverterUI.java:275)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:41)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!!

---

### Post by roy.b on 2008-10-02
OK, i have got a solution.

The problem appears to be the way dimensions are parsed in the profile.

The profile it is looking for does not exist and iriverter tries to parse an empty dimension string.

I changed my ~/.iriverter.conf to point to an existing profile and it starts up and works.

I hope this helps someone else, also it would be good if the Dimension class was fixed to handle an empty dimension property.

---

### Post by Gammell on 2008-11-14
> **roy.b said:**
> OK, i have got a solution.

The problem appears to be the way dimensions are parsed in the profile.

The profile it is looking for does not exist and iriverter tries to parse an empty dimension string.

I changed my ~/.iriverter.conf to point to an existing profile and it starts up and works.

I hope this helps someone else, also it would be good if the Dimension class was fixed to handle an empty dimension property.

Could you post a sample .conf file? I just installed iriverter and would like to see if I can get it to run if it has a .conf file (it does not create one on install)

---

### Post by aquarianwolf on 2008-11-14
I've got a problem with Java at the moment.

I'm trying to get into one of my java based chatrooms but when I click on the link it just says loading and does nothing.

I've checked in prefernces in firefox to see if it's all enabled and fair enough it is but I still have this problem.

Anybody know what to do?

---

