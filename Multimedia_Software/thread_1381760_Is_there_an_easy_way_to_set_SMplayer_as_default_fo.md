---
title: "Is there an easy way to set SMplayer as default for filetypes?"
date: 2010-01-15
forum: Multimedia Software
---

### Post by helamsirrine on 2010-01-15
I am running Kamic 64 Right now I can 'open with' any files into SMplayer from the context menu and I already have dvds set to always open in SMp. I would like to make SMplayer my default player for most video filetypes so that a simple double-click will open SMp and not totem. 

Is there an easy way to do this without editing '/etc/gnome/defaults.list' for each file type individually? If not, will replacing 'totem.desktop' with 'smplayer.desktop' for all video filetypes achieve the desired result? :-k

Thanks.

---

### Post by Linuxforall on 2010-01-15
Right click on the file and in open with tab select smplayer and it will remember in future for files with that particular extension.

---

### Post by helamsirrine on 2010-01-15
:roll:umm... no. It won't. 
Right now all video filetypes on my system, when double-clcked open in totem, but can be opened in SMp from the context menu. I would like the opposite to be true. 

Sorry for repeating myself.

---

### Post by chewearn on 2010-01-15
Right-click on the file.
Select "Properties".
Select "Open With" tab.
Choose "SMPlayer".
Repeat for each file type.

---

### Post by helamsirrine on 2010-01-15
D'oh!#-o 

Gee, I feel kind of silly now. I probably should have posted this query in the n00b forum.:lol:

Anyway, Thanks.

---

### Post by Guyllfyre on 2011-02-06
> **chewearn said:**
> Right-click on the file.
Select "Properties".
Select "Open With" tab.
Choose "SMPlayer".
Repeat for each file type.

This is not working for me.
My system keeps defaulting back to mplayer.
Preferred applications shows "Custom" and doesn't give the option of smplayer.

Any ideas here?

---

### Post by no2498 on 2011-02-06
do you have smplayer installed yet
type it in a terminal click enter it tells you how to install it

---

### Post by Guyllfyre on 2011-02-06
Yes, I have the newest smplayer installed since it solves a lot of wmv playback issues and so far has produced a better quality video playback with many files.

It just seems to keep going back to mplayer every time I do that process.

I've tried setting it from both the properties page and the play with and setting it to the preferred app.

I'm running Ubuntu Studio 10.04 x64.

---

### Post by Guyllfyre on 2011-02-09
Well, looks like doing this enough times has done the job.  It just seemed like there should have been an easier way.

Nearly every retarded Windows media player has a way of making it take over the defaults, would be nice if it could happen with Linux media players also.

---

### Post by meduser on 2012-03-11
I am trying to do the same thing. I have over 1000 songs on my pc, and there has to be a way to get the default player set for all files under that extension, instead of doing it file by file.

---

