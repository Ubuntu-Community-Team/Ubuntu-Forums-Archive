---
title: "Rhythmbox wont start HEEEELP!"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by bigbrovar on 2007-09-16
Everthing was working fine till i decided to enable some plugins in rhythmbox..i think i have enabled all the available pluggins...after i did these Rhythmbox just failed to load any more..i try completely uninstalling and reinstalling but nothing gives...i even tried sudo apt-get remove --purge rhythmbox and reinstalled nothing..when i tried to lunch it via terminal i get this 



[HTML]WARN  coherence                   Sep 16 11:06:00  Coherence UPnP framework version 0.4.0 starting... (coherence/base.py:156)
Segmentation fault (core dumped)
[/HTML]


please any help would be appreciated.
Thanks

---

### Post by bigbrovar on 2007-09-16
any body am getting despirate..or should i format and reinstall?? :( :confused:

---

### Post by bigbrovar on 2007-09-16
i was able to fix it by uninstalling Python UPnP framework thru synaptics and then then when i tried again amarok worked ..i then wemt on to disable the upnp pluggin ..and i installed Python UPnP framework back..and eveything worked...am written dis incase o=someone else has the same problem so he can easily follow my lead maybe it might help

---

### Post by oniichan on 2007-11-03
I had exactly the same problem. Thought it would be cool to see the other plugins. With exactly the same result you did. (Why this doesn't seem to happen to many others is puzzling?) I removed [COLOR=Red]rhythmbox[/COLOR] completely with the package manager and **THEN **deleted every [COLOR=Red]rhythmbox [COLOR=Black]directory in my user account, re-installed, and everything worked again. And I won't be adding those plugins anytime soon. If anyone has used the *libvisual-0.4-plugins* to work in [COLOR=Red]rhythmbox[/COLOR], I'd like to hear about your experience.[/COLOR][/COLOR]

---

