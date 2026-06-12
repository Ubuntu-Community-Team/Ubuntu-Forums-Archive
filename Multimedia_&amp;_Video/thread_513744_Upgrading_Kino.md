---
title: "Upgrading Kino"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by flyingsolo on 2007-07-30
Synaptic currently loads Kino 0.9 but how do I upgrade it to the current version, 1.0?  Any easy way? (sorry, noob question I realize)
thanks

Maybe I should clarify--If Synaptic doesn't hold the latest version of a given software but it is available elsewhere, how do I install it? (Kino is my current example b/c version 1.0 is available from Kino site)

---

### Post by flyingsolo on 2007-07-31
OK--update--I've been working on this myself and figured I can download the .deb file myself & install it.  However, I get the following:
```
Preparing to replace kino 0.92-1ubuntu3 (using kino_1.0.0.deb) ...
Unpacking replacement kino ...
dpkg: error processing kino_1.0.0.deb (--install):
 trying to overwrite `/usr/lib/kino-gtk2/libkinoplus.so', which is also in package kinoplus
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 kino_1.0.0.deb

```

..so I'm not sure how to proceed.  Should I just remove the version0.92 first and then install 1.0? (by the way, I renamed the .deb package as kino_1.0.0.deb so I could type less!)

---

### Post by Steven_B on 2007-07-31
Are you using "**sudo** dpkg -i kino_1.0.0.deb"?

BTW, I wouldn't rename the .deb to save typing.  If you just type "sudo dpkg -i k", and then hit tab, bash will fill in the rest of the filename.

---

### Post by flyingsolo on 2007-07-31
Yes, I did use the sudo dpkg... as you suggested.  I only did the renaming on suggestion from a Psychocats tutorial which didn't seem to mess it up.

---

### Post by Steven_B on 2007-07-31
You probably have to remove the kinoplus package.  "sudo apt-get remove kinoplus"
I should have seen that before. :oops:

---

### Post by flyingsolo on 2007-07-31
Great--removed kinoplus (btw, what was its purpose & why is it expendable?) and then redid sudo dpkg kino and now get:
```
(Reading database ... 207472 files and directories currently installed.)
Preparing to replace kino 0.92-1ubuntu3 (using kino_1.0.0.deb) ...
Document `kino-manual' is not installed, cannot remove.
Unpacking replacement kino ...
Setting up kino (1.0.0-1~getdeb1) ...
warning: file `/usr/share/doc/kino/help/index.html' does not exist at /usr/sbin/install-docs line 821, </usr/share/doc-base/kino-manual> line 11.
warning: file mask `/usr/share/doc/kino/help/*.html' does not match any files at /usr/sbin/install-docs line 826, </usr/share/doc-base/kino-manual> line 11.

```

thanks for ongoing help.

---

### Post by Steven_B on 2007-07-31
I think kinoplus just includes some extra effects plugins.  The kino package from getdeb includes the stuff from both the kino and kinoplus packages.  However, it appears to not contain all of the documentation, so dpkg is giving you a warning.  Does kino run now, or did dpkg quit with an error?

---

### Post by flyingsolo on 2007-07-31
Kino works now but it does seem a little 'flakey' and will frequently freeze & need a force kill.  (working under Feisty)  I can get video capture from my camcorder (Sony TRV510, a digital 8 machine) but I don't get the AVC controls--not critical & I can probably fix it with more reading around.  I'm just starting with this but I understand Kino is mainly for video editing but not for authoring DVD's, correct?  What is best for the DVD authoring (mainly, just home movies +/- digital stills with overlaid music or commentary)?  Is this where I consider Cinelerra or something else?

edit:  Fixed one thing myself:  The AVC is fixed by starting Kino with gksudo Kino & I've read elsewhere that I can adjust udev priveleges to permit this without using sudo each time so I'll pursue that next.  Still curious about the DVD authoring process.

---

### Post by Steven_B on 2007-08-01
I haven't done anything with Linux DVD authoring software, so I don't know what works best.  Google around for different tools.  I have used Cinelerra - It's a powerful tool for editing video, but it's rather buggy and has a steep learning curve.  Some of the other programs might be better for your intended use, but that's up to you!  The [list on GetDeb]("http://www.getdeb.net/category.php?id=12") is also a good place to start.

---

