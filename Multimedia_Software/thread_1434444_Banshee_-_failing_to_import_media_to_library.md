---
title: "Banshee - failing to import media to library"
date: 2010-03-20
forum: Multimedia Software
---

### Post by aquascrotum on 2010-03-20
I'm using the Banshee team PPA - since the last update banshee fails to import music media (at present all i've tried are mp3s) when I direct it to a media folder.  

Anyone else having this problem?  How do I go about posting a bug report?

---

### Post by boombox1387 on 2010-03-20
In general, see [http://banshee-project.org/contribute/file-bugs/](http://banshee-project.org/contribute/file-bugs/) for information on filing bugs against the Banshee project.

Recently, Banshee switched to the GIO backend, which caused some problems with importing.  I would guess that your issue has already been reported (and maybe even fixed).  For more info, see:

[https://bugzilla.gnome.org/show_bug.cgi?id=613182](https://bugzilla.gnome.org/show_bug.cgi?id=613182)
[https://bugzilla.gnome.org/show_bug.cgi?id=613292](https://bugzilla.gnome.org/show_bug.cgi?id=613292)
[https://bugzilla.gnome.org/show_bug.cgi?id=611813](https://bugzilla.gnome.org/show_bug.cgi?id=611813)

All three of these issues are related to either importing or rescanning the music library, and all three have been fixed.  If you want to test the latest version, you can add the Banshee Daily Build PPA to your software sources, or you can build from source.  Alternatively, you can just wait a few days, because I think 1.5.6 should be released sometime soon.

---

### Post by aquascrotum on 2010-03-22
Thanks for the reply - update today from Banshee team seems to have sorted the problem.  Happy again!! :)

---

### Post by boombox1387 on 2010-03-23
> **aquascrotum said:**
> Thanks for the reply - update today from Banshee team seems to have sorted the problem.  Happy again!! :)

Glad to hear it!

---

