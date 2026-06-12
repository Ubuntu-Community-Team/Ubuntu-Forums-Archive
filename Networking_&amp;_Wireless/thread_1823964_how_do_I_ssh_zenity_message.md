---
title: "how do I ssh zenity message?"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2011-08-12
I've been trying to use putty for windows to ssh zenity to an ubuntu box. 

zenity --info --text"my text here" 
i get the error Gtk-WARNING **: cannot open display. 

so I tried zenity --info --text"my text here" --display=:0.0
to get: Gtk-WARNING **: cannot open display: :0.0

I've tried 0.1 and 1.0 and nothing's working. :confused:

I used xmessage and it worked. I don't know why zenity won't.

---

### Post by spylinux on 2012-01-02
you need to add the display command correctly in the end

zenity --info --text "hi" --display=:0

and it will work

---

### Post by davethewave83 on 2012-01-02
> **spylinux said:**
> you need to add the display command correctly in the end

zenity --info --text "hi" --display=:0

and it will work

Thanks! :D

---

