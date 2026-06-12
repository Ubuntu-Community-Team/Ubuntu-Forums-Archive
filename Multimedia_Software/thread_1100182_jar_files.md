---
title: "jar files"
date: 2009-03-18
forum: Multimedia Software
---

### Post by msohn88 on 2009-03-18
I tried to install emulator on my samsung eternity so I followed the step

[http://arktos.se/meboy/download.php](http://arktos.se/meboy/download.php)

but I was not able to run .jar file!

ubuntu just opens it!

Help!

---

### Post by blackened on 2009-03-18
I'm assuming you don't have Ubuntu installed on your cell, and are trying to run this emulator on your computer.

Make sure you have the java runtimes installed
```
sudo apt-get install sun-java6-bin
```

then open the file with 
```
java -jar */path/to/file*
```

---

### Post by msohn88 on 2009-03-18
> **blackened said:**
> I'm assuming you don't have Ubuntu installed on your cell, and are trying to run this emulator on your computer.

Make sure you have the java runtimes installed
```
sudo apt-get install sun-java6-bin
```

then open the file with 
```
java -jar */path/to/file*
```

I don't get your second command what do I type in "path/to/file" part?

---

### Post by blackened on 2009-03-19
> **msohn88 said:**
> I don't get your second command what do I type in "path/to/file" part?

I mean enter the path to the file that you're trying to run. Say you downloaded the MeBoyBuilder.jar to your desktop, then you would run the file with
```
java -jar ~/Desktop/MeBoyBuilder.jar
```

---

