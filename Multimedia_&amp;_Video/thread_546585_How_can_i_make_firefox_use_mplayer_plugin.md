---
title: "How can i make firefox use mplayer plugin"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by dandandan on 2007-09-09
Hello guys

How can i make firefox use the mplayer plugin for videos, seems the plugin that comes per default plays only half of the time, other half screen stays black, and it wont play apple.com/trailers at all, pretty annoying. So if anyone could point me in the right direction where i can tell mozilla which plugins to use, that would be very helpfull


mfg
dan

---

### Post by trvr on 2007-09-09
The best I could dig up is this: [http://ubuntuforums.org/showthread.php?t=540412](http://ubuntuforums.org/showthread.php?t=540412)

It looks like you have to remove a couple of packages and then install the mplayer plugin. I hope it works!

---

### Post by dandandan on 2007-09-09
thx

well for now i removed the totem plugin(totem annoyes the hell out of me, no idea why gnome took the inferior video player,compared to mplayer,vlc etc.)
but when removing totem, apt prompts u to autoremove a lot of gnome packages which i dont want to, and i dont want to lose the autoremove option.
isnt there any config thingie for mozilla where u can say, "hey firefox, pls use plugin xy for playing video files"

i also dont understand why gnome depends on totem instead on "some video player", pretty annoying IMHO

---

### Post by trvr on 2007-09-09
Aww, ok. I found another guide that just moves the totem pluging files. Give it a go: [http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html](http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html)

---

### Post by dandandan on 2007-09-09
thx, this avoids at least the package dependency problem.

---

