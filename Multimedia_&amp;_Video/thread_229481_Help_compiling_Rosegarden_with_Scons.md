---
title: "Help compiling Rosegarden with Scons"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by jon_benge on 2006-08-04
I am trying to compile Rosegarden with scons, but when I type scons configure I get the following error:

```
megamaced@emachines3220:~/rosegarden-1.2.4$ scons configure
scons: Reading SConscript files ...
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.5.2
Checking for the qt library       :  qt was not found
Please set QTDIR first (/usr/lib/qt3?) or try scons -h for more options
```

How should I go about this?

I am running Kubuntu 6.06

Thanks in advance

---

### Post by croak77 on 2006-08-04
Try installing libqt3-mt-dev.

---

### Post by jon_benge on 2006-08-04
Done that, but still no go :(

---

### Post by megamaced on 2006-08-05
EDIT: whoops, wrong username! I am actually Jon benge, but using a different user name :)

Well I've got past this hurdle at least!

I installed the kdelibs and kdelibs4-dev packages and now it works. But... :)

Now I get this:

```
megamaced@emachines3220:~/rosegarden-1.2.4$ scons configure
scons: Reading SConscript files ...
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.5.2
Checking for the qt library       :  qt was found as /usr
Checking for uic                  :  uic was found as /usr/bin/uic
Checking for moc                  :  moc was found as /usr/bin/moc
Checking for the qt includes      :  the qt headers were found in /usr/include/qt3/
Checking for the kde includes     :  the kde headers were found in /usr/include/kde/
Checking for pkg-config ... ok
Checking for alsa >= 1.0 ... ok
Checking for jack >= 0.77 ... ok
Checking for dssi >= 0.4 ... failed
Checking for C header file ladspa.h... no
Checking for lrdf_init() in C library lrdf... no
Checking for liblo >= 0.7 ... failed
Checking for xft >= 2.1.0 ... ok
```

And that was AFTER I downloaded and compiled DSSI, lrdf and liblo :confused: 

Anyways, i've gone ahead with the 'make' because I can't find a fix at this time. I am hoping that DSSI support will just work, but I doubt it!

For some reason, the rosegarden4 package in the ubuntu repositories keeps crashing on me. It loads up the Rosegarden splash screen, but the sequencer fails every time.

---

### Post by jsmanness on 2006-08-20
Magamaced,

How did you get kdelibs4-dev installed to have the kde includes folders/files?  I am assuming that you have kdelibs4-dev to get these files but synaptic won't allow me to download it because I have "unresolvable dependencies."  After doing surfing the net, it seems that other people are having the same problems installing kdelibs4-dev as well. If you know how to get around this please let us know.  

Thanks,

Jon Manness

---

### Post by megamaced on 2006-08-20
All i did was type:

```
sudo apt-get install kdelibs kdelibs4-dev
```

I had no problems with dependencies.

Do you have the ubuntu universe and multiverse repositories set up?

---

