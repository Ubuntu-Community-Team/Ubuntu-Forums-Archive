---
title: "Screen Resolution...where stored?"
date: 2009-04-20
forum: Multimedia Software
---

### Post by Don DeGregori on 2009-04-20
Under System, Preferences, Screen Resolution.
If I make a change to Resolution, where are all the places is it written to? 

I selected the wrong resolution for my Sony HDTV, and now I see "Unsupported Resolution" on HDTV, and no Ubuntu. If I put in Ubuntu LiveCD, all OK. But want to to return to the way it was before I messed with it.

So, where are the directories I have to go to, so I can change the script? I know what I want:  1360 X 768  (16 X 9)

donde

---

### Post by VMC on 2009-04-20
Have a look inside /etc/X11/xorg.conf file and see if you can change it there. Sometimes just renaming that file will build a failsafe xorg.conf

---

