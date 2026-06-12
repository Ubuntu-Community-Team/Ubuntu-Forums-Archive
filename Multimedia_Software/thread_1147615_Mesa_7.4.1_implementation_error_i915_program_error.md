---
title: "Mesa 7.4.1 implementation error: i915_program_error"
date: 2009-05-03
forum: Multimedia Software
---

### Post by diedo on 2009-05-03
since i enabled blur windows and animations in compiz everything goes Black 

or picees of black things 

i'd clicked Crtrl+alt+F3 and wrote 

startx 

some errors had appeared but i don't know what is it was 

then i wrote 

```
sudo /etc/init.d/gdm stop 

startx
```


after that my Desktop appeared but when i move my cursor the screen turns to black not all screen some of it 

then i pressed Ctrl+ALT+F3

and that's what appeared 

```
Mesa 7.4.1 implementation error: i915_program_error: Exceeded Max nr indirect texture lookups .
Please report at Bugzilla.freedesktop.org
```

i've edit my Xorg.conf file with vesa and intel but was still the same 

Then i remove /.gconf/apps/compiz  the whole folder and startx everything was loaded perfectly execpt when i touch enable Blur windwos  in compiz 
i get back to ZERO point :confused:


i've Dell inspiron 1300 with Intel 915GM Graphics Card 

attached Xorg.0.log file

---

### Post by diedo on 2009-05-03
Bump

---

### Post by diedo on 2009-05-04
what is your problem guys are you really don't know what is the cause of this messages ?

:(

---

