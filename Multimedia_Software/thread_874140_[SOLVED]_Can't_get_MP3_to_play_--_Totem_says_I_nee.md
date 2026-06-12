---
title: "[SOLVED] Can't get MP3 to play -- Totem says I need x-ms-asf plugin??"
date: 2008-07-29
forum: Multimedia Software
---

### Post by tuebinger on 2008-07-29
Hello!  I've been trying to get this mp3 file to work that a friend (who has a mac) can't get to play on his computer.  When I double-click on it it opens up the Totem player, then I get a dialog that says it cannot play and needs an 'x-ms-asf' plugin.  

 I've installed the medibuntu respository, the nonfreecodecs, and ubuntu restricted extras but it still won't play. I thought it might be a corrupted file (my friend downloaded it from limewire), but thought I'd check this forum for help before I tell him it's a lost cause. Any ideas?  

Any help would be much appreciated.  Thanks!

---

### Post by kostkon on 2008-07-31
Did you install the *w32codecs* package? If not, install it. Also make sure that *gstreamer0.10-pitfdll* is installed.

Although, it seems to me that it is corrupted.

---

### Post by Tsarj on 2008-07-31
```
sudo apt-get gstreamer0.10-plugins-ugly
```
That's what I use for my mp3 codec.

---

### Post by tuebinger on 2008-08-01
> **kostkon said:**
> Did you install the *w32codecs* package? If not, install it. Also make sure that *gstreamer0.10-pitfdll* is installed.

Although, it seems to me that it is corrupted.

I have the w32codecs package installed but could not find gstreamer0.10-pitfdll.  Do I have to add a respository for that?

I also have the gstreamer0.10-plugins-ugly packagae installed.

I even tried opening this file with Windows.  Windows came back with the message that the .mp3 extension didn't match the file type, and asked if I really wanted to open it.   It got a severe threat warning, so I didn't.  I think it's safe to say it's corrupted!

Thanks so much for trying to help, anyway!

---

