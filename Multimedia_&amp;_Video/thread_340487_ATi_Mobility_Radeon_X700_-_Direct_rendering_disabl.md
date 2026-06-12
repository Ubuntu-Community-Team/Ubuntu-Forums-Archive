---
title: "ATi Mobility Radeon X700 - Direct rendering disabled"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by nolongerlivecd on 2007-01-17
Hi all, I'm currently facing troubles with my ATi Mobility Radeon X700 64MB within Edgy.

I'm trying to get direct rendering on my graphics card instead of using Mesa. I haven't touched the internals of a new system since Dapper in June last year, therefore I cannot recall how to get my direct rendering back. As this is already becoming quite old a graphics card, I hope that somebody could help me with this.

nolongerlivecd@ubuntu$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

[http://paste.ubuntu-nl.org/2221/](http://paste.ubuntu-nl.org/2221/) (xorg.0.log)

[http://paste.ubuntu-nl.org/2220/](http://paste.ubuntu-nl.org/2220/) (xorg.conf)

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) (instructions followed for installation of ATi Proprietary drivers)

Thanks in advance.

---

### Post by gaboro on 2007-01-17
hi,
try switching off the usplash

bye
gaboro

---

### Post by mirr0r on 2007-01-18
hi,

I hope this help you:

[link]("http://ubuntuforums.org/showthread.php?p=2029750#post2029750")

bye,

MiRr0r

---

### Post by nolongerlivecd on 2007-01-18
> **mirr0r said:**
> hi,

I hope this help you:

[link]("http://ubuntuforums.org/showthread.php?p=2029750#post2029750")

bye,

MiRr0r

Hi, the link is correct.

lrwxrwxrwx 1 root root     16 2007-01-16 05:16 libGLEW.so.1.3 -> libGLEW.so.1.3.4
-rw-r--r-- 1 root root 188032 2006-07-06 22:53 libGLEW.so.1.3.4
lrwxrwxrwx 1 root root     10 2007-01-16 19:21 libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     12 2007-01-17 23:28 libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 642552 2007-01-09 16:52 libGL.so.1.2
-rw-r--r-- 1 root root 684432 2006-10-12 11:53 libGLU.a
lrwxrwxrwx 1 root root     11 2007-01-16 19:21 libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root     20 2007-01-16 05:16 libGLU.so.1 -> libGLU.so.1.3.060501

---

### Post by nolongerlivecd on 2007-01-18
> **gaboro said:**
> hi,
try switching off the usplash

bye
gaboro

Sorry to bother you, but how does that work? And how do I go about doing it?

---

### Post by mirr0r on 2007-01-18
> **nolongerlivecd said:**
> Hi, the link is correct.

lrwxrwxrwx 1 root root     16 2007-01-16 05:16 libGLEW.so.1.3 -> libGLEW.so.1.3.4
-rw-r--r-- 1 root root 188032 2006-07-06 22:53 libGLEW.so.1.3.4
lrwxrwxrwx 1 root root     10 2007-01-16 19:21 libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     12 2007-01-17 23:28 libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 642552 2007-01-09 16:52 libGL.so.1.2
-rw-r--r-- 1 root root 684432 2006-10-12 11:53 libGLU.a
lrwxrwxrwx 1 root root     11 2007-01-16 19:21 libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root     20 2007-01-16 05:16 libGLU.so.1 -> libGLU.so.1.3.060501

Can u post me your Xorg.conf file? Did u seen mine attachment? Have u followed the how-to (method 2) linked [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Pre-Installation_Checks")?

---

### Post by gaboro on 2007-01-18
> **nolongerlivecd said:**
> Sorry to bother you, but how does that work? And how do I go about doing it?

you need to edit the /boot/grub/menu.lst file, for example w/ sudo gedit

look for your boot line, i.e.

kernel      /boot/vmlinuz-2.6.17-10-386 root=UUID=c46904f5-566e-487a-af0a-5f725129579b ro quiet splash

then remove the splash from the end of the line

if it does not help/work, you can anytime put it back

have luck
cheers
gaboro

---

### Post by nolongerlivecd on 2007-01-19
> **mirr0r said:**
> Can u post me your Xorg.conf file? Did u seen mine attachment? Have u followed the how-to (method 2) linked [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Pre-Installation_Checks")?

Hi, it's in my first post, and that was the method I used to install, as if I recall correctly, I used it too and Dapper and Breezy with no troubles.

---

### Post by nolongerlivecd on 2007-01-19
Done! It was a libGL conflict, not to mention several Xorg problems

---

### Post by commonplace on 2007-01-28
> **nolongerlivecd said:**
> Done! It was a libGL conflict, not to mention several Xorg problems

Can you be more specific as to what you did to fix this exactly?

/Kevin

---

