---
title: "Gutsy Totem DVD bug"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by waldrepdebater on 2007-11-14
I'm trying to play some DVD's on Gutsy using totem.  At first I tried to play them and it would just play the little 50 sec intro clip over and over and would never get to the menu.  I then ran these two commands according to an online guide to fix totem's DVD playing:

```
sudo apt-get install libdvdread3 totem-xine libxine1-ffmpeg
sudo /usr/share/doc/libdvdread3/install-css.sh
```

The DVD will now play fine...except for the video.  I am a getting most of the image obscured by a strange blue polygon that moves based on the movement of other windows/menus.  Here is a screenshot:

[img]http://img217.imageshack.us/img217/7958/screenshotdvdmenupz7.png[/img]

In the screenshot the whole image is blue, but normally I can see the upper left hand corner of the image playing normally, cut off from the rest by a jagged blue edge.  What is wrong and how can I fix it?  I really don't want to have to go back to vista to play DVDs

System info:
Ubuntu 7.10 dual-booting with Windows Vista on an Acer Aspire 5610Z laptop.  Intel dual-core processor, 1g RAM.

---

### Post by waldrepdebater on 2007-11-14
A quick bump for the graveyard shift.

---

### Post by wolfen69 on 2007-11-15
i would try
```
sudo apt-get purge totem
```
then
```
sudo apt-get install totem
```
then go here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) for the DVD codecs.
it's worth a try.

---

### Post by waldrepdebater on 2007-11-15
Sorry, its still having the same problem.

---

### Post by waldrepdebater on 2007-11-15
Um, is there any way to play DVDs on Ubuntu 7.10?  I would be happy to download another player, I don't really like totem anyway.

---

### Post by diebels on 2007-11-15
vlc is very good at playing dvd's. smplayer is the best all round player if you don't care about the dvd menus

---

### Post by mdpalow on 2007-11-19
Click the link in my Signature and read my first message about uBackup! It's a script I wrote that now includes an automatic install of all necessary DVD and Codecs files to make your DVD work.

Download uBackup! at the bottom of my post and then use option 15 to automatically do everything for you and it'll work.

---

### Post by waldrepdebater on 2007-11-20
VLC works!  It plays!  Thank you all for your help!

---

