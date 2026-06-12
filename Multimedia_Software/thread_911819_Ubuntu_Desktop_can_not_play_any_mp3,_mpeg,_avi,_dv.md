---
title: "Ubuntu Desktop can not play any mp3, mpeg, avi, dvd, ... by default."
date: 2008-09-06
forum: Multimedia Software
---

### Post by asadi on 2008-09-06
After I installed ubuntu desktop, I see that it can't play any mp3, mpeg, avi,... file. I guessed that ubuntu can not play this formats by default and we should install additional plugins to play them. But after a while I see that my sound card is not installed and this is the reason of the errors.

---

### Post by wolfen69 on 2008-09-06
> **asadi said:**
> Why you have named it "Desktop Linux" when it can not play any mp3, mpeg, avi, dvd, ... by default. !?

newsflash: windows does not play those things by default either after a fresh install. ```
sudo apt-get install ubuntu-restricted-extras
``` takes care of that. not difficult. if you want codecs preinstalled, there are a number of distros that come with the ability to play them immediately after install.

---

### Post by vishzilla on 2008-09-06
Those are restricted formats. read [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for info

---

