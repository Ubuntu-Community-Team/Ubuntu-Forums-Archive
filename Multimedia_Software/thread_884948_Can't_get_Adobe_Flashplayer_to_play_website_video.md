---
title: "Can't get Adobe Flashplayer to play website video"
date: 2008-08-09
forum: Multimedia Software
---

### Post by arnicainthemembrane on 2008-08-09
I am trying to play videos from the site [http://wiredispatch.com/news/sources.php?s=APVideo](http://wiredispatch.com/news/sources.php?s=APVideo) but when I hit the "play" button the little screen goes blank. I unblocked pop ups for this site with firefox. As I don't know what kind of file the video is, I can't choose the application in Edit-Preferences-Appications. Any advice, appreciated.

---

### Post by jolx on 2008-08-09
those videos don't work for me either, i'm pretty sure that they aren't videos. have you watched videos on this site before?

---

### Post by zachalekos on 2008-08-09
they don't work here either

---

### Post by arnicainthemembrane on 2008-08-09
They sure look like videos... I guess I can get someone to try from a windows OS computer or a Mac...

---

### Post by arnicainthemembrane on 2008-08-09
I also tried their "photos" page, maybe it's an issue with the site.

---

### Post by elcid89 on 2008-08-09
> **arnicainthemembrane said:**
> They sure look like videos... I guess I can get someone to try from a windows OS computer or a Mac...

These play on my Ubuntu box (Hardy) as Flash. Likewise on my Mac. They're Flash videos.

---

### Post by elcid89 on 2008-08-10
> **arnicainthemembrane said:**
> I also tried their "photos" page, maybe it's an issue with the site.

Try this procedure if you want. I had never ending problems with Flash. This fixed them.


wget [http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb)

sudo dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb

sudo apt-get remove --purge flashplugin-nonfree

sudo apt-get install flashplugin-nonfree

---

### Post by arnicainthemembrane on 2008-08-10
[http://launchpadlibrarian.net/134700...untu2_i386.deb](http://launchpadlibrarian.net/134700...untu2_i386.deb)
           => `134700...untu2_i386.deb'
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:06:11 ERROR 404: Not Found.

---

### Post by lukjad on 2008-08-10
The "vids" don't work here either.

---

### Post by shiver202 on 2008-08-10
those videos works for me , im  on win vista , right now

---

### Post by wolfen69 on 2008-08-10
i'm on hardy and the videos work fine for me. you are obviously having problems with flash.

---

### Post by lukjad on 2008-08-11
Funny. The all of the vids on every other site I go to work just fine.

---

