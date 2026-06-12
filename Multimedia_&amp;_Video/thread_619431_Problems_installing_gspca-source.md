---
title: "Problems installing gspca-source"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by Marianne_S on 2007-11-21
i have problems installing the gspca-source on my computer. i am new to ubuntu and are trying to learn terminal command lines. 

anyways i tried unpacking it with xfvj - but got this error message:

desktop:~$ tar xfvj gspca-source.tar.bz2
tar: gspca-source.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors 

i found this

[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg145983.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg145983.html)

but it isnt spesific for ubuntu - nor do i know how to change the name of the package.

can anyone help?

(oh and i use 7.10)

---

### Post by jespdj on 2007-11-21
The error means that the file gspca-source.tar.bz2 does not exist in the directory where you are executing the command. Find out where you put that file and untar it there.

You should learn some basic shell commands first, such as:

**ls** - lists the files in the current directory
**cd** - change directory; use this to change the current directory
**pwd** - shows you what the current directory is

---

### Post by Marianne_S on 2007-11-21
uh ok :) thank you :)

but if i want to install it and the file is placed in usr/src

how do i do it?

---

### Post by Marianne_S on 2007-11-23
can anybody help me with how to properly install gspca-source from the source code on 7.10?

i sure would like to have my webcam up and running, esp. now with the new skype beta :)

---

### Post by ubuntu.daemon on 2007-12-28
ok so extract it to /usr/src
then cd to the directory
then
```
user@home:/usr/src/gspcav1# nano READ_AND_INSTALL
```

there are some directions i found in the file that help alot GL
:popcorn:

---

### Post by Marianne_S on 2008-03-29
thanks - i did figure it out eventually and i am learning lots of new terminal tricks every day - but thanks anyways :)

---

