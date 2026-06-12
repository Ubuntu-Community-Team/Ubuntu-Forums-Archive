---
title: "flash fullscreen"
date: 2013-12-06
forum: Multimedia Software
---

### Post by the_luke on 2013-12-06
hi,

as a follow-up to this (closed) thread
[http://ubuntuforums.org/showthread.php?t=2173647](http://ubuntuforums.org/showthread.php?t=2173647)

so i've got the latest version of flash for linux (the one that's gonna be the last version, 11.2.202.327) and firefox 25.0.1+build1-0ubuntu0.13.10.1 and the described behaviour does not happen on youtube (which runs flashplayer as far as i can tell), but happens in other video players, like jwplayer (used for streams).

clicking fullscreen on jwplayer (and others) works for the first time after the browser was launched. then when you minimize and try to go into fullscreen again the fullscreen-image is shown for a short time and disappears, and the embedded player goes black.
i just changed from precise to saucy, and it worked(works) on precise (with the same flash version but firefox 25.0+build3-0ubuntu0.12.04.1).
i also tested different gfx drivers, this happens with nouveau and nvidia-319. i don't know, this could suggest it's due to a firefox bug? but maybe not.

anyway, i didn't really find a fix, but a kind of workaround. using the windows flashplugin through pipelight ([https://launchpad.net/pipelight](https://launchpad.net/pipelight) and [http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)) works pretty good (also doesn't interfere with existing wine installations) and gives the latest flash (windows) version (11.9.900.152). i thought i'd share this. maybe this thread could be prefixed [solved] but not quite i guess.

---

