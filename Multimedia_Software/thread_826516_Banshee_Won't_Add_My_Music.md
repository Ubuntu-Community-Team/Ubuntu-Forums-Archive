---
title: "Banshee Won't Add My Music"
date: 2008-06-12
forum: Multimedia Software
---

### Post by Literati on 2008-06-12
I'm using Banshee 1.0.0.1 and it's refusing to add my music.
I've tried choosing both "Import Local Folder" and "Import Local Files" and each way it'll show as though it's importing the files in the bottom left hand corner, but alas, it doesn't show up in my list of artists, or anywhere.

I've tried a COMPLETE removal of Banshee through synaptic, and reinstalled, but still no dice.

What gives?

EDIT:

I ran Banshee through Sudo, and it's able to add the same files, and they show up. Yet, I don't like doing it this way, as all my other songs/settings are gone. :(

---

### Post by paulderol on 2008-06-12
Is it a permissions/ownerships issue? If root can, and user can't, it often is, although i'm not really really familliar with banshee. also, did you install the package from the repos or did you pull from their site?

---

### Post by Literati on 2008-06-12
Well, that's the thing. I've been able to add songs until right now. And I've never run it as root before... 

Secondly, I installed it from the repos, using Synaptic.

---

### Post by ARhere on 2008-06-12
Not sure if this will help, but is your music on a network or shared drive?  If it is did you make sure to mount the network drive?  And if so, did you make sure your user has rights to read and write to the drive?

-AR

---

### Post by asphixmx on 2008-06-12
I recently installed Banshee 1.0 and have the same issue. I've never used before Banshee, it is the first time I try to use it and I can't add any music to my library either.

---

### Post by ARhere on 2008-06-13
> **asphixmx said:**
> I recently installed Banshee 1.0 and have the same issue. I've never used before Banshee, it is the first time I try to use it and I can't add any music to my library either.

Again I ask, is your music stored on a remote drive?  I.E.: not directly connected to your PC running Banshee?

-AR

---

### Post by bgjmo on 2008-06-13
i had the same problem.  it ended up being the fact that my music wa son a network drive.  so i mounted the drive to the computer running banshee.  works like a champ now.

---

