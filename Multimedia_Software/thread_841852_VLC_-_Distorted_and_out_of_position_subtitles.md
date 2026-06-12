---
title: "VLC - Distorted and out of position subtitles"
date: 2008-06-26
forum: Multimedia Software
---

### Post by Reaper14 on 2008-06-26
[http://img293.imageshack.us/my.php?image=capturaecrabg3.jpg]("http://img293.imageshack.us/my.php?image=capturaecrabg3.jpg")
It's like that on all movies that I try to see.
Any way to fix it?

---

### Post by ajmorris on 2008-06-26
Hi there,
Have you had a look through the subtitles options in the VLC options? Perhaps you can change something there...  Also, if you maximised the video, do the subtitles appear like that when displayed on the normal aspect ratio, before maximising?


AJ

---

### Post by Reaper14 on 2008-06-26
Thanks for answering.

I've looked in the VLC subtitle options, but i'm not sure what settings to modify. I have also tried to change the subtitles font, but it didn't change anything.

And yes, the subtitles look like that before maximizing and even in fullscreen.

---

### Post by Reaper14 on 2008-06-27
Don't let this thread get buried.
Help me.

---

### Post by mc4man on 2008-06-27
You really can't 'change' anything about subs from dvds in vlc (or probably any of the other players)
Quote from videolan
> DVD and SVCD subtitles are merely images, so you won't be able to change anything for them. OGM and Matroska subtitles are rendered text, so you will be able to change several options.
Considering that's a standard studio release (shawshank redemption) the subs should be ok.
Maybe try going to home dir. and deleting .vlc   then try again. 
Have you tried any other players? - totem-xine, mplayer (from gui) ect.
While i don't think it should matter install this and see
```
sudo apt-get install ubuntu-restricted-extras
```
If you install above make sure you have medibuntu enabled as software source
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Reaper14 on 2008-06-28
Thanks mc4man. Deleting the .vlc folder has solved my problem.

---

### Post by Kudaku Tama on 2008-10-25
Exactly where is the home directory and the.vlc file? I'm having the same problem.

Edit: Never mind, sorry, tenth version of vlc downloaded fixed it. Thanks, anyway.

---

