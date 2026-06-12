---
title: "How can I browse/download/stream PC files over wifi from android phone?"
date: 2014-07-04
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Ashfaqur Rahman on 2014-07-04
I have an android phone. I have lots of music/videos/movies in my PC. It would be very helpful if I could download/stream them from my android phone via wifi when I need them and I don't want to transfer them via cable. I have done some google search. Found some apps but they are basically for streaming or transferring files from android to PC. But I want the opposite. Any HOWTO/documents will be appreciated, thanks.

My android version is 4.2.2 and its not rooted.

---

### Post by SeijiSensei on 2014-07-04
I haven't yet found any method to avoid actually transferring the files to the phone.  Unless you have a rooted device, you cannot mount, say, an NFS server into the filesystem.  If you use an SMB client like AndSMB and Samba on the Linux box, the file will be transferred, not played as a stream.

I haven't tried using DLNA though.  There are DLNA clients like [this one](https://play.google.com/store/apps/details?id=com.dbapp.android.mediahouse&hl=en).  On the server there is software like [ps3mediaserver]("https://help.ubuntu.com/community/Ps3MediaServer").  If you can get DLNA to work, please report back.

---

### Post by coldraven on 2014-07-05
A friend installed MXPlayer onto my Moto G. It has an option "Network Stream" so I guess that if you run some sort of media streamer on your PC it would connect to it.
VLC has a "Stream to Network" option but I have not figured out how to set it up :(
If you succeed then let me know!
[http://www.videolan.org/doc/streaming-howto/en/ch02.html](http://www.videolan.org/doc/streaming-howto/en/ch02.html)

---

