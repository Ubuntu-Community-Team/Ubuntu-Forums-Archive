---
title: "cd crashes when using vlc or cd player"
date: 2016-07-14
forum: Multimedia Software
---

### Post by newblank25 on 2016-07-14
when using vlc or cd player it crashes. i reinstalled vlc. from internet i got this solution [COLOR=#333333][FONT=Courier]sudo /usr/share/doc/libdvdread4/install-css.sh i opened terminal & typed it in. It didn't recognize this command. any help would be appreciated.[/FONT][/COLOR]

---

### Post by ajgreeny on 2016-07-14
Do you have libdvdread4 package installed?

You will not get that command to do anything if not as the install-css.sh script is part of that package.

---

### Post by Keith_Helms on 2016-07-17
That install-css.sh script is the old method for setting up dvd support in a ubuntu system. It used to be part of the ubuntu-restricted-extras package.  If you're having trouble playing an audio CD, setting up DVD playback will not help.  To start with, you'd need to post whatever error you're getting when you try to play the CD.

---

