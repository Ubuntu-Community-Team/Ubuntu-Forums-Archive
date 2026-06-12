---
title: "MP3 Help"
date: 2008-12-25
forum: Multimedia Software
---

### Post by inversionce on 2008-12-25
my sister got a Nexter MA 166 mp3 and it says for linux you just plug in and it works but i plug it in and nothing happens

---

### Post by pytheas22 on 2008-12-25
If you open Rhythmbox from the Applications>Sound and Video menu, do you see the mp3 player listed in the left pane?  If so can you add music to it that way?

If that doesn't work, please plug the adapter in, run these commands and post the output:
```

lsusb
ls -R /media
```

---

### Post by inversionce on 2008-12-25
/media:
cdrom  cdrom0  Expansion  floppy  floppy0

/media/cdrom0:

/media/Expansion:

/media/floppy0:



thats what came out

---

### Post by pytheas22 on 2008-12-25
It looks like the system is trying to do something with the device, assuming that that /media/Expansion directory is related to it.

Did you check in Rhythmbox to see if it's listed there?

Also, under the Places menu, do you see anything listed that looks like the mp3 player?

Finally, please plug the device in, run this command and post the output:
```

lsusb
```

---

### Post by inversionce on 2008-12-25
it worked thanks

---

