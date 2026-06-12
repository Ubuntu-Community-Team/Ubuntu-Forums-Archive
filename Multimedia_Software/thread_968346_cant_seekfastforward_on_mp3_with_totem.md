---
title: "cant seek/fastforward on mp3 with totem"
date: 2008-11-02
forum: Multimedia Software
---

### Post by hachel on 2008-11-02
when i open an mp3-file it playes nicely, but in the bottom-left corner it says "Playing x:xx (streaming)" and I can't fastforward or seek (I can move the slider but that doesn't do anything).
what to do?
thanks

---

### Post by mic159 on 2009-03-27
I can confirm this. On a default installation of 8.10, i installed the "good" gstreamer pack, and mp3 files would not seek. To rectify, install the "bad" gstreamer pack (gstreamer0.10-plugins-bad-multiverse).

---

### Post by neilobremski on 2009-12-19
I have spent way too much time trying to figure this out and haven't found a solution for Ubuntu 9.10 Netbook Remix.  Today I thought: well, I'll just *remove* the "good" plugins to see if it forces gstreamer to use the "bad" ones.  It turns out trying to do this will also remove a ton of packages, including "ubuntu-netbook-remix".  So I wonder if this has to do with this in particular.  On my Ubuntu 9.10 Desktop installation I don't have this problem anymore.

Has anyone been able to get seeking in MP3's working under Ubuntu 9.10 Netbook Remix?  I'm considering doing a complete re-install just because of this one thing. :(

---

### Post by neilobremski on 2009-12-20
Alright, I got it working!  The missing piece of the puzzle was actually just adding in the "ugly" plug-in sets.  For your convenience, I have included a screenshot of "gstreamer" items in Synaptic Package Manager.

---

### Post by De4dSpace on 2010-03-02
Thanx Neil.  "gstreamer0.10-plugins-ugly" was all I needed, while cleaning up my system it was removed.

---

