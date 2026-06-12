---
title: "SoundKonverter/k3b problems - Ripping audio CDs, CDDB track data wrong"
date: 2009-08-15
forum: Multimedia Software
---

### Post by Shampyon on 2009-08-15
I'd like to use k3b to rip some Audiobook CDs (specifically the Ricky Gervais podcasts I bought from Audible - I had to burn them off on a Windows PC to enjoy them on my kUbuntu desktop thanks to their lack of Linux support). The reason Id prefer k3b is that it reads the Track and Album data from the CD itself instead of the CDDB - the CDDB actually has the wrong data! The Ricky Gervais audiobooks are "recognized" as various blues and folk singers by the CDDB!

Unfortunately, k3b seems to be having problems ripping MP3s. I run through the Rip Audio CD process, it creates the subfolders etc, but no MP3 files ar created!

I've tried various other CD Rippers, from RipperX to abcde to SoundKonverter, but unfortunately they all retrieve the incvorrect information from the CDDB, and I don't see any option to read from the CD-Text. I haven't been able to try Asunder due to it constantly crashing before the GUI starts (segmentation fault).

My ideal fix would be to find out how to get MP3 ripping working in k3b. Second best (but still great) would be to configure SoundKonverter to read the track and album data from the CD.

Where do I go from here?

---

### Post by Shampyon on 2009-08-16
17 hours later bump?

---

### Post by Shampyon on 2009-08-16
I thought I found a fix...

I went into *Settings/Configure K3b/Plugins/Audio Encoder/External Audio Encoder/Configure/MP3 Lame/EDIT* and ticked the *Swap Byte Order* and *Write Wave Header* boxes. From what I've been able to dig up this should fix the problem.

Unfortunately, k3b has other ideas. Once I press the OK buttons, it invisibly unticks the boxes! It *refuses* to let those options stay chosen!

---

### Post by Shampyon on 2009-08-17
Additional: I've tried this as my regular user account and as root. Either way, k3b will not save the settings. What the &#9762;&#9889;&#9881;&#9785; is going on?!

---

