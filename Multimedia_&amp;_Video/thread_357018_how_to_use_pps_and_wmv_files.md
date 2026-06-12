---
title: "how to use pps and wmv files"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by lanchongzi on 2007-02-09
i downloaded some . pps and wmv files

is there an application to use these files?

---

### Post by squirrel_f13 on 2007-02-09
Dunno about .pps - not sure what kind of file that is. WMV's (Windows Media Video) can be played by most media players (Totem-Xine, VLC) but requires the installation of codecs that allow that. Check out your 'Applications-->Add/Remove' menu option for basics (search for video or codec) or do a search on VLC/Xine for more info.

---

### Post by RomeReactor on 2007-02-09
Hi. You can use your power point files with Open Office Presentation, and installing w32codecs will let you view windows media video files. Do you have the PLF repositories? If you don't know, or don't have them, and If you're using Edgy, open a terminal and write

```
gksudo gedit /etc/apt/sources.list
```

and look for an entry that reads

```
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

If it's not there, add it at the end of the file. Save and close. Then, still on the terminal, write

```
sudo apt-get update
```

and when that finishes, open Synaptic and search for **w32codecs**. I also suggest you install **mplayer**.

---

### Post by lanchongzi on 2007-02-10
hi thanks for that.

only problem is that i dont have open office ( I use Xubuntu )
but since I am completly new and dont know which disrto is good and which not I will download Ubuntu And install it over my Xubuntu.
I also heard it should be easier to use for people like me.
I am just gona try it.
and after installing Ubuntu I will follow your advise.
then I will let you know how it went.


thanks  Johannes

---

