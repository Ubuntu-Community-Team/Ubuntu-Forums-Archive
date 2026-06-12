---
title: "Amarok ignores media keys"
date: 2011-08-21
forum: Multimedia Software
---

### Post by AlanDeSmet on 2011-08-21
Updated Ubuntu 10.04. Amarok 2.3.0. Dell Inspiron 1526.

My laptop has next, previous, and play/pause buttons that I would like to work with Amarok.  Amarok's default configuration appears to globally map these buttons exactly as I would like.  Amarok calls the buttons Media Next, Media Previous, and Media Play.  If I specify a custom mapping and hit the button, it maps the Media Next, Media Previous, and Media Play as expected.  (And indeed if I try to some other command to this, Amarok warns me that it's multiply defined.)  Clearly Amarok is capable of seeing these inputs.

However, they simply don't work.  Outside of setting a custom key, Amarok does not respond to them, even if Amarok has focus.  If I change the mapping from Global to Shortcut, they still don't work.

I found some online discussions about this, but all appear to be Amarok 1.x era.  The configuration settings appear very different and not relevant.

Can anyone suggest on how to get these buttons working in my Amarok?

---

### Post by Mamarok on 2011-08-21
I guess you are using Gnome, don't you? Then you should have a look at the script for Amarok 2.x here: [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys+2?content=103448](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys+2?content=103448)

FWIW, the multimedia keys on both my Lenovo laptops work fine under Kubuntu

---

