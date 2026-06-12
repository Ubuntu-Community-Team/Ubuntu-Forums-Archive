---
title: "Need a script to call Mplayer and rmvbs"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by lancest on 2007-09-10
Hi I want to get a script/commands to call up Mplayer and several .rmvb movies simultaneously from same directory.  People are usually impressed by this but using a mouse is so inefficient.

---

### Post by olejorgen on 2007-09-11
```
for F in *.rmvb; do mplayer $F; done
```
?

---

### Post by lancest on 2007-09-15
Thanks. Tried your script.  It works but only for 1 .rmvb file at a time with Mplayer.
(Multiple instances works using mouse though.)  But I would like to figure out a script to play all.  Any ideas?

---

### Post by olejorgen on 2007-09-15
```
for F in *.rmvb; do { mplayer "$F" & }; done
```
I thought this should've worked, but for some reason the mplayer processes are stopped (not terminated).
```
for F in *.rmvb; do gnome-open "$F" ; done
```
This works though. (If you set .rmvb to be opened with mplayer by default. To do this right click a .rmvb file -> properties -> open with)

---

### Post by lancest on 2007-09-15
for F in *.rmvb; do gnome-open "$F" ; done
This worked thanks! Opened all in Mplayer

 If i want to include *.avi what would I do?
Thanks, my scripting is not very good yet.

---

### Post by olejorgen on 2007-09-16
I'm not sure how to do that with "globbing". My best answer is to repeat the script with *.avi instead of *.rmvb

---

