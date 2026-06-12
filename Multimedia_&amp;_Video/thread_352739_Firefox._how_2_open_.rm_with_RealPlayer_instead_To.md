---
title: "Firefox. how 2 open *.rm with RealPlayer instead Totem"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by uterrorista on 2007-02-03
in firefox:
i want to **open *.rm files with Real Player** instead Totem...

the firefox launches totem.. "An externel aplication...." bla bla bla

this should be possible with about:config ... **but how?**

---

### Post by aysiu on 2007-02-04
Have you tried going to Edit > Preferences > Content > File Types > Manage?

---

### Post by uterrorista on 2007-02-04
yes, i already tried that...
without any success.

there, i can't see RM extension...

---

### Post by aysiu on 2007-02-04
Hm. Maybe it's not a Firefox thing, then.

Have you tried right-clicking an .rm file, selecting **Properties**, **Open With**, and then adding in RealPlayer and making sure the black dot is next to it?

---

### Post by uterrorista on 2007-02-05
i don't have any rm file.
but i renamed an other sound to rm and it opens with MPlayer... :( not with totem...
what can i do?

---

### Post by aysiu on 2007-02-05
Try this: ```
cd /usr/lib/firefox/plugins
sudo rm totem*
``` Then restart Firefox and see if you still get the behavior.

---

### Post by LotsOfPhil on 2007-02-13
I had a similar problem with m3u files. I edited mimeTypes.rdf and changed NC:useSystemDefault="true" to "false" in the appropriate section. The next time I opened an m3u, the dialog popped up and I got to pick the app I wanted.

---

### Post by Ms_Angel_D on 2008-07-18
> **LotsOfPhil said:**
> I had a similar problem with m3u files. I edited mimeTypes.rdf and changed NC:useSystemDefault="true" to "false" in the appropriate section. The next time I opened an m3u, the dialog popped up and I got to pick the app I wanted.

I hate to dig up an old post but I'm having this same issue, where exactly is mimeTypes.rdf located?

Thanks,
Angel

---

### Post by Ms_Angel_D on 2008-07-18
Nevermind I found it ;)

---

