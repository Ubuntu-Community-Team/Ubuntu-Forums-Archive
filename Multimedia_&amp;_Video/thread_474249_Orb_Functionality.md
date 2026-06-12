---
title: "Orb Functionality?"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by ericbarch on 2007-06-14
I'm looking for a program somewhat similar to Orb for Linux. I'd like to be able to access all of my XviD/FLAC files wherever I'm at. I'm not sure if transcoding would be possible, but it would be great. Does anyone have any recommendations for programs similar to Orb or any ideas on how to stream XviD/FLAC? I am using a Mac as the client end.

---

### Post by dreadlord_chris on 2007-06-14
> **ericbarch said:**
> I'm looking for a program somewhat similar to Orb for Linux. I'd like to be able to access all of my XviD/FLAC files wherever I'm at. I'm not sure if transcoding would be possible, but it would be great. Does anyone have any recommendations for programs similar to Orb or any ideas on how to stream XviD/FLAC? I am using a Mac as the client end.

I do believe that VLC (Video LAN Client) can handle your streaming needs

---

### Post by ericbarch on 2007-06-14
VLC doesn't quite seem to be what I need. The server system has no GUI and I'd like to be able to stream my media over the Internet and select what I want to watch/hear from a menu and have it transcode on the fly.

---

### Post by ericbarch on 2008-01-22
Just a follow up on this for anyone who is curious...it seems that if you compile VLC with mp3 support:

[http://www.torrentflux.com/forum/index.php?topic=1984.15](http://www.torrentflux.com/forum/index.php?topic=1984.15)

It provides an excellent way to transcode and stream video (XviD/DivX included) to anywhere, even over a slow cable modem. The best way I've found to do this is from TorrentFlux b4rt, which doubles as a nice web-based file/torrent download manager:

[http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/)

For audio streaming capabilities, try checking out Ampache:

[http://www.ampache.org/](http://www.ampache.org/)

For file sharing I just setup an SSH server and use an SFTP client to access all my files from anywhere.

Using these techniques I've come very close to getting Orb like functionality without the need for Windows or Orb and completely open source. Hope this helps.

---

