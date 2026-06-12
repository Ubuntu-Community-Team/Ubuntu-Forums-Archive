---
title: "no sound"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Kjamx on 2010-03-28
Hm i have a problem

i instald ubuntu 10.04 beta on my laptop medion md 96290

and there is no sound from the inbuild Speakers.

But the funy thing is if i conect headphones to my laptop there is sound

It's my first time using linux.

---

### Post by Kjamx on 2010-03-30
Well i searchd a litle bit the forum and faund

[http://ubuntuforums.org/showthread.php?t=1318474](http://ubuntuforums.org/showthread.php?t=1318474)

And here is how the problem should be fixd

[http://marc-spoor.blogspot.com/2008/02/2008-02-19-sound-finally.html](http://marc-spoor.blogspot.com/2008/02/2008-02-19-sound-finally.html)

Now i would like to know if the same goes for Ubuntu 10.04?
And would like to ask some1 if he could translate that for
a linux noob like me :D

Thx

---

### Post by lidex on 2010-03-31
Open a terminal ("Applications>Accessories>Terminal"). Enter this command:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
and press enter. In the file that opens paste this line at the bottom:
```
options snd-hda-intel position_fix=1 model=auto
```

Save. Close. Reboot.

---

### Post by dabby_yo on 2010-03-31
Make sure Digital is at 100%. I had this kind of issue with my netbook when I upgraded the kernel.

---

### Post by Kjamx on 2010-04-01
Hey lidex thx i am realy greatefull for your help!

I tryd to do something in the terminal myself but
as i said, first time using linux, and from this moment on the
experiance is just great!

I realy like Ubuntu 10.04!

---

