---
title: "Firefox and streaming.. again.. *sigh*"
date: 2008-07-20
forum: Multimedia Software
---

### Post by ChimpofDOOM on 2008-07-20
Ok relatively new member here at the forums!

However this issue has been somewhat a thorn in my side!!

Firefox, opera, basically anything that uses flash.. will play video.. but alas no sound.

I've done the suggested fixes from previous posts (they worked last night), but my problem seems to of adapted (maybe my computer is sentient now..) and now the previous fixes wont work :(

Any help welcomed with open arms \\:D/

---

### Post by gandaran on 2008-07-20
can you describe what type of fix you have done?
there are a lot of them around, one of the best is to just use flash 10, not flash 9.

---

### Post by ChimpofDOOM on 2008-07-20
I have tried everything in this thread

[http://ubuntuforums.org/showthread.php?t=708907](http://ubuntuforums.org/showthread.php?t=708907)

Well except for the pulse audio thing.  This problem isn't isolated in Firefox, it's apparent in Opera too.

---

### Post by Duranxl on 2008-07-20
swf-dec doesnt give me sound, but flashplugin-nonfree does

---

### Post by ChimpofDOOM on 2008-07-20
Yeah, I have the flash plugin, sound was working for a bit last night then suddenly stopped, then came back this morning and it was gone again..

---

### Post by gandaran on 2008-07-20
I,m still not sure what you have done, but if you installed 'libflashsupport', (libflashsupport fixes the sound issue with flash 9, but sometimes makes firefox crash) I still recommend removing libflashsupport and the flashplugin-nonfree and install adobe flash 10,
flash 10 is still in beta, doesn't work on some sites but will fix the flash sound problem.
get flash 10 tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) , just unpack/extract the package and drag the libflashplayer.so file to the hidden home .mozilla/plugins folder (no plugins folder there? make one) or to /usr/lib/mozilla/plugins.

if you also use opera, it's best it's installed in /usr/lib/mozilla/plugins

---

### Post by ChimpofDOOM on 2008-07-21
Cheers i'll give that a try when I get home.

---

### Post by Denizen08 on 2008-07-21
> **ChimpofDOOM said:**
> Firefox, opera, basically anything that uses flash.. will play video.. but alas no sound.

I have the same problem as you, but I seem to have found a quick fix and possibly a symptom of the problem.

First off: Have you been playing music or watching any media locally before you activated/opened/browsed into the streaming page (e.g. the page that contains the flash file from youtube)?

If you have then try closing all the multimedia players you have had running then the browser. Then try to open the page again from firefox. At this point, my problem was fixed. Basically, I think whatever makes multimedia playback possible cant multitask with flash streaming and local media streaming(?).
If not then it maybe something else... it would be best if you described in detail the symptoms of the error.

Hope it gets fix quick, for you and for me.

---

### Post by ChimpofDOOM on 2008-07-21
It's true that I usually do have Banshee open, but as i said before this wasn't a problem the previous night....

Ah well, will have to wait till I get home and test it :)

---

