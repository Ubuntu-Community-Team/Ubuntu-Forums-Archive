---
title: "[SOLVED] MP3 Repository"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Mizutsuki on 2007-11-07
I'm in an interesting position, and I'm not sure if anyone else has really had this same sort of problem, but I'm here with an open mind and I'm looking for creative solutions.

I have a web/file server at home (ubuntu server edgy.)  I have an xBox with XBMC on it at home.  I have a laptop that goes with me wherever I am.  I have an MP3 player with RockBox on it. Finally, I have a computer at work with ubuntu on it.  My problem is this: I would like all of these computers to have access to one centralized repository on MP3s, and I'm not sure how to go about doing this.  The xBox doesn't actually need it's own copy because it can stream from the server.  The work computer has limited bandwidth, so streaming there doesn't sound like a great idea.  The MP3 player obviously can't stream.  So I need to maintain 4 separate identical directories.
My first reaction was that I might use subversion, but this ended up being like swatting a fly with a bazooka.  The whole process is insanely slow for binaries.  Additionally, I don't care at all about the versioning, I just want all of the directories to be the same.  It's unfortunate that that didn't work out, because the idea of being able to commit data from work is highly appealing.  It'd be great if I could contribute data from anywhere.  Also, being able to use svn to instantly tell me if my current directory is off and by how many files and where is really nice.  going 'svn update' and having it sync up my collection was appealing.

So my question is: is there any way to do this with svn, or, if not, is there any way to do this with another piece of software?

Thank you,
Stephen

---

### Post by Lostincyberspace on 2007-11-07
I would set up a file server to hold all of the mp3s and mount it on the other computers. possibly using samba. I don't really know I have never tried yet.

---

### Post by Mizutsuki on 2007-11-07
> **Lostincyberspace said:**
> I would set up a file server to hold all of the mp3s and mount it on the other computers. possibly using samba. I don't really know I have never tried yet.

I'm not sure, are you suggesting accessing the music remotely?  If so, that doesn't address the problem of the MP3 player, since it can't stay connected.
Otherwise you're suggesting I keep local copies, and just use SAMBA/NFS to transfer.  The problem with this is that it doesn't address the problem of concurrency.  All copies of the collection have to be identical.  How would I verify/maintain the collection using this method?
Thanks,
Stephen

---

### Post by jacob01 on 2007-11-07
what's wrong with just having the music on the your computers, xbox, and mp3 player. is it a copyright issue, space issue or you just want your collection on a centralized server that you can access anywhere?

---

### Post by bom28 on 2007-11-07
I think you want to look into rsync.
Although streaming could work, mp3 don't need that much bandwith.

---

### Post by Mizutsuki on 2007-11-07
> **jacob01 said:**
> what's wrong with just having the music on the your computers, xbox, and mp3 player. is it a copyright issue, space issue or you just want your collection on a centralized server that you can access anywhere?
My problem is that my collection is coming from a number of different sources and keeping all of the computer up to date has become a problem in terms of management.  If I add a second CD by an artist I already have a CD from I have to remember that I purchased the CD and then I have to go through and make sure there's a copy on every device, otherwise I forget and two months down the line I'm scratching my head wondering whatever happened to that one CD.

> **bom28 said:**
> I think you want to look into rsync.
Although streaming could work, mp3 don't need that much bandwith.
So far, rsync looks right on the money, thanks.  I'm testing it right now.
The only problem with streaming is that it won't be possible most of the time with the laptop and all of the time with the MP3 player.

Thanks for your help,
Stephen

---

### Post by Mizutsuki on 2007-11-07
Arghhh... well, it looks like because these are binaries (and there are, therefore, no deltas to be made) rsync has decided that every time I want to sync I have to transfer the entire contents of the directory.  Mildly annoying over the home network, an absolute deal-breaker on the work computer (over the Internet and my poor ADSL.)  This is a process I want to be able to execute every time I download a new CD at work and then I'll have it at home after a short check to make sure nothing is changed and then the transfer of the new CD (and only the new CD.)
It seems silly to me that the application wouldn't simply check CRCs to check if they are the same much much faster.  This is beginning to feel like I'm going to have to write this application for myself.
Any other suggestions?

Thank you,
Stephen

---

### Post by Mizutsuki on 2007-11-07
Wait, sorry, I was being crazy.  It turns out that I had selected the wrong directory so it was just copying everything over.  My bad.  This looks just right.  Thanks, all.

---

