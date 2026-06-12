---
title: "Youtube/flash not working in Chromes latest update."
date: 2010-05-31
forum: Multimedia Software
---

### Post by brad1138 on 2010-05-31
When I try to view Youtube/flash I get the message "You need to upgrade your Adobe Flash Player to watch this video." but when I try to upgrade it says I already have the current version.

Any ideas?

Brad

---

### Post by lovinglinux on 2010-05-31
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

I know, is not a Chrome tutorial, but is the same old problem all people that get that message have. You are probably running swfdec plugin simultaneously with the one from Adobe and swfdec is actually the one being loaded. So you need to remove it.

---

