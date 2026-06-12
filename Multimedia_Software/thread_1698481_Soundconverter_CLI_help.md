---
title: "Soundconverter CLI help"
date: 2011-03-02
forum: Multimedia Software
---

### Post by grantmeaname on 2011-03-02
I have been in the process of SoundConverter-ing my library to shrink it so it will more easily fit on an SSD. The problem is, it's failed once or twice and so there are about 1700 mp3 files scattered around my Music folder, and there's no easy way to select only them for the GUI mode.


So I have
```
find -name *.mp3
```
which lists all the .mp3 files in the folder, and then
```
| xargs -0
```
which lets the recipient program recieve everything, special characters and all, and finally
```
soundconverter -b
```
which, when given a list of files from a first level folder can convert them all, but for some reason fails when handed information from find. I recognize that find is formatting the results incorrectly for soundconverter, I just don't know how to fix it.

---

### Post by kassoulet on 2011-03-08
Use the GUI !

All you have to do is adding your folder. There is a format selector on the bottom of the AddFolder dialog. Just select mp3 and you are done.

Use a recent version of SoundConverter (1.5+) they are really faster when adding tons of files to convert.

---

