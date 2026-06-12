---
title: "Unable to burn video in Brasero"
date: 2009-04-08
forum: Multimedia Software
---

### Post by Grievous on 2009-04-08
I have tried burning some video into a blank DVD and it seems that the "Burn" button is greyed out.  I have look for answers but it hasnt worked for me.  This is part of the log file:

(brasero:6286): BraseroBurn-DEBUG: At burn-caps.c:3640: Adding blank caps for Disc CD RW appendable with data with audio 
(brasero:6286): BraseroBurn-DEBUG: At burn-caps.c:3640: Adding blank caps for Disc CD RW appendable with data 
(brasero:6286): BraseroBurn-DEBUG: At burn-caps.c:3640: Adding blank caps for Disc CD RW appendable with audio 
(brasero:6286): BraseroBurn-DEBUG: At burn-caps.c:3640: Adding blank caps for Disc CD RW closed with data with audio 
(brasero:6286): BraseroBurn-DEBUG: At burn-caps.c:3640: Adding blank caps for Disc CD RW closed with data 
(brasero:6286): BraseroBurn-DEBUG: At burn-caps.c:3640: Adding blank caps for Disc CD RW closed with audio 
(brasero:6286): BraseroBurn-DEBUG: At burn-caps.c:3640: Adding blank caps for Disc CD RW blank 
(brasero:6286): BraseroBurn-DEBUG: At burn-plugin.c:998: Module wodim successfully loaded
(brasero:6286): BraseroBurn-DEBUG: At burn-plugin-manager.c:459: loading /usr/lib/brasero/plugins/libbrasero-vob.so
(brasero:6286): BraseroBurn-DEBUG: At burn-plugin.c:994: Module encountered an error while registering its capabilities:
unknown error
(brasero:6286): BraseroBurn-DEBUG: At burn-plugin-manager.c:492: Load failure, no GType was returned (null)
(brasero:6286): BraseroBurn-DEBUG: At burn-plugin-manager.c:459: loading /usr/lib/brasero/plugins/libbrasero-cdrecord.so
(brasero:6286): BraseroBurn-DEBUG: At burn-plugin.c:994: Module encountered an error while registering its capabilities:
cdrecord is a symlink pointing to another program. Use the target program instead.
(brasero:6286): BraseroBurn-DEBUG: At burn-plugin-manager.c:492: Load failure, no GType was returned cdrecord is a symlink pointing to another program. Use the target program instead.

What I guess is that there is a problem loading /usr/lib/brasero/plugins/libbrasero-vob.so

[http://bugzilla.gnome.org/show_bug.cgi?id=564169#c6]("http://bugzilla.gnome.org/show_bug.cgi?id=564169#c6")//bugzilla.gnome.org/show_bug.cgi?id=564169#c6[/URL] said that I might be missing: -ffenc_mpeg2video
-ffenc_ac3
-ffenc_mp2
-mplex

I searched for those items in Synaptic but can't find a search results.  Am I missing something or am I doing something wrong?

---

### Post by B4RR13N705 on 2009-04-08
Brasero have sme bugs... If you want to burn video, then use DeVeDe, is amazing!
```

sudo apt-get install devede

```
:popcorn:

---

### Post by Grievous on 2009-04-09
Thanks! Installing devede now :guitar:

---

### Post by Swithun on 2009-05-13
I have a similar problem (Brasero won't burn video). I think it's due to the fact that the ffenc_mpeg2video plugin isn't installed on my PC. I'm running Jaunty. I've loaded a good many extra gstreamer libraries, but it's still not appeared.

Any help greatly appreciated.:smile:

---

### Post by B4RR13N705 on 2009-05-13
I also had this problem in ubuntu. In ubuntustudio it records great! :popcorn:

---

### Post by whitemagicwoman on 2010-09-12
In fixing the mplex error, 

sudo apt-get install gstreamer0.10-plugins-bad-multiverse
worked for me.  I'm not sure about the rest.

---

