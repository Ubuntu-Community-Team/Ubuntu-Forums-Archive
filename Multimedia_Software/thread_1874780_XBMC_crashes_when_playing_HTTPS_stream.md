---
title: "XBMC crashes when playing HTTPS stream"
date: 2011-11-03
forum: Multimedia Software
---

### Post by Pwndrian on 2011-11-03
Hello,

on my fresh install of Ubuntu 11.04, XBMC 10.1 (installed from team-xbmc's stable PPA for Maverick) crashes when playing a video file streamed over HTTPS.

After struggling with the problem for several hours, I finally found a hint on [http://trac.xbmc.org/ticket/11601](http://trac.xbmc.org/ticket/11601), where fry indicates that the problems lies within the version of libgnutls26 used in Ubuntu 11.04. As he points out, the solution to this problem is to install a newer version (2.12.12-1 worked for me) from the Debian experimental repository. Before, you may also need to install a newer version of libp11-kit0 (version 0.8-1 worked for me).

Best regards,
Pwndrian

---

