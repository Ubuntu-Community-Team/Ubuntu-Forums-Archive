---
title: "Can't install/run a bin file in Ubuntu 16.04"
date: 2018-02-28
forum: Multimedia Software
---

### Post by dertuman on 2018-02-28
Hello! I'm trying to modify a bin file that is a firmware of hardware. I'm using a guide to manipulate this file with binwalk, but I can't seem to "install" the .bin file that I have. I've used the following commands, after being accesing the folder where the bin file is located.

chmod a+x file.bin
./file.bin 

Getting the following errors: 
./file.bin
./file.bin: line 1: $'verisignAAACAAAAAAAhAAAuAABP\001': command not found
./file.bin: line 2: syntax error near unexpected token `)'
./file.bin: line 2: `&#65533;0,J&#65533;:&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;Z&#45288;&#65533;u&#65533;&#65533;{@&#65533;&#65533;&#65533;)7&#65533;vi0&#1611;&#65533;&#65533;'

Any help? is it possible that the .bin file is "locked" rendering me unable to manipulate it? That would be odd. Also, I already have the following installed:
cpio, lzma, python 2.7, dd, xxd, and "file should already be installed"<<<----- This is the part that I'm missing. Thank you very much in advance.

Alex

---

### Post by TheFu on 2018-02-28
Extensions don't mean anything to Linux/Unix.  They are there for humans and very handy for us.  Some GUI applications use extensions too, when they really should be using the file header (file command) to get the "magic number" [https://en.wikipedia.org/wiki/Magic_number_(programming)](https://en.wikipedia.org/wiki/Magic_number_(programming)) to know the type of file it is.

Generally, a .bin file needs to be flashed onto the specific device using a specific tool for that device.  chmod +x dosn't help.  How a .bin file is packaged is completely unique to that device, though many just use cpio if they run minimal Linux systems.

Welcome to the forums.

---

### Post by dertuman on 2018-02-28
Thank you very much for the promt reply. How do you suggest for me to modify this file? It is a firmware file for a peplink device, and I want to change a few image files contained in it.

---

### Post by TheFu on 2018-02-28
I cannot suggest anything for that specific device. Sorry.  Best to look for a "peplink" forum and see what others are doing.
Found this [https://www.exploit-db.com/exploits/42130/](https://www.exploit-db.com/exploits/42130/) which might provide some insights.

Not sure I understand what this has to do with Ubuntu or Multimedia software. Care to elaborate?

---

### Post by dertuman on 2018-03-01
Ok, thanks a lot. It has to do with Ubuntu because I'm new to it and I was exploring the possibilities of handling .bin files in the system. I though maybe there was some insight on the software packages I mentioned above for the operating system. Thanks a lot and I will look into it.

---

### Post by monkeybrain20122 on 2018-03-05
Where do you get it from? Do you have a link to that guide you spoke off?

It is hard to give specific suggestions without knowing what it is and what you are supposed to do with it (e.g some .bin files are like iso images which you ate supposed to mount, others you run it like an executable ..)

---

### Post by Yellow Pasque on 2018-03-06
Yeah, it seems like a router firmware file that needs flashed to the router. Trying to execute it doesn't make sense. More info/context needed.

---

