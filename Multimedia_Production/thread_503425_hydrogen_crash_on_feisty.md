---
title: "hydrogen crash on feisty"
date: 2007-07-17
forum: Multimedia Production
---

### Post by wbrown on 2007-07-17
Greetings:  

I am getting a crash everytime I try to run hydrogen with feisty.  Can anyone here help me debug this further?  Thanks in advance.

bill@localhost:/usr/share/hydrogen/data$ hydrogen -V
Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8
Warning: error loading locale: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8.qm

Hydrogen 0.9.3 [May 18 2007]  [[http://www.hydrogen-music.org]](http://www.hydrogen-music.org])
Copyright 2002-2005 Alessandro Cominu


Compiled modules:  (FLAC) (Jack) (Alsa) (OSS) (LRDF)
Verbose log mode = active

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

Using data path: /usr/share/hydrogen/data
[INFO]      Preferences         INIT
[INFO]      Preferences         [loadPreferences] Loading preferences file (GLOBAL) [/usr/share/hydrogen/data/hydrogen.default.conf]
[INFO]      Preferences         [loadPreferences] Loading preferences file (USER) [/home/bill/.hydrogen/hydrogen.conf]
Segmentation fault (core dumped)
bill@localhost:/usr/share/hydrogen/data$

---

### Post by wbrown on 2007-07-17
Ok.  

For this:
**Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8 **

From here:  [http://www.hydrogen-music.org/forum/?action=show_thread&thread=209&fid=3&page=1](http://www.hydrogen-music.org/forum/?action=show_thread&thread=209&fid=3&page=1) 
Do this in /usr/share/hydrogen/data/i18n/updateTranslations.sh  
1) remove the relative paths and 
2) add   "$CMD ../data/i18n/hydrogen.en_US.UTF-8.ts" to the bottom of the other locales listed.
3) run the updateTranslations.sh script.

For this:
**Segmentation fault (core dumped)**

I found that the /usr/share/hydrogen/data/DefaultSong.h2song was missing.  reinstalling the package with synaptic resolved the issue and hydrogen started.

Maybe this will be useful to someone else here. 

Thanks.
Bill.

---

