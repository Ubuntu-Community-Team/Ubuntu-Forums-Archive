---
title: "double click iso or nrg dvd disc image"
date: 2008-08-11
forum: Multimedia Software
---

### Post by gaspard.leon on 2008-08-11
Hi,

I had the problem of trying to play my disc images without mounting or burning them.

First:
[LIST=1]
[*]I have switched to the xine backend for totem etc to get working subtitles/menus
[*]xine supports this type of argument: dvd:/[path to dvd file]
e.g. dvd://home/username/dvdimage.iso
[*]using the nautilus right-click menu you can "Open with" and put in a custom command such as:
```
totem dvd:/%f
```
And it works!!
```
xine dvd:/%f
```
would work too if you like xine (I prefer totem)
[/LIST]

also .nrg (nero burning ROM's iso-like image format) is similar to ISO in a lot of cases will simply work as one.

so I used a package called assoGiate
```
sudo apt-get install assogiate
```
"File Types Editor" to alter the "raw CD image" type to include *.nrg

That is like magic, as soon as you change it and hit refresh in nautilus your nrg files appear as CD images.

thought I would share my experiences...

---

