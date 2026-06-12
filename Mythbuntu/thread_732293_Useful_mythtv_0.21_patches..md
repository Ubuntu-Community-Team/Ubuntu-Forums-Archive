---
title: "Useful mythtv 0.21 patches."
date: 2008-03-22
forum: Mythbuntu
---

### Post by jmatienzo on 2008-03-22
I have been using the patches from the following link [http://www.ronfrazier.net/ronfrazier.net/mythtv/]("http://www.ronfrazier.net/ronfrazier.net/mythtv/")
for about a week and they are working great, thanks Ron. Is there any way we can get these added to the mythbuntu 0.21 fixes repo when it goes live, thank you.

---

### Post by laga on 2008-03-22
We usually do not add patches, especially for new features, to the builds unless they're also committed to MythTV mainline.

You can always create your own PPA :) I'm looking forward to seeing some of these paches merged, too.

---

### Post by jmatienzo on 2008-03-29
Quick question on building debs from source, if I'm reading the debian/rules correctly(apt-get source mythtv) you are getting the latest source code from the fixes branch.

---

### Post by laga on 2008-03-29
> **jmatienzo said:**
> Quick question on building debs from source, if I'm reading the debian/rules correctly(apt-get source mythtv) you are getting the latest source code from the fixes branch.

Usually, yes. The current package in hardy is 0.21 with some patches from the release-0-21-fixes branch. The next upload will be built completely from the release-0-21-fixes branch (including some patches, of course).

You can get the packaging part here: [https://code.launchpad.net/~ubuntu-mythtv/mythtv/mythtv-fixes](https://code.launchpad.net/~ubuntu-mythtv/mythtv/mythtv-fixes)

---

