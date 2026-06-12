---
title: "vlc error Edgy"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by Freiburg05 on 2006-11-09
Hi, 

    First of all, sorry for my bad English. I don't usually post many threads, so I hope this will be in the right place.


     I've upgraded From Dapper to Edgy (I don't recommend it), using the official method (#gksu "update-manager -c"). Many of my applications have now problems, some of them I already solved, and others I'm trying to. My problem now is that vlc doesn't work anymore. This is what the terminal returns:

inaki@ehLinux:~$ vlc
VLC media player 0.8.6 Janus
[00000285] skins2 interface: skin: Chaos  author: Cyril Deguet (based on Omar Hussain's skin)
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)


     Tried to uninstall and reinstall, but the same error appears.

     Any Ideas?

     Thanks!

---

### Post by ThrobbingBrain66 on 2006-11-09
it seems to be complaining about a Choas skin.  if you installed that skin for it, i would remove it from .vlc (in /home) and then restart vlc.

i have edgy and vlc works flawlessly

---

### Post by Freiburg05 on 2006-11-09
Thanks! It was the skin. It seems the Chaos skins has a problem now. I tried winamp5 skin (I had also installed), and it crashes also. The default skins and another one called Dalin_Media_Player work fine. I haven't tried any other. 

   Thanks again! Cheers.

---

