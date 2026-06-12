---
title: "solution to sound muted on startup"
date: 2008-06-04
forum: Multimedia Software
---

### Post by el_morsa on 2008-06-04
Hi, I'm new to the forums and wanted to contribute with a solution to a little annoyance I found while using Ubuntu on a Dell Optiplex 745. 

I noticed the sound on the front speaker is controlled by the "Mono" entry in Volume Preferences, and the value of that entry is not saved across reboots. Whenever I boot the machine, this entry is muted by default. 

I managed to workaround this problem by editing the file /etc/init.d/alsa-utils, adding the line:

unmute_and_set_level "Mono" "90%"

in the function sanify_levels_on_card(). I hope it helps you.

---

