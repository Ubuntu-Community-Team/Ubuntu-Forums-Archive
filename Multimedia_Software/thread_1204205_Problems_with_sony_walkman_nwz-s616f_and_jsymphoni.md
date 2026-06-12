---
title: "Problems with sony walkman nwz-s616f and jsymphonic"
date: 2009-07-04
forum: Multimedia Software
---

### Post by pythonscript on 2009-07-04
I'm not sure if I missing something very straightfoward here or not, but anyways... I have a sony walkman nwz-s616f model (probably about a year old, by now) and I'm trying to sync music/playlists to it using jsymphonic. The device mounts properly, ubuntu sees it, etc, but I can't figure out where it is! jsymphonic wants me to point it to the device, but I can't find it's mount location. It's not in /media, and when I select "Computer" from the Places menu, it shows up adjacent to the Filesystem, as if it has no mount point within it. Any ideas? This is pretty much the only thing forcing me to dual boot, and I'd really like it solved. I don't have enough money to just buy a different mp3 player, either. :) So where is the Walkman? If anyone has any ideas to sync music/playlists to it that work better than jsymphonic, that'd be appreciated too. Thanks!

---

### Post by pythonscript on 2009-09-06
All right, so... I've found that a lot of people have had nothing but problems with sony's devices, and I'm apparently in the same boat. I ended up creating a virtualbox xp image that I connect my walkman to. I set up ~/Music as a network share between xp and ubuntu, installed a windows driver for the ext2/ext3 file system so Windows Media Player can read my music from the aforementioned network share. I then just use the basic WMP functionality to sync music to my walkman. Not exactly the solution I was hoping for, but it was easy to set up and works flawlessly. Main point: it works.

---

