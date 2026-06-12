---
title: "Changing Rhythmbox settings?"
date: 2010-10-27
forum: Multimedia Software
---

### Post by Guns90 on 2010-10-27
Hello all.  I installed Ubuntu 10.10 yesterday, and cannot find the answer to my question.  I have a whole music library of mp3's on a secondary drive that I want to use in Rhythmbox.  However, in Rhythmbox's Music Player Preferences I can't get either the Library Location to change from "Multiple locations set" or the Preferred format to "CD, Lossy mp3".  Can somebody help please?

Okay, maybe a little more info.  When I go into Edit>Preferences>Music, where it says "Multiple locations set", it is greyed over (I think that's the term.  You can't access it.) When I go into the Preferred format, mps isn't there, but it does show up in another window when I click on edit; however, the only options I have there are 'Close' and 'Help'.  The help button brings up another window and syas its loading, but stays in a loading mode forever.  Anyone?

---

### Post by JimBuntu on 2010-10-30
Me too. Just had this problem. I'm trying to burn some cd's to put on my 5th gen ipod and I need to do it in .mp3...

Rhythmbox doesn't show .mp3 as an option. It does show it when I click edit but I am not able to select it. It's only allowing .flac, .ogg and .mp2

Anyone...

---

### Post by mc4man on 2010-10-30
probably the ugly-multiverse, though you could just fill in all the main gstreamer plugins

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by geeky_chris on 2010-11-27
I've got the same problem, installing the bad and ugly as described above hasn't helped :-(  Does anyone else have any tips?

---

### Post by keithpeter on 2010-11-28
> **geeky_chris said:**
> I've got the same problem, installing the bad and ugly as described above hasn't helped :-(  Does anyone else have any tips?

Hello geeky_chris

Have you already installed ubuntu-restricted-extras? I usually install this set of packages and rhythmbox shows the mp3 setting for ripping then. You also get the flash plug-in and the MS core fonts. If you don't want those, then you will need to work out which of the packages in ubuntu-restricted-extras is providing the functionality.

The first album I ripped produced mp3s that showed 48 kb/s as their bit rate. They didn't sound like 48Kb/s mp3s and the file sizes come out about right for 128kb/s.

Cheers

---

