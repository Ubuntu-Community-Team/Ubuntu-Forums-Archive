---
title: "Music from Windows in Linux"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by stickperson on 2007-05-23
Hey, I'm running Feisty Fawn and want to play my music that I have on my Windows partition in Linux.  It's in the My Documents/My Music/Itunes Music folder.  For some reason some artists show up but not all of them.  Any clue why?  And I dont have to copy all of them to my linux partition do  I?  Thanks

---

### Post by wolfen69 on 2007-05-23
i could be wrong, but it may be that some songs are in AAC format. without the proper codecs in linux, they might not show up.

---

### Post by cyrusrayne on 2007-05-24
> **stickperson said:**
> Hey, I'm running Feisty Fawn and want to play my music that I have on my Windows partition in Linux.  It's in the My Documents/My Music/Itunes Music folder.  For some reason some artists show up but not all of them.  Any clue why?  And I dont have to copy all of them to my linux partition do  I?  Thanks

Theoretically you don't have to move them to your linux partition.  The path you would take would probably be like /media/sda1/documents and settings/username/my documents/my music/itunes music.  I'm about 99.9% sure that should work for you.  You should be able to add references to the music to Rhythmbox or whatever media player you're using on your Linux partition.

Enjoy your tunes :)

---

### Post by stickperson on 2007-05-24
Hm.  When I'm in the home folder there is the music folder which I already talked about.  Then when I go into the File System thing there is a /media but after that only /cdrom, nothing else.

---

### Post by Emerzen on 2007-05-24
Is your Windows partition mounted?  What's the path to it?

---

### Post by onbongos on 2007-05-24
are you sure all the songs are in that folder? itunes will let you add things to your library from another folder and it will stay there until you do a consolidate library

---

### Post by stickperson on 2007-05-24
Um, I think it's mounted, not really sure though.  Like when I go to Computer there is the home folder, desktop, file system, and ibm preload (thats what all my windows stuff is on).  But ibm preload or whatever doesn't show up in the music thing.

---

### Post by Emerzen on 2007-05-24
Go to your ibm preload folder, right-click it, and see if there is an option to mount it (if so, it's not mounted)/ if the option is to unmount it, then it's already mounted.

After your sure it's mounted, right-click it again and go open up the properties-->permissions.  Do you own it?  If not do other users have read/write permissions?  I suggest the following

```
gksudo nautilus
```

This will open up nautilus in root mode so you can change the permissions.  I recommend added it to the "users" group so that you can read/write to it or just making yourself the owner.  Once you're sure it's mounted and you have the proper permissions set, let me know how it turns out.

---

