---
title: "Is it just me or is the latest Flash update really unstable?"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by samwyse on 2008-02-13
Firefox hangs or crashes often when browsing Youtube. It started after the update a couple of days ago.

---

### Post by jan quark on 2008-02-13
try this perhaps it will help
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by samwyse on 2008-02-14
Still the same crashing.

---

### Post by Dai777 on 2008-02-14
[http://videotutes.blip.tv/#669639](http://videotutes.blip.tv/#669639)
here is the problem I'm having with the flash plugin if you know the cure let me know.

---

### Post by Skitalets on 2008-02-15
I didn't see any instability with the new update, but the sound was horrible -- lots of crackling and stuff.  This should fix the problem for you:

Download the tarball [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash"). Extract it to a temporary directory.  Then run this command:

sudo cp libflashplayer.so /usr/lib/firefox/plugins/

In general, I have had lots of problems with the Ubuntu packages, but as long as I copy that library file to the Firefox plugins directory, it usually works just fine.  If you use other browsers, you might also need to copy the file to /usr/lib/flashplugin-nonfree/ as well.

---

