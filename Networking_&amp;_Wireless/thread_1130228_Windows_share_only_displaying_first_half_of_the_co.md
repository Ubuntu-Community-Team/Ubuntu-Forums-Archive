---
title: "Windows share only displaying first half of the contents"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by wookie_bw on 2009-04-19
Good morning!

I've got a bit of an odd problem. I have a Mythbuntu 8.10 combo frontend/backend in the living room that we mainly use for my little daughter to watch her movies. It uses multiple video sources, all Windows, that I mounted in /media. Everything worked just fine up until 2 days ago when we noticed that one of the shares only lists files/folders that start with 0-9/A-M. Anything past M isn't being shown. Other computers in the network can see the missing files just fine. The other share does not have this problem. Both have the same entry options in fstab, i.e. 

cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

There was one thing funny in the Myth logs:

videolist.cpp: getVideoListMetadata: index out of bounds: 0

This appears after running the video manager to repopulate the database. I Googled the error but found nothing to help with it.

I honestly have run out of ideas at this point and don't know what to do. Oh, one other thing, I've made no changes and have performed no updates on the machine since the initial build.

Thanks!

-Brandon

---

