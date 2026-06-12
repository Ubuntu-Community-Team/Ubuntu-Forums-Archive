---
title: "Playing WMA files in rhythmbox"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by Gerontius on 2008-02-10
Although i have installed all the needed gstreamer codecs (wma files play normally from totem) i can't get wma files to play from rhythmbox.

I can normally see the file in the database and read it's metadata information, but when i double click it there's no sound.

What could be the problem?

P.S. i can't get it to play with MPD/Sonata either - does MPD support WMA?

---

### Post by kostkon on 2008-02-10
Did you install the *w32codecs* package from the [*Medibuntu* repository]("http://medibuntu.org/")?

---

### Post by Gerontius on 2008-02-10
> **kostkon said:**
> Did you install the *w32codecs* package from the [*Medibuntu* repository]("http://medibuntu.org/")?

yes

it didn't help

as i mentioned before - WMA files normally play with totem which also uses gstreamer like rhythmbox

---

### Post by kostkon on 2008-02-10
> **Gerontius said:**
> yes

it didn't help

as i mentioned before - WMA files normally play with totem which also uses gstreamer like rhythmbox

Hmmm. Strange. It happens to have a WMA file and it plays fine in *Rhythmbox*. 

Could you try to run *Rhythmbox* from the terminal, in order to see if it will output an error message when you try to play that file?

---

### Post by Gerontius on 2008-02-10
thank you for your help... i've figured it out

it was caused by pulseaudio-esd deleting esound server. reinstalling esound solved everything :)

---

