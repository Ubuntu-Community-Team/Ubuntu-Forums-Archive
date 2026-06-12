---
title: "mplayer"
date: 2005-12-18
forum: Multimedia &amp; Video
---

### Post by Ana Carolina on 2005-12-18
Hi
I have the ubuntu breeze (5.10) installed in a laptop Toshiba satellite A45 series...
The totem program doen't work to play dvd, so I've tried the mplayer but I keep getting an error with VobSub (Bad magic in IFO header) that I don't know what does it mean...
But then when I was looking at the  mplayer in my Add Applications it says:
***This program is not currently installable. It should be available in the "multiverse" section of the repository. Enable that section in the Repositories dialog in the Settings menu to install it.***

Does anyone know which dvd player I can use?

thanks a lot
Ana

---

### Post by frodon on 2005-12-19
I advice you to run automatix, it's the quickest way to solve your problems here : [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563).
The lib which is needed to play dvd (all the player use it) is libdvdcss2 : [http://ubuntuforums.org/showthread.php?t=81577](http://ubuntuforums.org/showthread.php?t=81577)

---

### Post by jliedeka on 2005-12-19
You can enable multiverse by editing your /etc/apt/sources.list.  There should be some commented out lines with "multiverse" in them.  If not, read the instructions on [http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/").

---

