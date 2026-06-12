---
title: "Centralized metadata search system?"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by cybertoast on 2007-11-10
I work at a radio station (kruufm.com) and we're running into a bit of a problem as we collect a greater and greater repository of music. We have all the music as mp3 and ogg on a central server that all the hosts at the station can connect to. The files are served up via nfs mounts.

The problem is an efficient and usable search engine that can easily get at the files, and allow creation of playlists, previews, etc.

Basically what's necessary is an Amarok server which can be managed by web-based clients. I've done quite a few searches on freshmeat, sourceforge and the wider net and am able to find a lot of client solutions, but almost no server solutions. Wonder if anyone can provide suggestions?

The requirements are:
* Database that contains all the mp3/ogg/flac/ etc. metadata and the corresponding file location
* Database should update itself upon addition of any new files. New files might be added through any client on the network (CD ripped and file added to the NFS mount)
* Search should be possible from any machine on the network. But this could either be a client app or web-based.
* It should be possible to put the search results into a playlist, and to preview the tracks
* The meta-data should be updateable by users - basically the database should allow comments, rating, notes (eg. explicit lyrics) by any user. Sort of a wiki for each track. Obviously search should allow the flexibility to search this meta-comment as well as tag info if necessary

I'm leaning in favor of building my own solution, but given the excellent Tracker project and so many metadata database systems (ampache, jinzora, amarok, etc.) I'm wondering if there's already something that does what I need and I just have not found it.

Anyway, I'd greatly appreciate any suggestions to this problem.

---

