---
title: "the sexiest way to rip and burn a cd through the command line"
date: 2010-05-13
forum: Multimedia Software
---

### Post by shantiq on 2010-05-13
[COLOR="Blue"][B]many things in life are difficult so treat yourself to some relief once in a while and that is one way how to


RIP FROM WODIM
==============

 To copy an audio CD in the most accurate way, first run

```
           icedax dev=/dev/cdrom -vall cddb=0 -B -Owav

```
       and then to write run

```
           wodim dev=/dev/cdrw -v -dao -useinfo -text  *.wav
```


Files wav get stored in your home folder   delete afterwards if you wish to



PS :   ALL this info is to be found in the wodim manual


to see original text enter ```
man wodim
```in your terminal  Applications/Accessories/Terminal      
[/B][/COLOR]

---

