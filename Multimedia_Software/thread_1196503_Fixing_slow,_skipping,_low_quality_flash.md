---
title: "Fixing slow, skipping, low quality flash"
date: 2009-06-25
forum: Multimedia Software
---

### Post by Nubi505 on 2009-06-25
When I tried to watch a Youtube video in Ubuntu I was kinda dissapointed. I got it to play, I got the sound to work, and then the quality plain sucked and it skipped and sometimes looked odd and if I wanted to type or browse at the same time it made everything very slow. I noticed other people were having these flash issues.

But! I found a solution (by no means on my own). If it has already been posted I didn't find it, or maybe I'm blind, sorry! Hopefully this will help some people with the same problem. 

[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)

It worked for me, nothing blew up, youtube videos work, the sound still works (thanks god), I'm typing and browsing at light speed as I listen to Lovex streaming and it sounds great! 

Hope it works for anyone that needs it.

---

### Post by lovinglinux on 2009-06-25
The deb file from Adobe web site (adobe-flashplugin) has a different hash than the flashplugin-nonfree from the repositories and there are some reports of better performance using it, but I couldn't perceive any difference.

You could also try my [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567), which includes an simpler command to uninstall swfdec and install the flashplugin-nonfree.

These are my [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) benchmark points improvements using the suggested tweaks:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118681&stc=1&d=1245764692[/IMG]

The improvement is also due to recent updates of the kernel, xorg, compiz and other important packages.

---

