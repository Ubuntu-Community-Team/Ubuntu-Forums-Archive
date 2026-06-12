---
title: "Problems importing large music library into RhythmBox"
date: 2010-09-28
forum: Multimedia Software
---

### Post by roberj13 on 2010-09-28
I tried searching this topic, but couldn't find anything specific to my situation. I have two 1TB drives connected to my desktop that I have shared with my laptop. Mainly I have shared one folder on one of the drives and one on the other that has 20 subfolders of music with about 50k songs total. 

I have tried to import this library into RhythmBox on the laptop, and my problem is it will start importing and then at some point the drive will unmount. When I go through and reconnect it I can start importing and access the files right away but it will never get through all of the files before disconnecting again. 

Each of the folders have about 2k-2.5k songs in each and I am trying to import a folder at a time. Should I be trying a lot smaller amount. If so, what is the magic number. I was actually hoping to set it up to start importing and do something else but can't if I have to keep watching it.

---

### Post by roberj13 on 2010-09-28
I actually seemed to resolve the problem I was having. After I modified the /etc/fstab to permanently mount the smb shares, RhythmBox started syncing up just fine now up to 9k songs and counting into the player and no dragging folder by folder.

---

