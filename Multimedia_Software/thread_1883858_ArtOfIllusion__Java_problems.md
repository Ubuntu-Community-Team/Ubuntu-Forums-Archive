---
title: "ArtOfIllusion  Java problems"
date: 2011-11-20
forum: Multimedia Software
---

### Post by beew on 2011-11-20
Hi,

After installing ArtOfIllusion  I tried to run it with the script aoi.sh and get this error
> Error occurred during initialization of VM
Could not reserve enough space for object heap
Could not create the Java virtual machine.Since I have about 3G of ram  I don't believe I don'have enough ram to start JVM.

Now it seems that the script only initiates executing a .jar file called ArtOfIllusion.jar. I execute that directly from the terminal and the program loaded but I got a java.library.path error saying that it could not find gluegen.so. I did the following
```
sudo cp /usr/share/java/jogl.jar /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/ext/
sudo cp /usr/lib/jni/libgluegen-rt.so /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/ext/
sudo cp /usr/lib/jni/libjogl*.so /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/ext/
```Now when I start AOI I get this error

> Error creating GLCanvasDrawer: java.lang.NoClassDefFoundError: com/sun/gluegenPlease help me to fix it

I am also puzzled why the startup shell script gave the not enough space to create jvm error whereas the .jar file ran just fine save the error above.

Thanks in advance for any help.

P.S. I have configured to use sun-java as default. But somehow I have two java-6-sun folders in /usr/lib/jvm, one is called java-6-sun, the other java-6-sun-1.6.0.26

---

### Post by beew on 2011-11-20
Install in Natty again and the error message is

> Error creating GLCanvasDrawer: java.lang.UnsatisfiedLinkError: no gluegen-rt in java.library.path


---

### Post by beew on 2011-11-21
It seems that the problem can be resolved by linking the gluegen-rt library(ies?) to the correct java.library.path. But how do I find out what the java.library.path is? Sorry, I don't know anything about java.

---

### Post by beew on 2011-11-23
Is there anyone able to help??

---

### Post by beew on 2011-11-25
Bump!

---

