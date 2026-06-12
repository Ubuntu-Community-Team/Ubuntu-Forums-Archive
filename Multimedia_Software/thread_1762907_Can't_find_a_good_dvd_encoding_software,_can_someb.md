---
title: "Can't find a good dvd encoding software, can somebody recommend something?"
date: 2011-05-19
forum: Multimedia Software
---

### Post by someitalian123 on 2011-05-19
I'm looking for a dvd encoding software for linux that has a gui, can make menus, supports subtitles, and supports 2 pass encoding. I tried devede and everything seemed perfect till I looked at the file size of the dvd files, I tried setting the bitrate high enough to fill up a dvd, but the ending file size was only 2 GB. The bitrate was way too low. Are there any programs for linux that have are like devede but allow for higher bitrates.

---

### Post by wolfen69 on 2011-05-19
[DVD Styler]("http://www.dvdstyler.de/en/")?

---

### Post by SeijiSensei on 2011-05-19
> **someitalian123 said:**
> I'm looking for a dvd encoding software for linux that has a gui, can make menus, supports subtitles, and supports 2 pass encoding. I tried devede and everything seemed perfect till I looked at the file size of the dvd files, I tried setting the bitrate high enough to fill up a dvd, but the ending file size was only 2 GB. The bitrate was way too low. Are there any programs for linux that have are like devede but allow for higher bitrates.

I'm guessing your source files were in the Matroska container.  MKV's don't contain the video bit rate in the headers, so [DeVeDe is unable to determine the optimal bit rate]("https://bugs.launchpad.net/ubuntu/+source/devede/+bug/349011") for the DVD.  Usually it ends up over-estimating the size of the resulting file as you discovered.

You can set the bit rate manually in the GUI. You can also use mencoder to estimate the bit rate of the source material using [this method]("https://bugs.launchpad.net/ubuntu/+source/devede/+bug/349011/comments/15").

---

