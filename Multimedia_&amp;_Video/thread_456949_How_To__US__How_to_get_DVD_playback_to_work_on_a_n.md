---
title: "How To:  US:  How to get DVD playback to work on a new install without automatix or"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by tinker123 on 2007-05-28
This is how I got DVD playback to work on a clean install of Feisty without using automatix, easyubuntu, or altering my sources.list in other ways ( it screws up the update manager for upgrading to new versions of Ubuntu....hence the reason why I did a clean install ).
[B]
First, after a clean install backup  your /etc/apt/sources.list by making a copy of it under a new name in the same directory which indicates that it is the original sources.list from installation.   Should you ever be tempted to alter your sources.list or let a script alter it you can use this backup along with an apt-get how-to to fix your system.   I don't recommend it as there is a learning curve and a lot of futzing involved.   You are better off avoiding altering your sources.list or having other things alter it.[/B]


1.  Go to synaptic package manager under System | Administration.   Search for "totem-xine".  Install it.

2.  Do the steps detailed here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

3.  Download all-20061022.tar.bz2, put a copy of all of the codecs in all of the directories (do "sudo bash" to sign in as root to make the directories  ) mentioned in the README file.   If this URL is no good google on the name of the file:
[http://www1.mplayerhq.hu/MPlayer/releases/codecs/](http://www1.mplayerhq.hu/MPlayer/releases/codecs/)

4. I don't know if it is necessary but set the permissions on each of those directories and all of their contents to 777, i.e.:

chmod -Rv 777 /usr/lib/codes/*

HTH

---

