---
title: "Xlink Kai on 11.04"
date: 2011-05-18
forum: Multimedia Software
---

### Post by Pen16 on 2011-05-18
Tryin to install Xlink via terminal and this is what im getting.

basti@basti-RJ181AA-ABA-a1600n:~$ cd '/home/basti/Desktop/kaiEngine-7.4.18' 
~/Desktop/kaiEngine-7.4.18$ ./kaiengine
./kaiengine: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: wrong ELF class: ELFCLASS64

Is there another synaptic package needed or am i doin somethin wrong?

---

### Post by Pen16 on 2011-05-19
Has anyone gotten it to work on 11.04 yet?  Ive seen threads on how to install it but it pops up that error so im assuming its to do with the install.

It doesn't have to do with it being an x86 release and im runnin x64 does it?

---

### Post by Pen16 on 2011-05-22
Hey....


Hey, guess what!?....


MothaF*#$in bump!  ):P

---

### Post by mnlangston on 2011-06-01
This happens because it was compiled only for x86, you need to install 32-bit versions of the libraries it requires in order to use it on a 64-bit system.  I used getlibs for this [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

You can use ldd on the binary (kaiengine) to figure out what you need to install, use -l on getlibs if you don't know the name of a package that contains a specific .so file. Eventually all the dependencies will be solved and the program will start, have fun!

---

### Post by bilbometal on 2011-09-11
> **mnlangston said:**
> This happens because it was compiled only for x86, you need to install 32-bit versions of the libraries it requires in order to use it on a 64-bit system.  I used getlibs for this [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

You can use ldd on the binary (kaiengine) to figure out what you need to install, use -l on getlibs if you don't know the name of a package that contains a specific .so file. Eventually all the dependencies will be solved and the program will start, have fun!

It's worked!

That&#347; what I did:
1. Download and install GetLib software: [ click here]("http://frozenfox.freehostia.com/cappy/")
2. Execute on a terminal: ```
getlibs -l libwx_gtk2u_richtext-2.8.so.0
```
3. answer 'Yes' to the question
4. Try to execute Kai: ```
sudo ./kaiengine
```
5. if it asks for some other library, repeat the steps 2 (with the respectively library name), 3 and 4 until you can execute kai

Hope that helps.

---

