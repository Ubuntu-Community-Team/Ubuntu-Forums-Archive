---
title: "Default Application on Samba Share"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by seaders on 2008-01-01
This is a wierd problem that I've found while trying to fix playing AVIs with VLC over a samba share.

First off, I'm on 7.10, and if I have an AVI on my Desktop and double click it, it opens up perfectly in VLC, like I want it to.  If I right-click it, it shows me the default operation, 'open with "VLC"', then it shows me the other options, 'open with "Movie Player"' and so on.  However if I double-click it when it's on a samba share, it opens with Totem Media, if I right-click it, it only shows 'open with "Movie Player"' as the default application and 'open with Other Application' as the only other option.

Just to detail the VLC problem, if I open a AVI file from a samba share, it does open up, but as stated, incorrectly in Totem.  However, if I go the long route (Other Application --> VLC), VLC does open up, but doesn't open the file.  Even if I drag and drop the file into the player itself or even the playlist (both which work with a file from the desktop), nothing happens, no errors, no notifications, nothing.  Nor will it stop a playing video if I drop it into it.  Strange thing is that if I manually do a 'open network stream' and type in the full samba address, it opens and plays perfectly.  Stranger still, if I start VLC and change the skin, to say 'Skins 2', then I can drop a file into it.  

Any ideas on either issue?

---

