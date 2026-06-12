---
title: "Rhytmbox doesn't play ogg sound files in Ubuntu 13.04"
date: 2013-08-24
forum: Multimedia Software
---

### Post by nacho-wan on 2013-08-24
Hi, I installed Ubuntu 13.04 last week but for the life of me I can't get rhytmbox to play ogg files. I'm recycling my home directory which has been migrated through the last 10 or 12 ubuntu releases. I used one of those to encode those songs long ago.

Thank you for taking the time to read this post. Let me know if you need additional info.

---

### Post by mc4man on 2013-08-25
I'd first  try removing any  registry.xxxx.bin files you have & see if that helps (they will be recreated as needed.
(RB now uses gstreamer1.x where it used to use gstreamer-0.10

Look for one here -  (hidden folder
~/.gstreamer-0.10/

Also here -  (again a hidden folder
~/.cache/gstreamer-1.0/

---

