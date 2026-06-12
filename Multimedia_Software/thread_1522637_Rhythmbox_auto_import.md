---
title: "Rhythmbox auto import"
date: 2010-07-02
forum: Multimedia Software
---

### Post by McMajik on 2010-07-02
Hi,

Whenever I start rhythmbox, it starts scanning my external HDD for sound files. There are 450,000+ sound files at least, and it won't import my music collection while it's doing this. Is there a way to stop this? Disconnecting or hiding the drive isn't an option as my music collection is in a folder on that drive, and there isn't enough space on my local HDD to store it.

Thanks in advance,
McMajik

---

### Post by mamece2 on 2010-10-05
hello, i have the same problem with rhythmbox, i have my music in an external HD, it is a really big library with over 12,000 songs.

everytime i run rhythmbox it tries to load all the music in my external drive, is there a way to avoid this?

i just want the library to be loaded so i can play music from the HD

---

### Post by staticfive on 2010-11-03
YES.  This is incredibly irritating, as it renders RhythmBox useless for importing, and it insists on doing this every time I start it.  For 72,000 some-odd files (that I told it not to scan), it takes about 5 hours to finish before I can import a damned file.   This is unacceptable.  I'm not about to partition my drive just so RB stops arbitrarily scanning my entire life every time I start it.[-X

---

### Post by staticfive on 2010-11-03
Nice update:  I ended up moving ALL my music to it's own partition, and set the Library location to this location.  I updated the playlists and database file with the new locations, and it STILL scans the old external as a device.  

Next step, uninstall RhythmBox, delete the rhythmbox folder in .local, delete rhythmbox from .gconf, and reinstall.  Reset library location, let it rescan all the files, and..... NO F#$@*ING CHANGE!  

It still insists on scanning my entire external before letting me do anything.  The curious thing is... it's only scanning one particular partition on my external, and nothing else.  I. Don't. Get. It.

Is there a way to disable devices completely??  This is ridiculous!

---

### Post by staticfive on 2010-11-03
Found the problem:

The file .is_audio_player had somehow been placed on the root of the external.... Tricky, tricky rhythmbox!  I deleted it and now everything works as expected :-)

---

### Post by w4r_l0ck on 2011-01-06
YEAAAH excellent staticfive you saved my day. spent few hours cracking my head on that stupid bug that totally rendered rhythmbox USELESS!

---

### Post by migmruiz on 2011-02-07
> **staticfive said:**
> Found the problem:

The file .is_audio_player had somehow been placed on the root of the external.... Tricky, tricky rhythmbox!  I deleted it and now everything works as expected :-)

thank you!

how did it get there?

thanks anyway!

---

### Post by XelderX on 2012-01-05
> **staticfive said:**
> Found the problem:

The file .is_audio_player had somehow been placed on the root of the external.... Tricky, tricky rhythmbox!  I deleted it and now everything works as expected :-)

I'm having this same issue and would love to fix it, but I'm still learning to manipulate Ubuntu.

How do I find this file?

************Edit**************...nevermind....found it....right where it is supposed to be.

---

