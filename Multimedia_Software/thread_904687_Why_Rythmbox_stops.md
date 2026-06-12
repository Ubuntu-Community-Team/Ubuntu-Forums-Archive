---
title: "Why Rythmbox stops?"
date: 2008-08-29
forum: Multimedia Software
---

### Post by baronferg on 2008-08-29
G'Day All,

Greetings and best wishes. I am pretty sure that what's happening is not normal.......I launch Rythmbox, select all 1200 songs, select repeat, select shuffle and click Play. It plays fine but, after some time, maybe 15 minutes, the music stops and Rythmbox closes.

Any ideas, please.

Thanks

---

### Post by Crafty Kisses on 2008-08-29
Try running Rhythmbox in Terminal and see if you get any erros.

---

### Post by baronferg on 2008-08-30
Thanks for the reply.
I am not familiar with running Rythmbox in terminal.
Can you please point me in the right direction on how to get this done.

Thanks

---

### Post by huwnet on 2008-08-30
Just open a terminal, type rhythmbox and hit enter :). Rhythmbox will open as normal but any errors will appear in the terminal and you can then copy and paste them here

---

### Post by baronferg on 2008-08-31
Thanks for your help.

noname@noname-desktop:~$ rhythmbox
libpng error: IDAT: CRC error
libpng error: IDAT: CRC error
libpng error: invalid stored block lengths

---

### Post by kostkon on 2008-08-31
> **baronferg said:**
> Thanks for your help.

noname@noname-desktop:~$ rhythmbox
libpng error: IDAT: CRC error
libpng error: IDAT: CRC error
libpng error: invalid stored block lengths
Hmmm, it seems like it fails to load a album cover image for the song you are playing.

Do you use your own album cover images? If not, check the contents of this folder
```
/home/yourusername/.gnome2/rhythmbox/covers
```
To access this open, go to your home folder using the file browser, then select *View -> Show Hidden Files* and you'll see the hidden *.gnome2* folder.

You can try to delete any cover images that you'll find inside the *covers* folder. *Rhythmbox* puts in this folder the cover images that downloads from Amazon.

---

### Post by baronferg on 2008-08-31
Great!! Thanks very much. Took care of that.

My next and final little mission is to set up this music box to automatically logon and launch Rythybox, select all music and start playing whenever it is powered on or rebooted.

I am still searching into it but, if you happen to know how to accomplish this, any help would be much appreciated.

Thanks and best wishes and cheers.

Ferg

---

