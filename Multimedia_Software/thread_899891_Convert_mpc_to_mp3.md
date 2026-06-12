---
title: "Convert mpc to mp3"
date: 2008-08-24
forum: Multimedia Software
---

### Post by munkiepus on 2008-08-24
I was just reading a thread about converting mpc to mp3 the thread is now locked but just incase anyone needs it here is a small script to convert a whole folder of mpc to mp3 the original thread is here: [http://ubuntuforums.org/showthread.php?t=82704](http://ubuntuforums.org/showthread.php?t=82704)


first you need to download the mppdec program you can get it from [http://www.musepack.net/index.php?pg=lin](http://www.musepack.net/index.php?pg=lin) 

unzip it and copy mppdec to your /usr/bin directory 

you will also need to install lame 

sudo apt-get install lame

once those are installed use this command in the directory with the mpc files:

for i in *.mpc ; do mppdec "$i" - | lame -h -b 192 - "${i%mpc}mp3" ; done



hope this helps someone :)

---

### Post by ctiebs on 2011-01-30
Hi there. I'm very new to Linux. How do I copy mppdec to my /usr/bin directory? When I copy the extracted files and try to paste them in /file system/usr/bin the option to paste is disabled. 

Such a noooob!

Thanks

---

### Post by ron999 on 2011-01-30
Hi
You need to be 'root'.
Like administrator.
Use command:-
```
gksudo nautilus
```

---

### Post by andrew.46 on 2011-01-31
Mind you it is an old convention to establish your own 'bin' folder in $HOME and the add it to your path. I use this on my own system with the following in $HOME/.bashrc:

```
export PATH=$PATH:/home/andrew/bin
```

In this I keep an assortment of scripts, the nero executables and a few other odds and ends, the musepack encoders and decoders would work in this fashion too.

---

