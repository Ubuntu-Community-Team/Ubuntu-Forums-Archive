---
title: "How do I install MythTube on Mythbuntu?"
date: 2009-10-20
forum: Mythbuntu
---

### Post by RTucker on 2009-10-20
Hi,

I've finally got my muthbuntu system running 0.22 (via mythbuntu-repos) and its working very well. What I'm after now the MythTube plugin. There doesn't seem to be a binary/package avaliable so it has to be compiled from the source avaliable from the mythtv svn.

I downloaded the source and tried to follow the instructions under option 2 from [http://www.mythtv.org/wiki/MythTube#Installation](http://www.mythtv.org/wiki/MythTube#Installation). qmake was fine, but make explodes with errors and doesn't acomplish anything.

Looking through the errors it seems to be looking for some source files of mythtv itself, so, I got an svn checkout of the version of mythtv that I have installed, copied the mythtube folder in to the mythplugins folder and tried to follow option 1 from the same page (the plan was to copile it then steal the mythtube.so and put in in the plugins folder for the existing install). This time I can't get configure to run... I just get:
```

MythMusic requires vorbis.
MythMusic requires FLAC.
MythMusic requires libcdaudio.
MythMusic requires CDDA Paranoia.
MythMusic requires the LAME mp3 encoder.
./configure: 473: taglib-config: not found
test: 473: unexpected operator
MythMusic requires taglib 1.5 or later.
Disabling MythMusic due to missing dependencies.
ERROR: mythconfig.mak not found at /usr/local/include/mythtv/mythconfig.mak
Did you make AND install MythTV first?
Are you using the correct prefix (/usr/local) and sysroot ()?
Bailing out!!

```

Is there an easy way to do this?

---

### Post by elgordo123 on 2009-10-20
Looks like your missing the taglib library.  Google search points to possibly getting it here: 

[https://launchpad.net/ubuntu/+source/taglib](https://launchpad.net/ubuntu/+source/taglib)

Your in uncharted territory - good luck!

---

### Post by theophile on 2009-10-21
Or you could do it the easy way:
```
apt-get install libtag1-dev
```

---

### Post by RTucker on 2009-10-22
Ok, I'll give it a go, but I was really hoping not to have to compile all of mythtv...

Does anyone know what installing dependencies and compiling the whole things will do to my current working install? If I just want to steal mythtube.so and leave my current install in place should I still run make install or just make?

---

### Post by RTucker on 2009-10-25
I can't believe there's no easier way to do this...

I installed libtagl-dev and tried configure again, but apparently I cant even run configure for mythplugins unless I make and make install mythtv itself first. It looks a lot like this will install over the current copy (based on the paths configure looks in...) which I don't want to do...

Surely theres a better way...?

---

