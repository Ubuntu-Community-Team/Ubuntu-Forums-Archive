---
title: "DVD playback problem (fixed)"
date: 2008-11-23
forum: Multimedia Software
---

### Post by mediocrates on 2008-11-23
Even with all the right files installed, Xubuntu's default command parameters for DVD playback resulted in the following error message when I tried to play DVDs:

"Totem could not play 'file:///home/my_home_dir/dvd:/'."

The fix was to go into the settings manager and change the command for DVD playback from "totem dvd:/" to "totem /dev/dvd".

---

