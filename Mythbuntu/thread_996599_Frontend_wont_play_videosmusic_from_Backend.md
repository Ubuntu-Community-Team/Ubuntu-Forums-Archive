---
title: "Frontend wont play videos/music from Backend"
date: 2008-11-29
forum: Mythbuntu
---

### Post by cknight725 on 2008-11-29
Okay, so the issue is basically that the frontend can see the music and videos in the backend's database, however -- it won't play them.

Music throws a "DecoderMAD: Failed to open input file. Error 5" on the frontend ONLY. (Backend they play just fine!)

Videos just don't play -- selecting them causes the frontend to flash a mythtv "loading" screen for a split second, but that is all.  Again, playback on the backend is just fine.

If I do a search for music from the frontend, it blows away the music store on the backend, and likewise if I do a videos search -- it says all the files are missing and wants to remove them from the DB.

I can play recordings and watch TV streamed to the frontend without a glitch or jitter.

I confirmed that the mysql.txt file on each is identical. (Exception that the frontend uses the IP of the backend instead of localhost for the hostname - logical right?)

To make things fuzzier -- all my music and videos are in symlinked folders of samba mounts on the backend server.  I don't think these are the problem cuz as I said -- music and videos play just fine on the backend.

I'm running a fully updated Mythbuntu 7.10 (Gutsy) distro on both.  I'd prefer not to update to 8.04 or 8.10 cuz I use the backend to host some VMWare VM's and simply don't want to invest the time to migrate em.

Can anyone help?

---

### Post by SiHa on 2008-11-29
The music & videos folders need to be mounted on the local filesystem of the machine that wants to play them. So you need to set up Samba / nfs shares from the backend to your frontend.

I guess you already know how to do this, but see this post: [http://ubuntuforums.org/showthread.php?t=908779&highlight=nfs](http://ubuntuforums.org/showthread.php?t=908779&highlight=nfs) for a guide to setting up nfs shares for these folders.

Also - thanks to Newlinux for this point - the mount point on the frontend should be the same as on the backend else your metadata can get screwed.

---

### Post by cknight725 on 2008-11-29
Well -- thats just too simple.  Thanks!

---

