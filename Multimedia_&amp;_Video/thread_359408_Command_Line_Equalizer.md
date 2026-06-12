---
title: "Command Line Equalizer"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2007-02-11
I need to play with an equalizer to some MP3 files, and I'm looking for something that runs in the command line instead of a GUI. I adjusted my EQ in Beep Media Player on a particular song and exported the EQ file as:

[Equalizer preset]
Preamp=9.6
Band0=12
Band1=16
Band2=16
Band3=17.6
Band4=17.6
Band5=-4.8
Band6=12.8
Band7=12.8
Band8=17.6
Band9=16

So now I need to take this bit of info and process the MP3 as another MP3 through this EQ filter. Anyone got the command for that? I did a man on 'ecasound' and couldn't figure where to load multiple frequency settings like this. So, I think I need some other command line tool.

---

### Post by bionnaki on 2007-02-12
open terminal
and run alsamixer

---

### Post by Mike'sHardLinux on 2007-02-12
> **bionnaki said:**
> open terminal
and run alsamixer

Your alsamixer has an equalizer? Mine does not.

---

### Post by bionnaki on 2007-02-12
close enough.

---

