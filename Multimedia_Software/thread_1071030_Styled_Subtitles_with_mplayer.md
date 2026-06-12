---
title: "Styled Subtitles with mplayer"
date: 2009-02-15
forum: Multimedia Software
---

### Post by Jerrac on 2009-02-15
How can I get styled subtitles with mplayer? Currently it just displays the subs in a default font, colors, and position. I would just use VLC, but it doesn't play the files as well as mplayer does.

---

### Post by Jerrac on 2009-02-22
Six days and no reply.

Doesn't anyone have any ideas? Or even know if it is not possible?

---

### Post by shirilover on 2009-02-22
Add the following to your mplayer command line:
-a s s -embeddedfonts
( ^ ^ remove spaces)
or add the following to your ~/.mplayer/config file:
a s s=yes
#^ ^ remove spaces
embeddedfonts=yes

Another choice is to use the smplayer front-end which will give you a graphical method for enabling styled subtitles.
See here -> [http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)

---

### Post by Jerrac on 2009-02-22
> **shirilover said:**
> Add the following to your mplayer command line:
-a s s -embeddedfonts
( ^ ^ remove spaces)
or add the following to your ~/.mplayer/config file:
a s s=yes
#^ ^ remove spaces
embeddedfonts=yes

Another choice is to use the smplayer front-end which will give you a graphical method for enabling styled subtitles.
See here -> [http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)

I tried adding it to my config file, but it didn't work. It still goes with the default font.

I haven't tried smplayer yet.

---

### Post by Jerrac on 2009-02-22
Sweet! smplayer works! Thanks!

---

