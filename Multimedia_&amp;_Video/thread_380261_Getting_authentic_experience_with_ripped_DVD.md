---
title: "Getting authentic experience with ripped DVD?"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by christian.convey on 2007-03-09
[I'm very inexperienced in the multi-media scene, so this may be a newbie question]

If one were to plunk a DVD into Kaffeine, it would work as expected: the DVD menus come up, clicking on them brings one to the right chapter, etc.

If one were to rip a DVD, would he need to do anything special to rip to hard-disk, and play back from hard-disk, so that during playback the DVD menus continued to work?

If it *is* possible to have working DVD menus when playing back from hard disk, can all of the standard DVD playback programs (Kaffeine, MPlayer, Xine, etc.) get it right?

Thanks,
Christian

---

### Post by x64Jimbo on 2007-03-09
If you rip it to an ISO file, you can mount that file as a virtual DVD drive, much like you can do with DaemonTools in windows.  
Search google for mounting an ISO in Linux.

---

### Post by panch0 on 2007-03-09
No need to create an ISO actually. Just put all the DVD files in a directory, say /home/dvd.

Then you can play it straight from the directory like this with MPlayer:

mplayer -dvd-device /home/dvd dvd://

---

### Post by x64Jimbo on 2007-03-11
ISOs are just easier to handle because they package a directory up into one file. Then you can also burn them with GnomeBaker or K3B

---

### Post by montgoss on 2007-03-11
k9copy works well for creating the iso.  And it's available as a package, so no need to compile anything.  Once you have the iso from k9copy, you'll have to "mount" it to use it.  The first time you mount an iso, you'll have to create a directory to mount to.  For example, "sudo mkdir /media/dvd_iso/".

Then whenever you want to use your iso, browse to that directory from the command line.  Then run ```
sudo mount YOUR_MOVIE.ISO /media/dvd_iso -t iso9660 -o loop
```Now use whatever program to open a DVD with the path of /media/dvd_iso.

---

