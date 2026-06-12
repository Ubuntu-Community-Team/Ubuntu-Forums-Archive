---
title: "Rhythmbox Album Art"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by nikRbokR on 2008-04-10
I can't figure out how to get album art to show up for my songs in Rhythmbox.  I have the plug-in checked but no album art shows up.

To test out a manual addition of cover art, I decided to do a John Mayer song from Continuum.  I found the cover art and saved it like this:
```
~/.gnome2/rhythmbox/covers/Continuum.jpg
```

However, this still doesn't work.  I wish it allowed for drag and drop like iTunes (which I personally don't like very much) but I still don't understand why it is not getting any covers from the internet.

---

### Post by kostkon on 2008-04-10
> **nikRbokR said:**
> I can't figure out how to get album art to show up for my songs in Rhythmbox.  I have the plug-in checked but no album art shows up.

To test out a manual addition of cover art, I decided to do a John Mayer song from Continuum.  I found the cover art and saved it like this:
```
~/.gnome2/rhythmbox/covers/Continuum.jpg
```

However, this still doesn't work.  I wish it allowed for drag and drop like iTunes (which I personally don't like very much) but I still don't understand why it is not getting any covers from the internet.

If you want to manually add cover art for an album, then just save the cover art image inside the folder of this album as a variation of filename *cover*, *album*, *albumart*, *folder*; e.g. as *cover.jpg*, *album.png*, etc.
Also you can name the cover art image as *.folder* if you want to make it invisible.

The folder you found, i.e.
```
~/.gnome2/rhythmbox/covers/
```
is the place where *Rhythmbox* saves the cover art images, that it downloads from the internet, when there is not a cover art image inside the album folder.

---

