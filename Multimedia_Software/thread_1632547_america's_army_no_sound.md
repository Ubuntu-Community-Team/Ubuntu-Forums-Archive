---
title: "america's army no sound"
date: 2010-11-28
forum: Multimedia Software
---

### Post by mIXpRo on 2010-11-28
there is no sound when i run the game , this is the only problem (graphics etc... all works fine ).
at the terminal i get (after running the game) : 
```
[]("http://forums.linuxmint.com/viewtopic.php?f=49&t=60553&p=347296#")open /dev/[sound/]dsp: No such file or directory
```

i've searched a bit about this at google, the game forum .
and found that the game run openal as the audio driver/something and
openal supoort only for oss , and since new kernels doesn't support oss there is no sound at the game .

there is also something about making alsa support openal .

do anybody know something about the above .

thnx .

---

### Post by Yellow Pasque on 2010-11-28
openal should be configured to use pulse on a fresh install of ubuntu. If it's not. you can manually set it in /etc/openal/alsoft.conf or ~/.alsoft.conf
Look for code that says this, uncomment the drivers line and set pulse first, like so:
```
## drivers:
#  Sets the backend driver list order, comma-seperated. Unknown backends and
#  duplicated names are ignored. Unlisted backends won't be considered for use
#  unless the list is ended with a comma (eg. 'oss,' will list OSS first
#  followed by all other available backends, while 'oss' will list OSS only).
#  An empty list means the default.
drivers = pulse,alsa,oss,solaris,dsound,winmm,port,wave
```

If the app is trying to use OSS driectly, you'll need to use padsp to emulate OSS (or build your own kernel with OSS support):
```
padsp *command*
```

---

### Post by mIXpRo on 2010-11-28
> **Temüjin said:**
> openal should be configured to use pulse on a fresh install of ubuntu. If it's not. you can manually set it in /etc/openal/alsoft.conf or ~/.alsoft.conf
Look for code that says this, uncomment the drivers line and set pulse first, like so:
```
## drivers:
#  Sets the backend driver list order, comma-seperated. Unknown backends and
#  duplicated names are ignored. Unlisted backends won't be considered for use
#  unless the list is ended with a comma (eg. 'oss,' will list OSS first
#  followed by all other available backends, while 'oss' will list OSS only).
#  An empty list means the default.
drivers = pulse,alsa,oss,solaris,dsound,winmm,port,wave
```If the app is trying to use OSS driectly, you'll 


it didn't work but with :
```
padsp *command*
```
it worked .

thnx a lot .

---

### Post by lingenfr on 2010-12-12
Same problem with ut2004. It all worked fine in versions previous to 10.10. Is this going to be fixed or is it a new 'feature'.

---

### Post by Yellow Pasque on 2010-12-12
> **lingenfr said:**
> Same problem with ut2004. It all worked fine in versions previous to 10.10. Is this going to be fixed or is it a new 'feature'.
So did you start ut2004 with padsp command?

Disabling OSS symbols discourages programs from using OSS directly and forces them to use a higher-level construct like gstreamer or SDL to make sound in Ubuntu. Of course, a lot of the programs that use OSS are older and aren't going to be rewritten just because Ubuntu is trying to eliminate OSS. Ubuntu's decision may have been a progressive one in their minds, but users will suffer because they did not find a way to automatically run OSS apps through padsp.

---

