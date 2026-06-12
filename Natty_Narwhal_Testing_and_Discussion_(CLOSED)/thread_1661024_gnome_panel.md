---
title: "gnome panel"
date: 2011-01-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2011-01-06
after updates the gnome panel came back, how do you get rid of it ?

i tried pkill gnome-panel, it goes away for a few seconds and comes back :-(

---

### Post by lidex on 2011-01-06
Are you booting into classic or desktop session?

---

### Post by cecilpierce on 2011-01-06
> **lidex said:**
> Are you booting into classic or desktop session?

desktop, i tried ccsm unchecking gnome compatibility but its acting funny !

---

### Post by lidex on 2011-01-07
I finally ran the Thurs updates and **bam**, I had the same problem. After some soul-searching I think I figured it out. Go to root nautilus:
```
gksu nautilus
``` 
Navigate to ```
/usr/share/gnome-session/sessions
```
You should have 4 files there. Double-click 'ubuntu.session' to open in your default text editor. Edit this line:
```
Required=windowmanager;panel;filemanager;
```
to look like this:
```
Required=windowmanager;filemanager;
```
Then remove completely this line:
```
Required-panel=compiz
```
Save the file and close.
Ctrl-Alt-Backspace and log back in.

While I was in there I went ahead and edited the 'classic-gnome.session' file as well.
I changed required-windowmanager to compiz.

---

### Post by kyleabaker on 2011-01-09
Thanks @lidex! That fixed this problem for me. I just edited the first file though. :D

---

### Post by cecilpierce on 2011-01-09
@lidex, is this right ? If so I still have the darn panel :confused:

---

### Post by lidex on 2011-01-09
I think you want gnome compatibility enabled and also select the unity profile in ccsm with gconf backend and integration selected.
You may need to tweak your 'required components' in gconf editor.

---

### Post by cecilpierce on 2011-01-10
Just updated 2 Natty installs and the gnome-panel is gone! :o
Now if the pull down menus would get fixed, but I guess something else will go south. :(

---

### Post by lidex on 2011-01-10
> **cecilpierce said:**
> Just updated 2 Natty installs and the gnome-panel is gone! :o
Now if the pull down menus would get fixed, but I guess something else will go south. :(

With any luck! [-o<

---

