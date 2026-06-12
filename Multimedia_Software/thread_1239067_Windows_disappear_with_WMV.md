---
title: "Windows disappear with WMV"
date: 2009-08-13
forum: Multimedia Software
---

### Post by ChaucerChaser on 2009-08-13
Hello, 
  I've been working on this issue for maybe ten hours and am still confused. At first i kept getting an error from mplayer saying i needed the wmvdmod.dll. Even though mplayer was the only player to display an error message all video players automatically closed when i tried to play a WMV movie. So i went about getting the codecs and changing permissions to the /usr/lib/win32 so i could actually place the codecs in the folder.

   Well, It worked, the error message went away....But wait, the player still closes each time i try and play a WMV file, so now i'm wondering after reading and doing everything i could do, if anyone has any idea why i still cannot watch these videos. I have used all the knowledge i know and hope someone help out.

---

### Post by pmlxuser on 2009-08-13
this always works
```

$ sudo apt-get purge name_of_application

```
making sure that all the setting for that application have gone
then
```

$sudo apt-get install name_of-application

```
installing fresh and since all the codec are already installed you should get things working.

By the way have you tried VLC -it seems good at playing things like these

```

$sudo apt-get install vlc

```

---

### Post by mc4man on 2009-08-13
With stock repo players the only one which will play that format is mplayer (using win(w)32codecs.

so to see the issue start mplayer from the terminal in this manner
mplayer /path/to/[COLOR="Blue"]whatever.wmv[/COLOR]

If the file is loose in home folder then just
mplayer [COLOR="Blue"]whatever.wmv[/COLOR]


> So i went about getting the codecs and **changing permissions** to the /usr/lib/win32
certainly not necessary (the bold, if part of problem easily corrected


Vlc could play that format if built with the --enable-loader option which the ubuntu repo's and ppa's are either...
unwilling to do so
unable to do so
uneducated to do so

thread concerning same codec, though in this case the Op had a 64bit install where 32codecs are not usable w/ 64 bit players, you may wish to glance thru

---

