---
title: "Media/File server for the home"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by bthessel on 2007-03-07
OK, I have my old pc: Athlon 2600, 1 GB of Ram, 2 x 200 GB IDE, 2 x 250 GB Sata drives. I want to build a server I can leave on in a closet to store video, MP3's and pictures and also act a home file server. Connect with two windows laptops, a windows desktop, a Ubuntu laptop. Need to be able to sync a Zen vision M from the media. Would like to be able to stream to a laptop that is hooked to a TV/Audio system occasionally. 

Looking for recommendations on software to accomplish this the best. I would like to mirror data if possible for protection.

---

### Post by jinx099 on 2007-03-07
I've been doing this exact same thing for a while now with opensuse, but Ubuntu would work just fine as well.  Just be sure to install SSH before you dump it in the closet :)

You can use samba to share files with windows and NFS to share files with linux.  This is how I do it.  For the streaming, you dont really need to stream the A/V, you can just use samba/NFS and play the files like they were local.  If you really want to stream, you can use VLC, but I beleive you'll have to leave it running on a VNC session on the server.

For RAID, you can use linux software RAID.  This is what I use and its worked great.  I was confused at first with it because it RAIDs partitions rather than drives.  So you have to make RAID partitons on the drives, and then create the array with whatever partitons you choose, and then create a filesystem on the array.

good luck!

---

### Post by Aberrix on 2007-03-09
[FreeNAS]("http://www.freenas.org")

---

