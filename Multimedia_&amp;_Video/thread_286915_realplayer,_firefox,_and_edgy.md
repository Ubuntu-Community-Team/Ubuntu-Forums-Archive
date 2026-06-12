---
title: "realplayer, firefox, and edgy"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by stevieb on 2006-10-28
hello,

just upgraded to edgy and trying to get realplayer to work with firefox again.  i've installed realplay with automatix and removed mplayer-in-rm files, replaced them with nphelix files, but still no dice- realplayer doesn't come up when clicking on an rm link.

i noticed that on previous occasions, the first excecution of realplay runs a dialog that configures mozilla plugins.  this did not happen this time.  is there any way to do this manually, or should I remove/reinstall realplay?

thanks,
-steve

---

### Post by stevieb on 2006-10-29
this seems to have solved the problem:
```
sudo apt-get remove totem-mozilla
```

hope this helps anyone else!
-steve

---

### Post by tomcat1965 on 2006-10-31
eek! "sudo apt-get remove totem-mozilla" wants to remove the Ubuntu desktop!!
Sounds a rather drastic solution to watching the occasional beeb vid!!
I reckon this is because I did a distro upgrade not a fresh install,removing a plugin shouldn't mean sacrificing the desktop surely? anyone else get this warning when trying to remove the plugin?:confused:

---

### Post by stevieb on 2006-10-31
from what i understand removing "ubuntu desktop" is not as drastic as it seems.  i experienced no change whatsoever; can't guarantee you'll have the same luck.

here, check [this ]("http://www.ubuntuforums.org/showthread.php?t=286459&highlight=remove+ubuntu+desktop")out!
-steve

---

### Post by edmund on 2006-11-22
There's a way of doing it without removing ubuntu-desktop, which claims to be required "to ensure proper upgrades".

cd /usr/lib/firefox/plugins
rm libtotem* 
Copy the libtotem* files to a different directory first, just in case.

---

