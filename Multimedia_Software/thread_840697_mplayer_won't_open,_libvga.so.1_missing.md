---
title: "mplayer won't open, libvga.so.1 missing"
date: 2008-06-25
forum: Multimedia Software
---

### Post by weidongche on 2008-06-25
Hello smart gurus, I'm having trouble with installation of mplayer.  I am using Hardy Heron.  I installed mplayer with: apt-get install mplayer.  At first it started ok with gmplayer.  But a few days later, none of the commands work: mplayer or gmplayer.  And the error message from the terminal says: 
"mplayer: error while loading shared libraries: libvga.so.1: cannot open shared object file: No such file or directory"

Please, for those who are able, help me out here!!!

Thanks!

---

### Post by andrew.46 on 2008-06-25
Hi,

You are missing these files:

```
/usr/lib/libvga.so.1
/usr/lib/libvga.so.1.4.3
```

Looks like you need definitely the first of the files below, the 'dev' file will be usefull later if you ever compile against libvga:

```
$ sudo apt-get install libsvga1 libsvga-dev
```

You can see the details [here]("http://packages.ubuntu.com/hardy/i386/libsvga1/filelist"). A more interesting question is how did the file become mislaid :-).

   Andrew

---

### Post by weidongche on 2008-06-26
Thank you Andrew, but "$ sudo apt-get install libsvga1 libsvga-dev" did not work.  libvga.so.1 is no where to be found.  In a few days, if I still couldn't get it to work.  I will just reinstall Ubuntu.  I am little dissappointed with ubuntu now.  So many things did not work as I hoped.

---

### Post by markbuntu on 2008-06-26
libvga1 and libvga-dev are in the Universe repository. You must have universe enabled in your software sources in order to get them.

---

### Post by mc4man on 2008-06-26
try this instead
```
sudo apt-get install libsvga1 libsvga1-dev
```

---

### Post by weidongche on 2008-06-26
Guys,

I didn't encounter any trouble installing libsvga1 and libsvga1-dev, but no avail.  But never mind, I will reinstall ubuntu.  I am a little swayed now to try red hat.  What do you guys think about red hat.  Are ubuntu and red hat similar enough for me to make a smooth transition?

Anyway, thank you for your prompt respond.  This is the first time I post on a forum.  I could not possibly anticipate that people would respond to my question to quickly.  I appreciate this nice first experience.

---

