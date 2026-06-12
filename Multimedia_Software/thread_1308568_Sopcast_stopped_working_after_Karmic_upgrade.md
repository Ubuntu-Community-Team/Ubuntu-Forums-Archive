---
title: "Sopcast stopped working after Karmic upgrade"
date: 2009-10-31
forum: Multimedia Software
---

### Post by shanksy75 on 2009-10-31
I have used Sopcast on 64 bit ubuntu 9.04 fine from just installing the two debian installers 'sp-auth' and 'sopcast gui'

However, since the upgrade to 9.10 I cannot get any streams to play.

Every link I paste it just says 'connecting' and then 'retrying' in an endless cycle.

Has anyone else experienced this, are there any dependencies not available in 9.10.  I have tried uninstalling and reinstalling both deb's.

Hope someone can help, I can't bear having to boot into windows!

---

### Post by shanksy75 on 2009-11-16
For anyone interested I solved this by uninstalling sp-auth and sopcast-gui.

I then re-installed the 64 bit sp-auth 3.0.1, then installed the sopcast gui with built in libstdc++5 from :

[http://www.sourceslist.eu/installare-software-tramite-repository/installare-sopcast-player-0-3-0-su-ubuntu-karmic-koala-9-10-in-pochi-click/](http://www.sourceslist.eu/installare-software-tramite-repository/installare-sopcast-player-0-3-0-su-ubuntu-karmic-koala-9-10-in-pochi-click/)

Just remember to get the 64 bit sp-auth from google code, the sp-auth from the link above I think is just the 32 bit build as it didnt work for me.

---

