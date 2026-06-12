---
title: "Split Uploads"
date: 2013-09-15
forum: Multimedia Software
---

### Post by Geoff_Lane on 2013-09-15
Folks,

I would like to transfer a particular DVD over the internet.

Rather than one huge iso file I'd like transfer smaller chunks.

The intention is to upload the VOB files individually but is there any way of playing them automatically rather than as 4 separate files.

Geffers

---

### Post by TheFu on 2013-09-15
The way that usenet has done this works well.  I'm certain there is an automatic way, but I only know the manual method.  Use split/join to .... split the devices, use rsync to transmit them and use join on the other side to rejoin all the files.  4M is a good size for each chunk to be transferred.  Forget about playing them automatically on the other side ... at least as long as you have them as VOB or split.

Most places would transcode the VOB files into a single xvid/avi or h.264/mp4 or flv before attempting to split/transmit/join them. There is a 3:1 ratio of size reduction with the transcoding, so the transmission should be 2/3 faster than VOB files.

Another option is to run a private bittorrent server and tracker for the other person, but with just 2 machines, there really isn't much to be gained.

rsync is probably the best transfer tool for this and will work over an encrypted ssh tunnel of you setup ssh between the 2 machines.

---

