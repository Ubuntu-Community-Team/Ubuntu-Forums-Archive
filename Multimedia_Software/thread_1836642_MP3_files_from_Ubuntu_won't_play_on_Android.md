---
title: "MP3 files from Ubuntu won't play on Android"
date: 2011-08-31
forum: Multimedia Software
---

### Post by slowtrain on 2011-08-31
I am trying to digitize my CD collection.  So, I used Soundjuicer to extract MP3s from a couple test albums, used USB to transfer them to my Droid phone (put them under an 'audio' directory I created, with subdirectories by artist and album), and tried running from the standard Music app.  I can see the music and select it, but when I try to run a tune, it comes through in short, almost indistinguishable bursts while the application locks up (have to force shutdown).  The music plays fine in Ubuntu.

Any ideas about what might be causing this?  The MP3 converter I used is 'lame'.  Is there some incompatibility?

---

### Post by slowtrain on 2011-09-01
Okey doke, so I tried running the Ubuntu-created MP3's on my wife's identical phone--they worked fine, as did ogg files.  Which then set me to looking for something on my phone that could explain the problem.  I installed a process and memory watcher.  It wasn't very clear from that what was going on, but it was clear that when I turned the player on 70-80% of my processor was used up and that applications such as last.fm and go.weather were chewing up processor time, only a few percent according to the process watcher, but I tried shutting them down.  They would restart themselves.  So, I uninstalled them and, lo, I can now listen to music on my Android.  I'm still a bit baffled as to why the music app would lock up (play music in short bursts ever 30 seconds and be unresponsive) though the phone was not locked up (could go to home and work on other apps) even though 20-30% of the processing power was still available.  

I hope this helps someone!

---

