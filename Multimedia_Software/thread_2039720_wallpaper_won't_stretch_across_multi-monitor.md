---
title: "wallpaper won't stretch across multi-monitor"
date: 2012-08-09
forum: Multimedia Software
---

### Post by toffer96 on 2012-08-09
My wallpaper is displaying on both monitors separately. rather than spanning across two. This is my own dumb fault, as I recently decided that I wanted to have my wallpapers randomly change every few minutes, so I decided to try some wallpaper changers (wally, wallch, desktop nova) none of which seemed to work very well. At any rate, when I went to uninstall one (dektopnova was the last one I tried, I think), my wallpapers were no longer spanning across my two monitors. Is there a way to restore my display setting to their default setting or something like that? Running 12.04, btw.

Thanks in advance. toffer.

---

### Post by FatFrog on 2012-08-09
nitrogen should help you accomplish this

# sudo apt-get install nitrogen
 
then point nitrogen at your pictures filed

# nitrogen ~*pictures*


Additionally, make sure you have pictures large enough to span both monitors

---

### Post by toffer96 on 2012-08-10
Thx Frog... I'll give it a try.

---

### Post by toffer96 on 2012-08-10
Recieved this error message:

(nitrogen:3207): Gtk-CRITICAL **: IA__gtk_list_store_set_value: assertion `VALID_ITER (iter, list_store)' failed

toffer.

---

### Post by toffer96 on 2012-08-11
Figured it out... nevermind.

---

