---
title: "Problems ripping a brand new CD"
date: 2008-06-23
forum: Multimedia Software
---

### Post by eajohnson on 2008-06-23
hey guys,

so i came down to my computer today in hopes of ripping a new CD i just got. unfortunately, when i put the CD in the drive spun for a minute or so, then an icon on my desktop popped up labeled "Audio CD".  I tried to open the CD in Nautilus and straight from the desktop and it shows the tracks listed as Track 1, 2, etc. with a little lock symbol next to the icons. When i try to rip it using Sound Juicer, it will start the rip but never move off of the first track.  When i tried to open the CD using Amarok this was the error message i got:

Could not start process Unable to create io-slave: klauncher said: Unknown protocol 'audiocd'


Also can't rip it from Rhythmbox. lists the CD as Unknown Audio.

Any suggestions? Thanks

---

### Post by wolfen69 on 2008-06-23
it sound like you need codecs. go [HERE]("https://help.ubuntu.com/community/Medibuntu") to enable medibuntu repos. then install gstreamer codecs (good/bad/ugly) from synaptic. or just install vlc. (it has almost all codecs)

---

### Post by mc4man on 2008-06-23
> with a little lock symbol next to the icons That's normal for cds. What happens if you drag a track to the desktop?

---

