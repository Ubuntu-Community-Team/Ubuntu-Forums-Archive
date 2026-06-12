---
title: "Can't play avi files?"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by eeefresh on 2008-03-26
I have been backing up my DVD collection to Xvid avi files using AcidRip, but I sat down tonight to actually watch one and got this error:

[I]The filename "The Italian Job.AVI" indicates that this file is of type "avi document". The contents of the file indicate that the file is of type "AVI video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "AVI video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. [/I]

I am getting this error for all of the files I have ripped so far.  I have restricted drivers installed and have VLC set as the default player.  If I just click an avi file it gives me this error, but if I right click and say "open with VLC," it will play fine.  Any ideas?

---

### Post by Pgi947 on 2008-03-27
Perhaps try what it says, rename the file extension to .avi if its not already?

Is the file assosiated with VLC?

---

### Post by TenPlus1 on 2008-03-27
Once I installed all of the gstreamer codecs my .avi and othe rmovies opened 1st time...  Do you have all the codecs installed ?

---

### Post by eeefresh on 2008-03-27
I tried switching the extensions between upper- and lower-case letters, but that didn't help.

I am pretty sure I have the right codecs installed.  I ran 

```
sudo aptitude update && sudo aptitude install ubuntu-restricted-extras
```

When that didn't solve the problem, I went in and installed all the restricted stuff via Automatix, but that didn't solve it either.

---

### Post by eeefresh on 2008-03-27
I just did a search in synaptic, and yes, gstreamer plugins are installed.

---

### Post by eeefresh on 2008-03-27
Okay, I think I just fixed it, but man is this weird...

The files I ripped all had "avi" extensions...lowercase.  I changed them to uppercase, and that didn't work either.  However, when I now change them BACK to lowercase avi, they are opening fine!

Very strange....oh, well. I guess its working as long as I don't mind some renaming.

---

### Post by eeefresh on 2008-03-27
...and I rebooted, and it no longer works.  Damn it!

---

### Post by Prefix100 on 2008-03-27
right click the file > open in vlc

---

### Post by eeefresh on 2008-03-28
That's exactly what I am doing, and they open fine that way.  I just can't figure out why they don't open when I left-click them.  I have gone into the properties for the files and set them to open with VLC, but they will only do so if I right-click and say "open with."

---

