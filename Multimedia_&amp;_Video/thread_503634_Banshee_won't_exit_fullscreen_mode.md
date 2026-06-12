---
title: "Banshee won't exit fullscreen mode"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by Death &amp; Taxes on 2007-07-18
I've got a problem with Banshee 0.12.1. I've clicked on the option "Fullscreen" in the "View" menu and now it doesn't want to exit the fullscreen mode. Removing the option doesn't work, restarting the app doesn't work, it goes into fullscreen mode right after the start and it is impossible to get it out of there again. I also won't minimize, and I can't move it with Alt+Click (there's also no title bar). When I choose "Mini mode" it changes into the small window, but after clicking "Full mode" it's fullscreen again. 

I was looking for a config file, but obviously Banshee stores the configuration along with the all the other data in the database (there's no text file to edit :()

Usually this wouldn't be a big problem, I would simple delete the configuration and start with a new one, but in this case it's a bit different: I've got about 40 Podcasts in there and I'm - quite honestly - too lazy to manually search all the RSS feeds again. Too bad there isn't an option to export the Podcast-Feeds into an XML file or something.

Any idea how to solve that problem?

---

### Post by marsmissionaries on 2007-07-18
try pushing F11

---

### Post by Death &amp; Taxes on 2007-07-18
Pressing F11 would be same as clicking on the menu option. Doesn't work.

---

### Post by marsmissionaries on 2007-07-18
did you actually try it, or are you just saying this?

---

### Post by Death &amp; Taxes on 2007-07-18
Yes, I tried it.

---

### Post by marsmissionaries on 2007-07-18
have you tried gconf-editor?

---

### Post by Death &amp; Taxes on 2007-07-18
Ah, very nice. The values for /apps/banshee/player_window/height and /apps/banshee/player_window/width were maxed out.

Thanks for the hint!

---

