---
title: "Amarok locks up"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by skydiver|goose on 2008-02-06
I downloaded Amarok since I backed up all the files from my ipod to my hard drive to transfer my music over to my laptop and I needed a program that would automatically sort through it all and get the filenames right since Rythembox wouldn't. Amarok figured out the file names, but every time I try and play any of them it freezes  up at "Building Playlist". I let it run a couple of minutes and then give up and X out it. After I close out, it won't reopen unless I reboot the laptop.

Anyone got an idea?

---

### Post by millenniumtree on 2008-05-23
killall amarok
killall amarokapp

Then you should be able to fire it up again.

If that won't quite do it, throw a -9 before the process name like this.

killall -9 amarok
killall -9 amarokapp

For very badly behaved programs, I throw these into a bash script and toss a launcher in the panel :P  Just don't click it accidentally!  I live just a little bit dangerously.

---

### Post by RemoteUser on 2008-07-10
Amarok locks my computer up completely.  I'll continue to use my Windows computer for listening to music, I guess.  This is pretty shameful at this point.  People have been reporting this for years.

---

