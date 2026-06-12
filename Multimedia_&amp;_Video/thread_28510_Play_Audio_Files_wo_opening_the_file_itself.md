---
title: "Play Audio Files w/o opening the file itself"
date: 2005-04-20
forum: Multimedia &amp; Video
---

### Post by afonit on 2005-04-20
This one I discovered by accident.

to play an audio file (to just hear what it has in it) merely hover your mouse over it, and it will start to play.  (to this point I only have .wav files to work like this and I had to have the file on the desktop)  But this is very handy for the environment I am in now.

---

### Post by TravisNewman on 2005-04-21
There's some package you have to have installed for this to work. I can't for the life of me remember which it is. sox maybe?

But yes, I love this feature.

---

### Post by graigsmith on 2005-04-22
i wish i knew how to turn this off.  i find it annoying, it took me forever to figure out what was causing sounds to play.

---

### Post by Nis on 2005-04-22
[QUOTE=graigsmith]i wish i knew how to turn this off.  i find it annoying, it took me forever to figure out what was causing sounds to play.[/QUOTE]
 In System/Preferences/File Management select the Preview tab and set Preview Sound files to Never.

By the way, this only works if you have sox installed (like pthumb said) and if the file is wav or mp3.  ogg and flac do not trigger this.  A zombie nautilus property shows up in System Monitor but nothing plays.

---

### Post by froguz on 2005-06-16
[QUOTE=panickedthumb]There's some package you have to have installed for this to work. I can't for the life of me remember which it is. sox maybe?

But yes, I love this feature.[/QUOTE]

i get this working by installing [COLOR=DarkOrange]mpg123-esd[/COLOR] (mpg123 without esd support didn't work), i think sox is necessary too, but it comes allready installed in ubuntu 5.04   :-)

---

### Post by dommyOZ on 2007-04-27
I've just installed Fiesty Fawn 7.04 and to get preview working for ogg, mp3 and wav I've had to add vorbis-tools , mpg123 and sox in that order but I still can't get flac to preview and its the only one left

Any one know how I can do this??

---

### Post by mahiyar on 2007-04-28
Thanks Dommy that was a nifty feature which I was missing in feisty

---

### Post by phenest on 2007-04-29
This only seems to work for icon view. If your files are in list view, there is no preview.

---

### Post by phenest on 2007-04-29
I've just being playing around with Beryl. Neat. Too much for me though, so I have gone back to the built-in Desktop Effects (compiz) in Fiesty. No, this isn't off-topic. Now, none of my music files preview in nautilus. Re-installed: sox, mpg123, and vorbis-tools. Now, only ogg files preview. Installed mpg123-alsa. Now mp3 files preview. but I still can't get wave files to preview.

Any ideas anyone?

---

### Post by mahiyar on 2007-04-30
You need to install sox support as in dommyOz's mail to play wav file.

---

