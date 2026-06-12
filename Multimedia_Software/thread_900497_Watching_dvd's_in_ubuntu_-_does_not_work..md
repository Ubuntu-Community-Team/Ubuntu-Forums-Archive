---
title: "Watching dvd's in ubuntu - does not work."
date: 2008-08-25
forum: Multimedia Software
---

### Post by jakupl on 2008-08-25
Only approx. every second dvd works in ubuntu. This is very annoying as half of my movie collection is worthless for me now.

Is there any way of knowing if a movie works before you buy it, is there some special kind of codex, or the copy protection?
What is the problem?

---

### Post by r0k3t on 2008-08-25
Did you install the libdvd3 codec? 

scope out this thread
[http://ubuntuforums.org/showthread.php?t=899502&highlight=dvd+codec](http://ubuntuforums.org/showthread.php?t=899502&highlight=dvd+codec)

---

### Post by jakupl on 2008-08-25
> **r0k3t said:**
> Did you install the libdvd3 codec? 

scope out this thread
[http://ubuntuforums.org/showthread.php?t=899502&highlight=dvd+codec](http://ubuntuforums.org/showthread.php?t=899502&highlight=dvd+codec)

yes I did.

---

### Post by mc4man on 2008-08-25
While there may be some titles that require a patched or the new version of libdvdnav4 and maybe a couple that can't be played back at all, 50% isn't right.

Did you install libdvdcss2?
If not add medibuntu as a repo source and install.

see here about medibuntu, ect.
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

new dvdnav (if you want to install do that after getting dvd playback going -  it has reduced error message output when used with vlc, ie. less info for troubleshooting.
Just go to link, d. click app. ver, (probably i386), pick mirror and let Gdebi handle - don't uninstall current libdvdnav4, Gdebi will do that for you

[http://packages.debian.org/lenny/libdvdnav4](http://packages.debian.org/lenny/libdvdnav4)
above link is slow loading today

---

### Post by wolfen69 on 2008-08-25
what media player are you using? have you tried vlc?

---

