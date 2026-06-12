---
title: "Cannot Open .BIN File [HELP!!]"
date: 2010-12-30
forum: Multimedia Software
---

### Post by shivugh on 2010-12-30
Hi Fellas,

I have downloaded a video series which are packed in .bin file. I am trying to open it but unable to do so. Here's what happened when I tried to open it-

Jon@Jon-laptop:~/Desktop$ chmod 755 cfe-vtccp2007.bin
Jon@Jon-laptop:~/Desktop$ ls -l cfe-vtccp2007.bin
-rwxr-xr-x 1 Jon Jon 312813648 2007-07-07 23:21 cfe-vtccp2007.bin
Jon@Jon-laptop:~/Desktop$ sudo ./cfe-vtccp2007.bin
./cfe-vtccp2007.bin: 1: Syntax error: "&" unexpected (expecting ")")

I tried this too-

Jon@Jon-laptop:~/Desktop$ chmod a+x ./cfe-vtccp2007.bin
Jon@Jon-laptop:~/Desktop$ ./cfe-vtccp2007.bin
bash: ./cfe-vtccp2007.bin: cannot execute binary file

Help would be much appreciated. Thanks in advance.

---

### Post by shivugh on 2010-12-30
It's solved.

I used 

sudo aptitude install bchunk

bchunk cfe-vtccp2007.bin cfe-vtccp2007.cue cfe-ctccp2007.iso

Done!

---

