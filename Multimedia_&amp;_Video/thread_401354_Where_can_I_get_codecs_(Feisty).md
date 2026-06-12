---
title: "Where can I get codecs? (Feisty)"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by Crakie on 2007-04-04
In Edgy, I let Automatix handle this sort of thing. But now I have Kubuntu Feisty installed and the video players are giving me a hard time. I wonder if there is repository (or more) where I can find all the codecs I realistically can expect to need?

---

### Post by tpg on 2007-04-04
If you're using KDE and Kaffeine (which I assume you are because of the "K" :) ), and you're using the xine backend for kaffeine (which I think is the default), then
```
sudo apt-get install libxine-extracodecs
```
should get all you need. If you need more, look for the w32codecs package (it's not in the repositories as far as I know) which has even more codecs. Hope this helps! :)

---

### Post by Crakie on 2007-04-04
Thanks, that fixed it! :)

---

