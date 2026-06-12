---
title: "Ripping stubborn audio track"
date: 2012-12-17
forum: Multimedia Software
---

### Post by Lars Noodén on 2012-12-17
I have an audio CD which has a stubborn audio track which refuses to let sound-juicer extract it.  Is there a way I can mount the CD and copy the track using the file system?  Or is there another way?

Sound Juicer extracts all the other tracks on the disk and there seems to be no visible physical damage to the disc.  When it gets to just that one track, the estimated time progresses, but then stops and stays at the same number apparently indefinitely.

---

### Post by sudodus on 2012-12-17
This is only a 'brainstorming idea'

If there is an error in the file system or the hardware storage, maybe ddrescue could be used to copy what is readable and then you can rip from the copy (maybe treat the bad spot in a lossy way).

---

### Post by mc4man on 2012-12-17
Try another ripper or browse in file manager to location & try copying the problem track directly (DnD to a folder, whatever

(just d. click on audio cd icon in nautilus or whatever you have to open location, in older Ubuntu releases it would be ~/.gvfs/cdda mount on .., in newer it would be simply cdda://sr0/ or cdda://sr1/, ect.

---

### Post by Lars Noodén on 2012-12-17
I've tried all the options that it gives me when I insert the CD: rhythmbox, audacious, sound juicer, xfburn (not relevant) and open in file manager.  Even Open in File Manager does not open up the disc.

---

### Post by andrew.46 on 2012-12-17
cdda2wav might have some useful options, have a look at this:

[http://www.andrews-corner.org/burning.html#audio](http://www.andrews-corner.org/burning.html#audio)

and scroll down to 'Using cdda2wav & cdrecord...'. Perhaps you could also add in *-paranoia* option.

---

### Post by sudodus on 2012-12-18
I have found a link, that might help you to find how it is mounted and to read and copy the track with problems.

Try the following command and ***use auto-completion*** (tab).
```
ls -l ~/.gvfs/cdda
```
The continuation is sensitive to the locale, and it works for me.

This is the link: [[COLOR="Red"]http://ubuntuforums.org/archive/index.php/t-1293693.html[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-1293693.html")

---

### Post by Lars Noodén on 2012-12-18
Strangely, this morning the audio CD was suddenly mounting.  Yet I couldn't read the whole of the last track using PCManFM.  That too gets stuck at the end of the track.  I think the disc has gone bad, but wonder which tools can compensate for the error(s).  

Thanks for the tips.  I'll try them out.

---

