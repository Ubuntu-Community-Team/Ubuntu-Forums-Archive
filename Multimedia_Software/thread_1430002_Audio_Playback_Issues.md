---
title: "Audio Playback Issues"
date: 2010-03-14
forum: Multimedia Software
---

### Post by Spaztic_One on 2010-03-14
Hello all, I am currently running Karmic as an install "within" Windows XP (trying it out / getting my feet wet / whatever you choose to call it) and I am experiencing issues in regards to audio.

First problem I discovered: Audio played through Rhythmbox has atrifacts within it. Crackles and other things are present that should not be. I do have the "restricted codec" pack installed. It should also be worth noting that I am hearing these crackles in both MP3 and flac encoded files.

Next thing I found: When I was checking things out to see if I could determine the cause of problem 1, I went to the Sound Preferences window and tried setting my speakers to 5.1 surround sound (which my computer is fully capable of) and the sound went from 95% clear to about 1%, and that 1% was nothing but faint crackles. Setting to 5.0 fixed it, but reduced the level to about half of what it normally is. It is currently set to Stereo Duplex, which was the default.

The third and final problem I have noticed is: Flash video (Ala Youtube) has no sound. None. Not even crackling.

I have followed [This]("http://ohioloco.ubuntuforums.org/showthread.php?t=766683") but it has not helped any of my issues.

Any help is appreciated, and if you need more information (such as system info not mentioned below) all you need do is ask.

Ubuntu 9.10 Karmic Koala
Intel Pentium 4 with Hyperthreading @ 2.8 GHz
3 GB DDR2 asymmetrical

Thanks
-Jim

---

### Post by Spaztic_One on 2010-03-14
Update:

So, as a Windows user, I played all of my music through foobar2000, not using WMP for anything if I could avoid it, and not using iTunes but for burning / ripping CDs. Well, I just ran foobar2000 in WINE, and it seems to play back the audio with out quality defects. I don't know why, but it does.

Edit :: User in IRC directed me to [This Site](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html), and following those directions seem to have solved all issues.

---

