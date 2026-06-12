---
title: "SYNC ARCHOS5 with Amarok"
date: 2010-07-11
forum: Multimedia Software
---

### Post by jack frost on 2010-07-11
I am trying to get Amarok to see my Archos5 device. Rhytmbox sees the device fine; but I want to try and use Amarok to sync playlist.  I can do it with Songbird inside Win7 virtual but trying to avoid having to use windows.  The linux version of songbird does not support mtp from what I have seen. I also tried to use   p, li { white-space: pre-wrap; }  /media/ARCHOS5/Music) but Amarok crashes with that mount command.
Any help is appreciated. Thanks.

---

### Post by jack frost on 2010-07-14
> **jack frost said:**
> I am trying to get Amarok to see my Archos5 device. Rhytmbox sees the device fine; but I want to try and use Amarok to sync playlist.  I can do it with Songbird inside Win7 virtual but trying to avoid having to use windows.  The linux version of songbird does not support mtp from what I have seen. I also tried to use   p, li { white-space: pre-wrap; }  /media/ARCHOS5/Music) but Amarok crashes with that mount command.
Any help is appreciated. Thanks.

i marked it solved... even though I settled with just using media monkey inside windows 7 virtual machine.. Media Monkey is the best show far with no issues on syncing the archos..

Basically just:
- checked all my playlists under the auto-sync list  playlist tab
- checked "Delete tracks... " under auto-sync options  (and check confirm deletion)
- Removed all auto-conversion rules

-  Device config tab; Sync tracks to: \Music\<Album  Artist>\<Album>\<Track:2> <Title>
check "Copy  Playlists", under options check "Library Playlists"; Destination  directory: \Playlists\
check "Use only the first Genre... "
check  "Use only the first value...  "

got this info. from:
[http://www.mediamonkey.com/forum/viewtopic.php?f=12&t=38134](http://www.mediamonkey.com/forum/viewtopic.php?f=12&t=38134)

---

