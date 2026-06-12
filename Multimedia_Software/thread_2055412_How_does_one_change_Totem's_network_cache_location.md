---
title: "How does one change Totem's network cache location?"
date: 2012-09-09
forum: Multimedia Software
---

### Post by a2_ on 2012-09-09
Hi All,

I have hard times trying to use Totem to watch a large movie file via network (using the 'Open Location' option). 
Since Totem stores its cache in /tmp and my root partition(where /tmp sits) isn't really big (about 10GB), the 4GB movie file fills out all the space available that way not allowing the system to operate properly. 
The first idea that came to my mind was to change the default cache location, but Totem's Preferences menu does not have this option, neither the settings available via gconf do (I looked into /apps/totem).
Does anybody know how the Totem's cache location can be changed (maybe the name of gconf option I could put into  ~/.gconf/apps/totem/%gconf.xml manually)? Any help is appreciated!

P.S. I'm using 12.04.1 x86

P.P.S. Basically, I am able to watch the movie, there are a couple of workarounds available 
here, staring from just downloading the file, and even (temporal) symlinking /tmp to other place. The question is mainly about Totem's capability to use another location for its network cache.

---

