---
title: "Backend &amp; FileServer"
date: 2007-11-18
forum: Mythbuntu
---

### Post by Stevieo85 on 2007-11-18
Hi guys,

I'm in the process of setting up Mythbuntu for the first time to use seriously. I have the backend server set up and the frontend set up on another box. What I am wandering is how should the music and videos and images etc sections be set up on the front end?

Basically I want to use the backend to store all my media, do I just have to share the drives using NFS then mount them on the frontend and set myth... to point to the mounted point or is there a way on the backend to say here is where music is stored and the frontend picks it up? 

I am wandering this as I will soon be building my second front end and want it set up properly rather than having each front end scan for music and store its own database of music if it can access a central database.

Hope this makes some kind of sense.

---

### Post by uopjohnson on 2007-11-18
This is kind of an oddity of myth becuase mythmusic and mythvideo don't stream content the way the core does.  You need to share your music/video location as an NFS share and then mount it on the frontend. Each frontend uses the central db for info about the files, but they need to have their own local mount point.  I have my backedn setup with /storage/recordings, /storage/media/video /storage/media/music I then export /storage/media over NFS and mount it as /mnt/media on each frontend. 
Seems to work well.

---

### Post by Stevieo85 on 2007-11-20
Thanks for that info. So will both front ends use the same data for mythmusic and mythimages or does it store the data twice? In essence if i update the music and scan on one box does the other box pick up the changes when I next go into mythmusic on that?

This maybe should go in a different thread if so let me know but is there a way to comeout of mythmusic and continue to have the music playing whilst i look at images? I have googled and can;t find very much about this.


Cheers,

Steven

---

### Post by newlinux on 2007-11-20
They use the same data. An update on one box will update them all. Just make sure the mount points are the same on all frontends.

I don't use mythmusic much (I find the interface to be annoying and I just use amarok - I wip out the wireless keyboard) due to it's poor playlist implementation (specifically the lack of an easy way to import playlists) so I can't help much with that - but that would be a good feature.

---

### Post by uopjohnson on 2007-11-20
I think that is probably one of the most requested features of mythmusic, but there  is no way to do it right now.  There have been several calls for mythmusic developers on the mythtv lists and I think there is some really good activity going on currently, maybe this will make the cut.

---

