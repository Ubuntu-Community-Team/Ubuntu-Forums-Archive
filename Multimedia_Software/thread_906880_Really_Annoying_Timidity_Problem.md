---
title: "Really Annoying Timidity Problem"
date: 2008-08-31
forum: Multimedia Software
---

### Post by SZ07 on 2008-08-31
Timidity is not using timidity.cfg to scan for soundfonts or eawpats. It defaults to freepats and changing options in timidity.cfg does absolutely NOTHING!

See details in next post

---

### Post by SZ07 on 2008-09-01
I installed and setup timidity and midi files play fine. However, I noticed some instruments were missing so I decided to switch from freepats to eawpats or some soundfont.

Here is where things get crazy. I downloaded eawpats and unzipped it to the correct directories. I opened up timidity.cfg in /etc/timidity and then changed the directory so it would look for eawpats. Well, it didn't work. I then tried to change to a soundfont but same result: timidity was still using freepats.

Then I deleted timidity.cfg and not only was I able to still able to play midis but it was still using freepats! Even more crazy, I deleted freepats.cfg and same thing, midis were still playing using freepats!

It seems obvious that timidity is not relying on timidty.cfg or freepats.cfg.

---

### Post by SZ07 on 2008-09-03
I figured out what the problem was. Timidity did indeed rely on the cfg files I mentioned. The problem was that I was playing midis through totem and totem doesn't use timidity as a backend. It uses its own midi codec.

---

