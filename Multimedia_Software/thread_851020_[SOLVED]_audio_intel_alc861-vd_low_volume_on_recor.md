---
title: "[SOLVED] audio intel alc861-vd low volume on recordmydeskop"
date: 2008-07-06
forum: Multimedia Software
---

### Post by Creative2 on 2008-07-06
well i am using 

**kubuntu 8.04**
 
audio card 

**intel alc861-vd on toshiba laptop a100-063**

driver:

** default installation **

problem:


when i record audio with **audacity** (alsa default):

it works fine ah very fine with nice sound** nice volume**

when i use silly **recordmydeskotp i have low volume.**

what's the problem i have set volume and boost on kmix but with a software works fine and with another no? what a bad issue!!!

---

### Post by Creative2 on 2008-07-07
up

---

### Post by Yellow Pasque on 2008-07-08
If you would like to build the latest version of ALSA from source, here are some scripts to do that: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

I'm not sure if that will fix the problem.

You can also try OSS4.

---

### Post by Creative2 on 2008-07-08
well but isn't strange i have to compile again audio driver if with audacity it's working fine?
 

well i suppose is the last way i can take... -.-'' what silly issue!

---

### Post by Creative2 on 2008-07-08
well now i have 1.0.17rc3 but still the same.... i have tried to set quality 10 i have tried to compile recordmydestop i have now new driver alsa 1.017rc3  wtf what's the problem with recormydestop

---

### Post by Creative2 on 2008-07-08
up

---

### Post by Creative2 on 2008-07-09
i was on irc channel...and i have asked 

they have said  it'a a recordmydesktop bug.... '-..-'

---

### Post by Creative2 on 2008-07-14
well i am pretty noob on alsa and sound system because i really i have not time but on this week end i have lost my data partiton :'( so i have reinstalled every damned thing (of course i know foremost and photorec and testdisk) and now  i have solved :



I have written here about what i do to increase my mic volume

[http://fuocotools.byethost13.com/index.php?topic=149.0](http://fuocotools.byethost13.com/index.php?topic=149.0)

anyway i leave here a copy:


first it's very important sox library so 

sudo apt-get install sox libsox-fmt-all 

then open a terminal and type

```
kdesudo systemsettings
```

--->Sound System
------>Hardware
-------->Select Device (remember the default should be Autodetect)
--------->Opend Sound System

close
[B]
open kmix[/B]
------>Settings
------->Configure KMix
-------->set un-checkek Restore Volumes on log in

----------> Now set your volumes on kmix

```
kdesudo systemsettings

```
--->Sound System
------>Hardware
-------->Select Device
--------->Set Autedetect or what you had before

close
now everythings works in my computer , but you could see this 

[http://docs.kde.org/stable/en/kdemultimedia/kmix/tips-and-tricks.html#id2545838](http://docs.kde.org/stable/en/kdemultimedia/kmix/tips-and-tricks.html#id2545838)

et voila'  every silly things are working now :

no alsa recompiling stuff
no oss4 compiling stuff


... pretty simple...xD shame i didnt discover that before

---

### Post by nowardev on 2008-10-04
thanks it worked for me

---

