---
title: "mp3 joiner"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by shadowboxer_k on 2007-08-26
hi guys,

i was wondering if someone could recommend me a simple program that joins mp3 files. i need it to make my podcast. what do you use?

thanks in advance. :)

---

### Post by rsambuca on 2007-08-26
If you just need to join them end to end very quickly, it is easiest to use the terminal and the "cat" command.  Open a terminal (Applications -> Accessories -> Terminal) and enter the following command:```
cat file1.mp3 file2.mp3 file3.mp3 > outputname.mp3
```  You can join together as many files as you wish in this manner.

---

### Post by shadowboxer_k on 2007-08-27
wow. that looks amazingly simple. thanks so much! i will try it asap.

---

### Post by tgalati4 on 2007-08-27
If you need to edit the files (like fade-ins, cross-fade, etc) then use Audacity.

If you have lots of files to edit in batch mode then use sox.

>sudo apt-get install sox audacity

---

### Post by shadowboxer_k on 2007-08-27
thank you. that looks very helpful. now i'm all set. :)

---

### Post by arijarot on 2007-12-25
> **rsambuca said:**
> If you just need to join them end to end very quickly, it is easiest to use the terminal and the "cat" command.  Open a terminal (Applications -> Accessories -> Terminal) and enter the following command:```
cat file1.mp3 file2.mp3 file3.mp3 > outputname.mp3
```  You can join together as many files as you wish in this manner.

I've been looking for a good mp3 joiner/paster for a while now to no avail. This works beautifully. Thanks ! :KS

---

### Post by OZFive on 2008-04-29
> **rsambuca said:**
> If you just need to join them end to end very quickly, it is easiest to use the terminal and the "cat" command.  Open a terminal (Applications -> Accessories -> Terminal) and enter the following command:```
cat file1.mp3 file2.mp3 file3.mp3 > outputname.mp3
```  You can join together as many files as you wish in this manner.

What directory do the files need to be in for this to work?  I keep getting a "no such file or directory"

Help please :D  

Thanks!

---

### Post by arijarot on 2008-04-30
> **OZFive said:**
> What directory do the files need to be in for this to work?  I keep getting a "no such file or directory"

Help please :D  

Thanks!

Either be in the file's directory or specify the path to both the input and the output file.

For example cd to file's directory or cat /home/username/file1 /home/username/file2 > /home/username/fileout

---

