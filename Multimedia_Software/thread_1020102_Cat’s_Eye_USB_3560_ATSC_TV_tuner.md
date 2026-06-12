---
title: "Cat’s Eye USB 3560 ATSC TV tuner"
date: 2008-12-23
forum: Multimedia Software
---

### Post by orziv on 2008-12-23
Did anybody figured out how to use an Ebox Cat’s Eye USB 3560 ATSC TV tuner with Ubuntu? I used it with Windows XP and it was great, but I have no idea how to make it work with Ubuntu.

---

### Post by cubdukat on 2012-03-06
You probably already gave up on it, but unfortunately there is no way. The tuner chipset apparently isn't supported in Linux.

Unfortunately, it's not even supported in Windows. VBox abandoned the tuner a couple years back, and they don't even have Windows drivers for it anymore. 

About the only way I could think of to get it to work would be something like ndiswrapper, which lets you use Windows drivers for network devices, except for everything else...

---

