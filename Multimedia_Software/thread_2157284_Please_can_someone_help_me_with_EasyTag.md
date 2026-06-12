---
title: "Please can someone help me with EasyTag"
date: 2013-06-24
forum: Multimedia Software
---

### Post by oxf on 2013-06-24
This is probably down to my ignorance having only just installed EasyTag for the first time and the fact that I can't find a "beginners guide" So if someone could set me straight please...

I've scanded the directory and the tagged the music tracks with the names I wish to use and saved them. They seem to save OK because when I open it all later and re-scan all my stuff is still there. However, when I transfer the tracks to my MP3 player it doesnt seem to transfer, the tracks are all listed as "track1, track2...." etc. What am I doing wrong here?

Thanks
Katelyn

---

### Post by tgalati4 on 2013-06-24
There are several versions of ID3 tags.  Some players will only read a particular version of ID3.  Also, ID3 tags can be stored in different places in a music file.  Some players have trouble with embedded pictures (typically album art).  So, you need to do some research on your particular player and see what version of ID3 it accepts.

Look in Settings-->Preferences-->ID3 Tag Settings.  Try changing the settings.  Use one mp3 as a test case and keep changing the settings until your player can read it.  Keep accurate notes as to what you tried and what works.

---

### Post by oxf on 2013-06-25
Thanks. 
Well I researched it and found that my version of Walkman doesn't seem to be compatible with ID3v2.4 and need to switch to 2.3 in the settings menu. I did that and changed about everything else I could think of but still no luck. It doesn't seem to want to transfer the tag to the mp3 player so I don't know? 

Anyway i found I can rename the file name in the file manager and name it that way and then copy to the mp3 player. (I thought it wasn't supposed to be possible that way?) Of course this means it appears on the player as "trackname.mp3" but I suppose I can live with that.

---

### Post by tgalati4 on 2013-06-25
Some Sony players are problematic.  I had to use [jsymphonic]("http://symphonic.sourceforge.net/page.php?4") to be able to transfer files.  What version of the player do you have?

Try unchecking ID3 version 2.3/2.4 and just write ID3 version 1 tags and see if your player recognizes that.  All you need is Artist and Song Title.

---

