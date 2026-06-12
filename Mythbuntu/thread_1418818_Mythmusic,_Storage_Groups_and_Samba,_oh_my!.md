---
title: "Mythmusic, Storage Groups and Samba, oh my!"
date: 2010-03-01
forum: Mythbuntu
---

### Post by TheMiz on 2010-03-01
Hi I am having a difficult time trying to get Mythmusic to work on a remote front end.  Mythmusic works well on the FE/BE system, but not on either remote frontend I have.

I have made Samba shares and mounted them on the Mythbuntu stand alone Frontend and the Mac OX frontend.  I can access the mp3 files on either system (with VLC or some other player) and they will play... just not through mythmusic.

I changed the "Directory to hold music" to reflect the mount points (they are different on either frontend, so I put a colon before the entry.

When I go to mythmusic it will see the files, and it wil say the proper file location, but it will not play them... and ideas/other options?

---

### Post by SiHa on 2010-03-01
> **TheMiz said:**
> 

I changed the "Directory to hold music" to reflect the mount points **(they are different on either frontend**, so I put a colon before the entry.



That might be your problem. I know that for Mythvideo, the mount points should be the same otherwise the metadata gets screwed up.

---

### Post by TheMiz on 2010-03-01
Well,
either that was the problem, or the ":" in front was the problem.

Storage Groups would be awesome... if they worked.

---

### Post by nickrout on 2010-03-01
> **TheMiz said:**
> Well,
either that was the problem, or the ":" in front was the problem.

Storage Groups would be awesome... if they worked.

storage groups do not work on mythmusic (yet). You need the mount point t be the same on each frontend (including any combined fe/be)

Change your mountpoints :)

---

### Post by TheMiz on 2010-03-02
Well, I have it working, and my mount point is the same on my 2 remote frontends.... but my main Frontend/Backend has a different mount point, and Mythmusic, and Mythvideo both seem to be OK.

I have a Mac that I installed Mythfrontend on... I use a script and SAMBA to mount my music and ISO shares from my main FE.  I don't know how to make it run a script and mount it where I want it so it gets mounted at /Volumes/music.  I created a /Volumes directory on my other remote frontend (an Acer Revo) and mount the Samba shares with an edited fstab at /Volumes/music.  On my FE/BE box (a small home-built box with a NVIDIA ION MB) the mount point is still the default /var/lib/mythtv/music.  They all seem to work.

---

