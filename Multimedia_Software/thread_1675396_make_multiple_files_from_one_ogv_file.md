---
title: "make multiple files from one ogv file"
date: 2011-01-25
forum: Multimedia Software
---

### Post by e24ohm on 2011-01-25
Folks:
I have used Thoggen; however, there is no way to break the output in to multiple files.

I encoded at 1000MB, but now I want to break the file into 40MB chunks. Is there an app that can do this? Does ffmpeg support these feature?

---

### Post by ron999 on 2011-01-25
Hi
MKVmergeGUI will let you create mkv files from your ogv file.
The 'Global' options can 'Enable splitting...after this size'.
So then you'll have 25 mkv files.

If you really do need ogv files then put them in a folder and convert with a command like this:-
```
for f in *.mkv; do ffmpeg -i "$f" -vcodec copy -acodec copy "${f%.mkv}.ogv"; done

```
MKVmergeGUI comes with these packages:- mkvtoolnix mkvtoolnix-gui

EDIT
MKVmergeGUI won't accept ogv files unless it's set to _All Files*_ at 'Choose an input file to add'.

---

