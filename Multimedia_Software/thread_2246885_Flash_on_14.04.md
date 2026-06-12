---
title: "Flash on 14.04"
date: 2014-10-04
forum: Multimedia Software
---

### Post by oygle on 2014-10-04
Have done a fresh install of Kubuntu 14.04, and wanting to install Flash. The "flashplugin-installer" is not in Muon though.

Has the name changed ? See [https://launchpad.net/ubuntu/trusty/flashplugin-installer](https://launchpad.net/ubuntu/trusty/flashplugin-installer)

---

### Post by vasa1 on 2014-10-04
Did you enable restricted extras?

If you enable kubuntu-restricted-extras you may then see it.

---

### Post by oygle on 2014-10-04
I was thinking of doing that, but found a Mozilla document at [https://support.mozilla.org/en-US/kb/install-flash-plugin-view-videos-animations-games](https://support.mozilla.org/en-US/kb/install-flash-plugin-view-videos-animations-games)

Followed the instructions, and apart from some minor changes to the instructions, I can view videos in FB and Youtube okay now.

The minor changes to the instructions were:

1. The "tar" part is not correct, it extracts all the files when only libflashplayer.so is required
2. The command to copy should be **sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/**

Thanks.  :)

And, as a bonus, now the sound works in Kubuntu 14.04.  :D

---

