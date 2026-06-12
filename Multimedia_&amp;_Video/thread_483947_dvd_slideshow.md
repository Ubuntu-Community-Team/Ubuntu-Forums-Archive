---
title: "dvd slideshow"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by tednugent on 2007-06-25
I just installed dvd-slideshow and cant seem to find it . It shows to be installed in synaptic package manager but I am unable to find it to open it. any help would be greatly apreciated. thanks.

---

### Post by cyberia81 on 2007-07-12
Bump- I am also having the same problem. I installed this using Synaptic, and I found it in /usr/bin, but from that point it will not run. Any help would be greatly appreciated. Thanks!

---

### Post by lhtown on 2007-07-16
dvd-slideshow is a command line program. It does not come with a graphical interface although there might be one available.

Basically, you put all of your pictures in a file, and make a list of the pictures you want in the presentation using a text editor such as gedit and using the format specified in the documentation for dvd-slideshow, indicate the transitions, and duration of each picture. When you are done with that, you run a command from the terminal command line to compile it. You can go make yourself a cup of coffee while it is compiling.... It will take some time.

While this might all seem a bit arcane, it is actually a pretty good way to do it. It is different, but not that hard. Also, you can make advanced presentations on an older computer since you are not compiling in real time. Albeit, you might want to start compiling at night or some other time when you won't be using the computer for awhile.

---

### Post by zzztownsend on 2007-07-17
Hi - I just tried dvd-slideshow
worked perfectly first time!

step by step here: [http://dvd-slideshow.sourceforge.net/wiki/Complete_Example](http://dvd-slideshow.sourceforge.net/wiki/Complete_Example)
I only made two changes: -p option to make sure DVD was PAL not NTSC (I am in UK)
and I used k3b to burn the ISO to DVD

only problem is that it is all command line, but some may say that this is an advantage!!!

---

