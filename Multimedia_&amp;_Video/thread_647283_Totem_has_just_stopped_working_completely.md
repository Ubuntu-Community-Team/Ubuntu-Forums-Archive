---
title: "Totem has just stopped working completely"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by ubukool on 2007-12-22
Hi everyone,

I've got a problem with Totem - it's just stopped working.  I click on the icon to start it and it appears and pretty soon 'greys out' to show that it's not responding.  This is without even trying to play a file!  Anyone got any ideas?  I've tried reinstalling everything - totem, totem-mozilla, etc but nothing seems to be working.  I can't figure out why it should suddenly stop - the only things I've done since yesterday have been to install a new update and install flyback (I also tried installing time vault but uninstalled it again).

Any ideas?  Thanks in advance for any help.

---

### Post by ubukool on 2007-12-22
Hi,

I fixed it!  This morning, in addition to the packages I installed I also installed the ear training package 'GNU solfege' with its dependencies to have a look at it.  Later, I uninstalled it with its extra dependencies 'timidity' and 'freepats' and it must have been then that Totem broke.  I've subsequently reinstalled solfege and Totem is working fine now.  There must be some strange dependency going on.

This is just a note for someone who installs solfege, uninstalls it and subsequently find that Totem is broke.  The answer is to reinstall solfege and its dependencies.

:)

---

