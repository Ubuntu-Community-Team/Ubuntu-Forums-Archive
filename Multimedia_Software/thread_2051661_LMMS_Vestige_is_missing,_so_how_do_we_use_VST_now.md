---
title: "LMMS Vestige is missing, so how do we use VST now?"
date: 2012-09-01
forum: Multimedia Software
---

### Post by Jonatello on 2012-09-01
extensive searching showed me many online discussions (here and elsewhere) that sort of seemed to address this, but not directly.

I am running 12.04, just installed LMMS version 0.4.13

there is no Vestige in the instruments section. i read somewhere, one person claimed vestige is no longer part of lmms. 

in the presets section, it still has a folder for vestige though (albeit empty). in the settings, it still asks me to specify my VST folder (which i did).

has anyone figured out how to get VSTs to work?

---

### Post by Phazonx on 2012-09-04
I also need to know this...I'm a musician that has upgraded from 11.04 to ubuntu 12.04 and now all of a sudden none of my projects are playing properly cause the VST adaptor is no longer there in the program... I sure hope there's a way to get it back.

---

### Post by marin123 on 2012-09-11
+1

Reading the changelog, they state that they have improved VST support, but I didn't find a way to load VSTs in LMMS.

---

### Post by gargl on 2013-01-02
bump +1
lmms 0.4.10
amd64 Ubuntu 12.04 (precise pangolin)
Trinitydesktop

It might be that the problem is related to the architecture version
installed (i386 vs amd64 i.e. 32 vs 64 bit?).

Because the package list for the 32bit architecture version
contains files such as:
/usr/lib/lmms/libvestige.so
[...]
/usr/lib/lmms/libvstbase.so
/usr/lib/lmms/libvsteffect.so
source:  [http://packages.ubuntu.com/precise/i386/lmms/filelist](http://packages.ubuntu.com/precise/i386/lmms/filelist)

whereas compareable files seem to be missing in the 64bit architecture
version.
See: [http://packages.ubuntu.com/precise/amd64/lmms/filelist](http://packages.ubuntu.com/precise/amd64/lmms/filelist)

So maybe this "problem" is "known"?!
Can anyone confirm, respectively confute this hypothesis by
informing us that he/she has lmms installed on a 64bit (k)ubuntu
_with_ working VST support?!

---

### Post by Aditya Srivastava on 2013-01-12
> **Jonatello said:**
> extensive searching showed me many online discussions (here and elsewhere) that sort of seemed to address this, but not directly.

I am running 12.04, just installed LMMS version 0.4.13

there is no Vestige in the instruments section. i read somewhere, one person claimed vestige is no longer part of lmms. 

in the presets section, it still has a folder for vestige though (albeit empty). in the settings, it still asks me to specify my VST folder (which i did).

has anyone figured out how to get VSTs to work?
 Vestige is still a part of lmms. You may use the windows version of lmms to confirm this fact. The linux version seems to have some issue. How ironical!](*,)

---

### Post by marin123 on 2013-01-12
I installed it from this repo, works like a charm :)

[http://ppa.launchpad.net/irie/lmms/ubuntu](http://ppa.launchpad.net/irie/lmms/ubuntu)

---

### Post by Aditya Srivastava on 2013-01-14
> **marin123 said:**
> I installed it from this repo, works like a charm :)

[http://ppa.launchpad.net/irie/lmms/ubuntu](http://ppa.launchpad.net/irie/lmms/ubuntu)
Thanks!):P

---

### Post by djallalnamri on 2013-01-26
i have installed lmms.exe with wine on ubuntu 12.10 and uptill now it works very well ... this is an option in case you have problems with lmms-vst as i did ...

---

### Post by djallalnamri on 2013-01-26
not so very well after all

---

