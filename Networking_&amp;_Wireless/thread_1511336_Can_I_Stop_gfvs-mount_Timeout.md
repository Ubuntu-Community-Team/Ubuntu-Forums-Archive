---
title: "Can I Stop gfvs-mount Timeout?"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by justinmiller87 on 2010-06-16
So here's what I've done.

First, I ran [FONT="Courier New"]gvfs-mount smb://tv-pc/media_drive/[/FONT] from the command line to mount my media drive on my network. Then I ran [FONT="Courier New"]ln -s ~/.gvfs/media_drive\ on\ tv-pc ~/media[/FONT] to create a sym link to my media in order to let Banshee play nice and actually read my music.

This works great except that if I walk away from my computer for a while, I come back and the system has seemingly forgotten the network share even exists and I have to run [FONT="Courier New"]gvfs-mount smb://tv-pc/media_drive/[/FONT] again in order for my drive to show up. Is there any way to keep the network share alive full-time short of constantly playing music? It gets annoying honestly and I don't want to have to periodically go and check to see if it's mounted before I start playing music.

---

### Post by justinmiller87 on 2010-06-20
Bumpity bump

---

### Post by justinmiller87 on 2010-06-30
bump

---

