---
title: "wavemon: fatal error: could not get range information"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by tasuki on 2006-06-02
Yesterday I upgraded my Breezy to Dapper.

Since then, wavemon stopped working.

There already was one post about this, but the forum is closed now:
[http://ubuntuforums.org/showthread.php?t=184852]("http://ubuntuforums.org/showthread.php?t=184852")

I have some problems with my wifi so I'd really welcome wavemon working again so that I can check it...

---

### Post by tux73 on 2006-06-03
Same to me. I'm using ndiswrapper.
However, I tried to compile it directly from source and got an error while 'make' in config.h and config.c.
Did you try to compile from source?
[http://www.janmorgenstern.de/projects-software.html](http://www.janmorgenstern.de/projects-software.html)

edit:
do you have a ~/.wavemonrc ? I don't!

---

### Post by nanocosm on 2006-06-06
Try one (or both) of the following:

```
export TERM=vt100
wavemon -i ethX
```

and recompile it from source:
```

sudo apt-get -b source wavemon
sudo dpkg -i wavemon_0.4.0b-8_i386.deb
```

and tell if that works ;-)

---

### Post by Deusiah on 2006-06-07
I tried both of your suggestions however it dies with exactly the same error message mentioned above.

---

### Post by forquato on 2006-06-13
I have exactly the same problem!!! :confused: 

forquato

---

### Post by Riddian on 2006-07-04
I found out it's crashing on the info screen, if you create a file ~/.wavemonrc and place "startup_screen=histogram" inside it works but still crashes if you try to view the info screen.

---

### Post by msbrentlinger on 2006-08-11
i feel your pain... i fought this forever too

its something about it being complied with gcc3.4 vs gcc-4 thats in dapper? i dunno that could be completely wrong but it seems to have something to do with it from other stuff ive read...  heres what got it going for me,i just got a newer version of package 

wget [http://ftp.us.debian.org/debian/pool/main/w/wavemon/wavemon_0.4.0b-9_i386.deb](http://ftp.us.debian.org/debian/pool/main/w/wavemon/wavemon_0.4.0b-9_i386.deb)
sudo dpkg -i wavemon_0.4.0b-9_i386.deb 

now it works like a champ

---

