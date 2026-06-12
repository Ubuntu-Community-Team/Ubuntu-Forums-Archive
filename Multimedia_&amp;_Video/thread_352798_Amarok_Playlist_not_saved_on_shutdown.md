---
title: "Amarok Playlist not saved on shutdown"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by chriscando on 2007-02-03
Hello, I am using Amarok 1.4.3 under Gnome. My problem is that Amarok always starts with an empty playlist, clearing my previous one from last use. 

I have set the 'Remember current playlist on exit' option but it has no effect. Also, I have used this feature just fine under KDE.

I really like Amarok, just wish it could keep a persistent playlist for me. Any ideas how I might fix this?

Thanks

---

### Post by MGStreak on 2007-09-14
Although I know this information will not solve the problem, perhaps it will ease your mind to know that I suffer the same problem, and I have discovered that the root of the issue is that upon shutting down, any programs which take 'too long' according to the system get shut down via a 'kill' command.  Basically what happens is that Amarok is taking too long to save its playlist, and the system just sends it a 'kill' command, ending the program before it finishes saving... so the next time you start Amarok, the last *saved* playlist is what will come up.

---

### Post by scabies on 2008-03-12
Is there any solution for this yet?  I still get the problem with having to click 'all collection' under smart playlists each time I start my workstation in the morning.

Even if I close amarok a few minutes before shutting down, at the next boot I don't have anything in my playlist when amarok starts again.  But if I shut it down and open it up again without rebooting, the files will be there, and the last song played is selected in the playlist.

I'm running 1.5.8 from the Hardy repos.

Thanks!
Mike

---

### Post by scabies on 2008-04-24
My mistake in the last post--I'm running 1.4.9.1 from the Hardy repos, not 1.5.8.

I've cleared out the amarok files from ~/.kde/share/apps/amarok, dropped and recreated the amarok database. Still a blank playlist every morning...what other possible approaches are there?  

Thanks!

---

