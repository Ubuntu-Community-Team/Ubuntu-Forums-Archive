---
title: "Need ideas for centralized multimedia management"
date: 2009-12-22
forum: Multimedia Software
---

### Post by LightningCrash on 2009-12-22
My home network:
-The big box, an Ubuntu 8.04 LTS box connected to the HDTV. Exports NFS, DLNA. Has VNC via vino-server and a vnc4server session in the back. Has a card-reader.
-Wife's laptop. 9.10 Karmic,  Aspire One, card reader. NFS mounts the big box's drives RO in fstab
-My laptop. 9.10 Karmic, Same deal, different make/model.
-Floater laptop. 9.10 Karmic, Same deal, but just a spare.

So I have the problem of everybody popping the SD cards into whatever they happen to be using and having 30940938 copies of everything everywhere because nobody in my house bothers to delete crap from the SD cards.

Is there any photo management software that uses inotify or some sort of directory watcher loop to suck up photos from a pickup folder? Bonus points if it discards duplicates.

I'm probably going to autofs the NFS mounts and mount a user-specific RW directory from the HTPC. It would be nice if there is something that could play right into this.

Thanks in advance.

---

