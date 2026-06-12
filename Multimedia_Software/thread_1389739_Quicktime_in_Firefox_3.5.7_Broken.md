---
title: "Quicktime in Firefox 3.5.7 Broken"
date: 2010-01-24
forum: Multimedia Software
---

### Post by bluefoxox on 2010-01-24
Hey All,
  
  I am having trouble getting Quicktime to work in Firefox 3.5.7 on a 64bit Ubuntu 9.10 Wubi install.  I have read and tried the suggestions in several threads using totem, mplayer and VLC (which of the three I like VLC the best).  When I type about:plugins into the address bar of the it shows that VLC can handle Quicktime extensions, but when I go to [www.apple.com]("http://www.apple.com") and try to view a video I am prompted to download Quicktime.  Any help here would be greatly appreciated.

PS  [www.youtube.com](www.youtube.com) does not work as well.  I am not experienced enough to know whether the problems are related.  Please advise.

Thanks!
Patrick

---

### Post by mikewhatever on 2010-01-24
Well, quicktime definitely works in Firefox, check it out yourself.
[http://www.esm.psu.edu/Faculty/Gray/old-apple-ads.html](http://www.esm.psu.edu/Faculty/Gray/old-apple-ads.html)

I suspect the problem is with apple.com, since Apple is among the least Linux friendly companies. Perhaps if your browser doesn't identify as Linux/Firefox, the movies will play. If you think you must watch movies from apple.com, try using the Agent Switcher extension. Check out [http://www.supportdetails.com/](http://www.supportdetails.com/) to see what a site gets from you.

Youtube uses Flash, apple.com quicktime, so no, they aren't related. Have you installed flash?

---

### Post by bluefoxox on 2010-01-24
Thanks for the reply. I did get the problem fixed.  This was accomplished by installing ubuntu-resricted-extras, removing VLC and then re-installing MPlayer, all using the synaptic package manager.  Everything works great now.

---

