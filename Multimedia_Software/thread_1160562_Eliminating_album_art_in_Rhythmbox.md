---
title: "Eliminating album art in Rhythmbox?"
date: 2009-05-15
forum: Multimedia Software
---

### Post by chellrose on 2009-05-15
I just brought a bunch of my music files from WinXP over to Ubuntu 9.04.  In Windows, I was *very* careful not to allow WMP to download any album art, and I know that there was none associated with any of my music.

However, in Rhythmbox I am seeing album art.  Is there any way to get rid of it?  I don't simply want to suppress the display; I want to eliminate the files from my computer.  I don't have a need for the album art, and those pictures take up a lot of disk space. :)

I did search the forum for this, but couldn't find anything.

Thanks! :D

---

### Post by ShadowTek on 2009-05-15
I just started using Rhythmbox, and I have noticed that it will use image files that are in the same directory as the music files, or it will retrieve cover art from the Internet. I'm not sure exactly what algorithm it's using to decide which one to use over the other, but you should be able to disable its downloading of cover art from the net in **Edit > Plugins > Cover Art**.

---

### Post by kostkon on 2009-05-15
Yes you can just disable it, it's a plugin, actually.

Thus, open *Rhythmbox*, go to *Edit &#8594; Plugins* and then just disable the *Cover Art* plugin.

To get rid of the covers that *Rhythmbox* has already downloaded, go to your home, select *View &#8594; Show Hidden Files* in the *Nautilus* menu and then go to this folder
```
.gnome2/rhythmbox/covers
```
and delete everything in there.

Hope that helps.

---

### Post by chellrose on 2009-05-15
Thank you; that seems to have worked.


In case it helps anyone else... I didn't have that folder you mentioned, but I found some downloaded covers in here:

```
~/.cache/rhythmbox/covers/
```

---

