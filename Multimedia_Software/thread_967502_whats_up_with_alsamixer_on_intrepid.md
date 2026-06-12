---
title: "whats up with alsamixer on intrepid?"
date: 2008-11-02
forum: Multimedia Software
---

### Post by bionnaki on 2008-11-02
alsamixer only shows one slider on intrepid - it has always shown them all on previous ubuntu versions.

any ideas?

---

### Post by bionnaki on 2008-11-02
bump

---

### Post by mc4man on 2008-11-02
That's because your using pulse. I haven't fooled with it because sound works quite well here by default. If you wanted to see more alsamixer 'sliders' then double click on the speaker icon in upper panel -> preferences and add what you wish to see. Whether anything but the master and or individual pcm sliders work I don't know. It's probably better to make adjustments if needed thru pulse anyway

---

### Post by bionnaki on 2008-11-02
I dont use gnome, so I dont have the preferences you speak of.

Is there anyway to change from pulseaudio to the old alsa setup? I prefer to adjust sound via console - I'm running a mostly CLI install.

---

### Post by metalgtr on 2008-11-03
I had the same problem but fixed it; I have GNOME so I just ended the process for pulseaudio in the system monitor, but you can do also do this from the terminal if you don't have GNOME, then I launched alsamixer in a terminal and all of the trackbars reappeared. Hope this works on your system, too.

---

