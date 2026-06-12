---
title: "how can i get devede to use both cores?"
date: 2009-03-28
forum: Multimedia Software
---

### Post by markp1989 on 2009-03-28
when running devede, it maxes out one core, whilst the other is idle, is there any way i can make devede run mencoder so that it takes advantage of both cores?

thanks markp1989

---

### Post by markp1989 on 2009-03-28
when i run devede from the terminal, you can see that it only seems to be detecting 1 core, but i know there are 2

```
[mark@markspc ~]$ devede 
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
DeVeDe 3.12c
Locale: en_US.utf8
Using package-installed files
/usr/bin/devede:143: GtkWarning: GtkSpinButton: setting an adjustment with non-z
ero page size is deprecated
[mark@markspc ~]$ devede 
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
DeVeDe 3.12c
Locale: en_US.utf8
Using package-installed files
/usr/bin/devede:143: GtkWarning: GtkSpinButton: setting an adjustment with non-z
ero page size is deprecated
  arbol=gtk.glade.XML(glade,domain="devede")
/home/mark/
Entro en fonts
Salgo de fonts
/home/mark/
Temp Directory is:  /var/tmp
home load:  /home/mark/.devede
linea:  video_format:pal

linea:  temp_folder:/var/tmp/

linea:  multicore:1

linea:
```

edit: fount a setting in ~/.devede to change how many cores

---

