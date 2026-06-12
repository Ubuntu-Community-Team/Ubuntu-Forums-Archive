---
title: "Can't get MP3Diags  to do anything"
date: 2012-12-24
forum: Multimedia Software
---

### Post by Carl H on 2012-12-24
I've just installed the MP3Diags tool and I can't get it to do anything at all. When it runs up it asks me to select a directory to include.

No matter which one I select, when I click OK I get an error box saying "You need to select at least a directory to be included in the session."

After a search on here and the net, I seem to be alone in having problems, so quite possibly it's user error...

It's version 1.0.11.076-1 on Xubuntu 12.10 64-bit.

---

### Post by Yellow Pasque on 2012-12-24
Just clicking/selecting a directory won't do anything. There's actually a checkbox between the name/icon of the directory and the arrow to its left that expands the directory tree. Depending on your theme, the checkbox can be difficult to see (I'm using Debian with xfce and it certainly was for me).

Mp3diags looks to be a Qt (not gtk) app, so if you want to make changes to your theming, you'll need to find something capable of modifying Qt theming (the KDE systemsettings package does that, but it will probably pull in a bunch of crap you don't want if you install it). There's probably a better way, but all of the theming stuff confuses me (and I'm not the only one), so I personally just find a good dark, gtk theme and forget about tweaking.

---

### Post by Carl H on 2012-12-24
> **Temüjin said:**
> Just clicking/selecting a directory won't do anything. There's actually a checkbox between the name/icon of the directory and the arrow to its left that expands the directory tree. Depending on your theme, the checkbox can be difficult to see (I'm using Debian with xfce and it certainly was for me).

Yes, that's sorted it out! Thank you. :D

---

