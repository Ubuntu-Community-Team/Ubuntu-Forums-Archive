---
title: "mp3 issues"
date: 2008-08-20
forum: Multimedia Software
---

### Post by jarome on 2008-08-20
Only some will play in Banshee. None play in Rhythmbox. They do play in gxine and VLC. Amarok flashes up the start screen and disappears.

How do I get my music going in 8.04? I have an HP mini-note.

Thanks,
Jim

---

### Post by erginemr on 2008-08-20
> **jarome said:**
> Only some will play in Banshee. None play in Rhythmbox. They do play in gxine and VLC. Amarok flashes up the start screen and disappears.

How do I get my music going in 8.04? I have an HP mini-note.

Thanks,
Jim

Try to play an mp3 song in Totem. When you do that, Synaptic should interfere and install the necessary gstreamer packages to play mp3's.

---

### Post by cpetercarter on 2008-08-20
You may not have all the appropriate codecs installed. Do this:

First, System > Administration > Software Sources > click "software restricted by copyright or legal issues (multiverse)"

When prompted, click to update.

Then, System > Administration > Synaptic Package Manager > search for Ubuntu-restricted-extras, click to install, then click "apply"

However, if any of your music tracks are DRM protected files (eg songs downloaded from iTunes music store), there is - alas - no way of playing them in Linux. You either need to keep Windows going to play these tracks in iTunes, or use Windows to download and run a programme to convert the DRM protected files to a playable format like mp3.

---

### Post by jarome on 2008-08-20
I do not do any DRM files because their quality is too low. I rip my own extensive CD collection (300 GB now), so that is not the issue.

Installing the extras did nothing about amarok.

RhythmBox still puts a red icon next to the tracks when I try to play them. Gnome Mplayer refuses to play them. Banshee just scrolls through my tracks without playing them!

What now?

---

### Post by erginemr on 2008-08-20
And did you try opening them in Totem?

---

### Post by jarome on 2008-08-20
> **erginemr said:**
> And did you try opening them in Totem?
Totem is not listed in the Applications menu. Ubuntu (as opposed to SUSE) seems really bad at adding newly-installed apps to this menu. How do I do this?

So, Totem works. But I listen to classical music and always want to hear whole albums without making a playlist. Totem and Banshee require selecting the individual tracks. Amarok organized by album. That's why I really want Amarok to work.

---

### Post by erginemr on 2008-08-20
For one thing, that means the required gstreamer codecs have been installed, and you should look elsewhere. It is still a mystery why Rhythmbox, which also uses gstreamer codecs, cannot play them.

Can you try to start amarok from the terminal and then open up an mp3 file from it? It will crash as before, but the terminal window should at least give you a hint on why it crashes.

---

### Post by jarome on 2008-08-20
jar@jarhp:~$ amarok
trying to create local folder /home/jar/.kde/share: Permission denied
trying to create local folder /home/jar/.kde/share: Permission denied
trying to create local folder /home/jar/.kde/share: Permission denied
trying to create local folder /home/jar/.kde/share: Permission denied
trying to create local folder /home/jar/.kde/share: Permission denied
trying to create local folder /home/jar/.kde/share: Permission denied
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

I fixed the permission problem. I have libgl-mesa installed, but cannot find libGL in the synaptic manager.

---

### Post by erginemr on 2008-08-20
I guess it is somewhat related to the graphics driver, because when I issue the following command:
```
ls -l /usr/lib/libGL.so.1
```
I get:
```
lrwxrwxrwx 1 root root 17 2008-07-14 23:11 /usr/lib/libGL.so.1 -> libGL.so.96.43.05
```
where 96.43.05 is the version number of my NVidia graphics driver (nvidia-glx). 

So, you should first check if there really is a libGL..blah blah file in /usr/lib:
```
ls /usr/lib/libGL.so*
```

---

### Post by erginemr on 2008-08-20
OK. Here is another thread with the same problem and a solution proposal:
[http://ubuntuforums.org/showthread.php?t=648512](http://ubuntuforums.org/showthread.php?t=648512)

---

### Post by jarome on 2008-08-20
That solved it. I had a different libgl-mesa installed, which this uninstalled. But the synaptics package manager is falling down on the job. It sees to play also :-)

Thank you.

---

### Post by erginemr on 2008-08-20
Great news! Have fun with your music collection! :) (I'm also a fan of classical music, esp. Mozart & Tchaikovsky)

---

