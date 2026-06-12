---
title: "Command Help"
date: 2009-07-25
forum: Multimedia Software
---

### Post by Psycho.mario on 2009-07-25
Hi, after using K9Copy, it gives me a folder full of files named  <title>-chatper1.mpg up to about <title>-chapter20.mpg. I join these together using the cat command (cat <title>-chapter1.mpg <title>-chapter2.mpg... > <title>.mpg) Is there any way i can use the cat command with some kind of wild card, so that i can joing all the files in a directory, IN ORDER.

Thanks

---

### Post by SuperSonic4 on 2009-07-25
```
cat chapter*.mpg > title.mpg
```

Not too sure about order though

---

### Post by bacil on 2009-07-25
what is exact command you using ? . sou can sort things with command sort. give me example of command :-)

are you trying to merge files ?

---

### Post by Psycho.mario on 2009-07-25
@SuperSonic4
That doesnt put them in the right order, that buts 11, 12, 13...., 19 before 1

@bacil
This is the last command i did, i had to write it out by hand, that is why i want an easier way:
```
cat LVK-chapter1.mpg LVK-chapter2.mpg LVK-chapter3.mpg\
LVK-chapter4.mpg LVK-chapter5.mpg LVK-chapter6.mpg\
LVK-chapter7.mpg LVK-chapter8.mpg LVK-chapter9.mpg\
LVK-chapter10.mpg LVK-chapter11.mpg LVK-chapter12.mpg > LVK.mpg
```

Thanks.

---

### Post by martinbaselier on 2009-07-25
if the file with numbers <10 would be name 01 instead of 1 it could be done in several ways.

Rename would be the command for it. I does not look easy to use unless you know perl expressions if I check the manual. 

To add files, sorted you could use find:
find * -exec cat {} \; > output.

cat * uses the access or the modification time.

---

### Post by Psycho.mario on 2009-07-26
I don't understand what your saying

---

### Post by martinbaselier on 2009-07-26
> 
I don't understand what your saying 

My physics teacher in high school used to reply, "That's not a question" to remarks like that. Please explain what you don't understand. 

My first sentence is rather cryptic, I must admit: 
edit: just reread it, posted that late yesterday night, the whole post is rather cryptic. 

The files are not named correctly. 

LVK-chapter1.mpg should be named LVK-chapter01.mpg
LVK-chapter2.mpg should be named LVK-chapter02.mpg
LVK-chapter3.mpg should be named LVK-chapter03.mpg
LVK-chapter4.mpg should be named LVK-chapter04.mpg
...
etcetera 

If the files are named properly, you can use cat * to combine the files. 

You can rename the files with rename.

Forget the statement about the times, I made mistake there (this applies to other commands), so it's not relevant. 
Also forget the find statement, it has some other side effects (it will output all files in subdirectories too)

---

### Post by Psycho.mario on 2009-07-26
Oh, ok. I understand now, thanks. So i just have to rename 1 to 01 and 2 to 02 and so on, then run cat * > final.mpg?   Thanks

---

### Post by Psycho.mario on 2009-07-26
That works perfectly, Thanks so much

---

