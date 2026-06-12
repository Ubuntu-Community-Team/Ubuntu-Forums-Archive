---
title: "totem-xine"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by mechanic on 2007-05-05
After going through the procedure on the Feisty user guide (I thought Feisty was supposed to do this for you automatically?) I got totem-xine to play a DVD fine. On the other hand I can't get it to play from files saved from other DVDs. It will play individual .VOB files, but it doesn't appear to see the .IFO files which presumably sort out the continuity through the  movie. And when it does play the individual .VOB file, I can't click on options to choose scenes or other options (like 'Play Movie'!). Any ideas on how to fix this problem?

Regards, m.

---

### Post by mechanic on 2007-05-05
Ah-ha! A quick follow up; in this thread:
[http://ubuntuforums.org/showthread.php?t=87417&highlight=vob+files+xine](http://ubuntuforums.org/showthread.php?t=87417&highlight=vob+files+xine)
it's explained that entering (for example) file:///media/sda8/Films/SomeFilmTitle into the OpenLocation box sorts this out! And it does seem to work!

Regds, m.

---

### Post by kevindontenville on 2007-05-05
Hi, I have a similar problem. Opening a saved DVD on Edgy was easy, Open Location and paste/type the uri and off it went playing the dvd as it would on a dvd disk itself.

However on Feisty I get no drop down or similar on the Open Location and when I paste or type the location in it it tells me it doesnt have a plugin to handle the location and shows it as eg [http:///location/on.the/disk](http:///location/on.the/disk).

If I manually type the uri file:///location/on.the/disk then it works fine. Maybe a bug unless anyone has another solution?

Does that file:/// bit work the same for you?

Kevin

Aha close posting! glad we are on the same track hadnt found that one yet!

---

### Post by mechanic on 2007-05-06
Yes, this lack of design thought followed by no real customer testing is typical of Ubuntu releases I'm afraid.

Regds m.

---

### Post by jiminycricket on 2007-05-06
Make sure you file a bug about this (if there's not one already) at [http://bugs.gnome.org](http://bugs.gnome.org)

---

