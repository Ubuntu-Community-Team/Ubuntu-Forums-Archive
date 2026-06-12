---
title: "No video in Myth?"
date: 2007-11-23
forum: Mythbuntu
---

### Post by couzin2000 on 2007-11-23
Although this is weird, I'm getting no video whatsoever to playback on Myth. I don't have cable input to my pc, but I use it to playback videos I've downloaded. 
I've managed to install MythTV properly, so naturally I'm trying out everything I can. However, now video playback. I get audio just fine, I get all the Myth frontend behaving correctly right until I hit **play**. Then the screen stays as is. I can continue working in Myth, but I get no video playback.  I get pics, news, all kinds of stuff - but no video.

I checked the command inside the Setup - it's linked to Mplayer. I haven't had much experience with it, but I hear it's all all it's cracked up to be. Maybe a different command, or different app would work better? VLC?

---

### Post by only1platinum on 2007-11-24
Not trying to hijack the post. But I am having the same problem if anyone comes up with any suggestions I would greatly appreciate it. When I exit back out of myth TV the videos play just fine thru any of the media players installed. It just won't play thru the MythTV engine. I am pretty new to linux as well so please talk down to me. :-) I am running Mythbutu 7.10.

---

### Post by lordkalkin on 2007-12-18
I'm having the exact same problem as well.  Everything seems to work fine, and if I exit the mythtv frontend, I can play videos fine, just not within the frontend.  Any ideas on how to fix this?

---

### Post by couzin2000 on 2007-12-19
ANYONE? (This is hard for me, it's the 3rd time I open a thread and no one answers. Is there a dedicated forum for this? please help!)

---

### Post by couzin2000 on 2008-01-02
Again, I'm still waiting for some help. I've tried alternatives, but nothing has worked. Until someone replies to my original post, I can't do anything - can't watch video from Myth.. please help.

---

### Post by lordkalkin on 2008-01-13
Following a link from another thread, I found something that worked.  Basically, all I had to do was go into Video Settings -> File types, uncheck the option to use the default player for everything other than .iso files, and tell it to use this line:

```
 xine -pfhq --no-splash
```

After that, I can play everything right from MythTV.  The link below is more information about Xine configuration in MythTV.

[http://www.mythtv.org/wiki/index.php/MythVideo#Xine_Configuration]("http://www.mythtv.org/wiki/index.php/MythVideo#Xine_Configuration")

---

### Post by couzin2000 on 2008-02-23
For now, I've given up on Myth. I did want to have some sort of HTPC, but Myth doesn't work properly, and I am getting very little help so far. Since I cannot fix the system myself, I'm uninstalling the whole thing. I'll probably come back to it later... maybe in Hardy Heron. Thanks to all who've helped!

---

