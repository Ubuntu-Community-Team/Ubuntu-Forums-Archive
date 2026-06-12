---
title: "Webcam upside down Ubuntu 10.04 Asus k52N"
date: 2012-11-03
forum: Multimedia Software
---

### Post by Biosteel on 2012-11-03
As the topic follows i've got a real different problem that seems unsolvable regarding my webcam and the asus k52n laptop. I've got the ubuntu 10.04 lts and have to say im Not a newbie nor a pro in ubuntu when ive had it from 7.10.

First of all i will start off to say that ive been literaly dragging the internet about this wierd phenomen and tried every piece of information i'd come over but now im turning myself to you guys. I need some ideas how to turn my webcam back (not only because my girlfriend a 1000 miles away wants to kill me ) But it annoys me aswell. And grammar isnt my thing.

So guys what to do?

---

### Post by Biosteel on 2012-11-04
Bump*

---

### Post by Biosteel on 2012-11-04
cant believe such a low respons in the matter.

---

### Post by BlinkinCat on 2012-11-04
> **Biosteel said:**
> cant believe such a low respons in the matter.

It doesn't help you at all, but I can assure you that there have been quite a few searches on your behalf.
I hope you solve your problem.

---

### Post by Biosteel on 2012-11-04
> **BlinkinCat said:**
> It doesn't help you at all, but I can assure you that there have been quite a few searches on your behalf.
I hope you solve your problem.

Thanks but its really annoying that it doesent work. As i saw on the google the problem regards all the asus KN laptops wich is quite a lot. And none of the solutions they've found out worked for me. Just kind a strange.

---

### Post by BlinkinCat on 2012-11-04
You might look at #14 on this thread - No guarantees though -

[http://ubuntuforums.org/showthread.php?p=9449973](http://ubuntuforums.org/showthread.php?p=9449973)

Cheers - :)

---

### Post by Biosteel on 2012-11-04
> **BlinkinCat said:**
> You might look at #14 on this thread - No guarantees though -

[http://ubuntuforums.org/showthread.php?p=9449973](http://ubuntuforums.org/showthread.php?p=9449973)

Cheers - :)


thanks for the try ut i've already tried everything written on that page. As i said before i have tried all the solutions available on the internet so thats why im on this forum in the first place. :)  Greetings form e pissed of swede :(

---

### Post by BlinkinCat on 2012-11-04
Did you see solution #5 here? -

[http://ubuntuforums.org/archive/index.php/t-1460790.html](http://ubuntuforums.org/archive/index.php/t-1460790.html)

---

### Post by Biosteel on 2012-11-04
Thanks thats a solution i havent seen before. followed, tried, failed. 

Here's the output of that link .

root@zipota-laptop:/home/zipota#  sudo apt-get install libv4l-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libv4l-0:i386
root@zipota-laptop:/home/zipota# dpkg --add-architecture i386
dpkg: unknown option --add-architecture

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !


Seems it doesnt understand the commands but its still right ?

---

### Post by BlinkinCat on 2012-11-04
Please correct me if I'm barking up the wrong tree, but a look on the internet appeared to indicate that the Ausus k52N was 64 bit - could that have caused an error?

Cheers - :D

---

