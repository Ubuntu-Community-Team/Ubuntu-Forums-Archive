---
title: "Amarok fail - installed with MySQL and MTP support"
date: 2008-06-18
forum: Multimedia Software
---

### Post by thedaylights on 2008-06-18
I recently installed Amarok with MySQL database and MTP support for Creative Zen mp3 players. Now Amarok behaves strangely. For instance, it loads up with the playlist tab open, I then click on the collection tab. At this point Amarok darkens as though the application is processing and stays dark. It does not open the collection tab or allow me to play music.

The next day I noticed that songs were missing from my collection even though I had completely scanned the folders with my music. So I started to rescan - however after about 30 minutes of scanning I wanted to turn off my computer so I clicked cancel all background processes. It would not shut down the scan, and I had to terminate the application with system monitor. Then I could not shut down ubuntu and I had to hard power off my system.

Is this an artifact of interrupting the scan? Or is there maybe a problem with my install of MySQL? My install was aborted twice because of missing dependencies, which I then downloaded and installed. I finally used this list of amarok dependencies:
[http://amarok.kde.org/wiki/Requirements](http://amarok.kde.org/wiki/Requirements)
as well as
[http://freshmeat.net/depends/download-all/42210/](http://freshmeat.net/depends/download-all/42210/)
plus one other that was on an official ubuntu page - can't find it at the moment.

Additional note: my music collection is on an external hard drive, the FreeAgent 500GB. This hard drive has a habit of powering down when idle and it unmounts from the file system when it does so. I noticed that just now after restarting Amarok, my external drive had unmounted and the collection was empty. When I mounted it and restarted Amarok, Amarok had to "build collection". After building it still would not play a song and required a system monitor shutdown.

---

### Post by thedaylights on 2008-06-24
I am going to try to uninstall and then reinstall amarok in a straightforward manner. I do not know how to uninstall amarok since it does not show up in add/remove programs.

Any help please?

---

