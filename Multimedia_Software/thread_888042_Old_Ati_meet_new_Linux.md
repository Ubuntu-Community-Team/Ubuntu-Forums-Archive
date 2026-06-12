---
title: "Old Ati meet new Linux"
date: 2008-08-12
forum: Multimedia Software
---

### Post by twiggy2cents on 2008-08-12
Okay ive been puzzled on this i have a ati 9200se video card running on hardy heron. The current driver is the standard fglrx supplied by linux. I am not interested in gaming and the sorts i just want to activate my svideo tv out port. I am running x11r6 also.

When i try to install the driver ati-installer8.28.8. It is the last supporting driver for my card, supporting "Automated installer and Display Drivers for XFree86 4.3 and X.Org 6.7, 6.8, 6.9, 7.0, 7.1"

During installation i come up with the error of x server: could not detect, deleting temporary directory. Then it ends it.

I am a noob i know this. And im pressed for time so i cant use the search button at the moment. I have tried many guides on the internet and most end up with me running recovery mode.

Any help would be greatly appreciated

---

### Post by overdrank on 2008-08-12
> **twiggy2cents said:**
> Okay ive been puzzled on this i have a ati 9200se video card running on hardy heron. The current driver is the standard fglrx supplied by linux. I am not interested in gaming and the sorts i just want to activate my svideo tv out port. I am running x11r6 also.

When i try to install the driver ati-installer8.28.8. It is the last supporting driver for my card, supporting "Automated installer and Display Drivers for XFree86 4.3 and X.Org 6.7, 6.8, 6.9, 7.0, 7.1"

During installation i come up with the error of x server: could not detect, deleting temporary directory. Then it ends it.

I am a noob i know this. And im pressed for time so i cant use the search button at the moment. I have tried many guides on the internet and most end up with me running recovery mode.

Any help would be greatly appreciated

Hi and welcome, have you tried to use the command using the alt, F2 keys 
```
gksu displayconfig-gtk
``` and enable your extra monitor there.

---

### Post by twiggy2cents on 2008-08-13
it brings up the command window and i type that in, it asks for my password then nothing comes up

---

### Post by overdrank on 2008-08-13
> **twiggy2cents said:**
> it brings up the command window and i type that in, it asks for my password then nothing comes up

Ok you may want to use synaptic manager and install  displayconfig-gtk.

---

### Post by twiggy2cents on 2008-08-14
okay youve been a big help so far...now my problem is that it only recognizes my monitor, when i try to force it to use other drivers the tv screen will loose sync and then come back.   But it wont recognize my tv.  any help?

---

### Post by twiggy2cents on 2008-08-18
bump bump bump?

---

