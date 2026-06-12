---
title: "Mounting ISOs of DVDs"
date: 2012-10-08
forum: Multimedia Software
---

### Post by phoenix32 on 2012-10-08
I've been ripping my DVDs to have my multimedia library on my laptop for when I travel.  I used Brasero to take the images as ISOs.  I can mount them, but they will not play in the movie player or vlc.

Any thoughts or assistance is greatly appreciated.  Thanks!

---

### Post by mc4man on 2012-10-08
No need to mount, just play in vlc or totem
A dvd .iso is just a file, either r. click on the .iso > open with, ect. or open from the player
(Media > open file, browse to in vlc, Movie > open, browse to in Totem

---

### Post by phoenix32 on 2012-10-08
I tried that... It crashed both movie player and vlc.  That's why I thought I needed to mount the ISO.

In that case, do you have suggestions as to why the media players are crashing?

---

### Post by mc4man on 2012-10-08
Try opening vlc from a terminal, then play the .iso, see what it says.
a command of just vlc should be ok, if more info is needed use 
vlc -vv

(if the dvd has structure protection it's possible brasero created an unusable iso

---

### Post by evilsoup on 2012-10-09
If you're mounting by right-clicking the file and selecting 'archive mounter', then I've found that you won't be able to play them as DVDs.

VLC should be able to play it, as mc4man wrote.


Alternatively, in terminal, you can

```
sudo mkdir /media/fakedvd

sudo mount -o loop path/to/movie.iso /media/fakedvd
```

(You only need to create the directory once)

Ubuntu should then act as if you have inserted a DVD, you'll get the prompt of what to do. It treats it entirely as a DVD, including preserving the DRM, so you'll need the DVD decoding stuff <--this is probably why you can't play the ISOs straight in VLC etc.

---

