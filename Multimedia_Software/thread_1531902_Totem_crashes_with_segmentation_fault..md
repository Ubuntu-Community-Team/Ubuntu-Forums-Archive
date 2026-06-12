---
title: "Totem crashes with segmentation fault."
date: 2010-07-15
forum: Multimedia Software
---

### Post by Vik Vasilev on 2010-07-15
I searched the forums and google, and I found no solution for this.
Can anyone help.

Yesterday Totem started crashing - the window shows for a second and then dissapears. 
Reinstalling via synaptic didnt help.

Here is the error shown in a Terminal

```
vik@vik-desktop:~$ totem 

(totem:4433): Gtk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gtk/gtkliststore.c:797: 
Invalid column number 6 added to iter (remember to end your list of columns with a -1)
Segmentation fault

```I removed all installed gstreamer codecs, and it still crashes, and I now I have no clue why I cant use the app.

I`m using a fresh install of Karmik Koala (over my ubuntu 10.04 without a format )

---

### Post by Vik Vasilev on 2010-07-16
Anyone?


BUMP

---

### Post by Vik Vasilev on 2010-07-16
After installing all available updates, everything works fine now.
    "Thanks for the help" =;

---

