---
title: "media server - with web interface?"
date: 2015-01-23
forum: Multimedia Software
---

### Post by Tommy_Maersk on 2015-01-23
Hey
I got a ubuntu computer, that right now is set up with samba to share my media files across my home network - however I am interested in some sort of webinterface so that I from my various windows and linux machines at home, can access my media files from some sort of cool webinterface - is there something like that around?

Thanks

---

### Post by TheFu on 2015-01-23
Plex Server.

It has a web interface, but that really isn't how to use it. It is also a DLNA server, so any DLNA client can access the media - android, lunix, windows, chromecast, roku, vlc, ..... BR players, smart TVs .... there is a plex client application for most OSes. I've never used it.  My HTPC has XBMC on it, uses the PlexBMC addon to access the plex server.  On android, I use bubble UPnP.

Bonehead to setup, provided you follow the media layout requirements. Point at the web-admin page to allow local LAN access and that's it. I don't have a plex account, but most people will. No need of you don't want to access your media over the internet.

---

### Post by Tommy_Maersk on 2015-01-24
Hey

Thanks, I have already looked and tryed Plex - but it wont let me add anything, guess its because the naming of my media files isnt what plex excepts - and dont wanna go rename 1000s of files

---

### Post by TheFu on 2015-01-24
You can tell Plex Server to ignore metadata and treat your media as plain videos. Any file in the subdirectory of the "videos" will be seen, usually in just a few minutes. The web interface will show those new files too.

All the media servers have the file-naming and directory-type requirement if you want metadata to be automatically pulled in.

I don't know of any web-interface media servers that allow media upload through the web. This is because doing large file uploads over the web is a terrible design and prone to timeouts or other disruption. Use NFS or CIFS to drop files onto your Ubuntu media directories.

Or you can write your own solution.  Creating a webpage from a list of files inside a directory isn't too hard.  Could be a fun exercise. After all, Linux/Unix is designed to make end-user scripting easy.

---

### Post by Tommy_Maersk on 2015-01-24
How do I tell Plex to ignore meta data, and just list the media as is?

Okay found out it is not a metadata problem, but a permission problem, as all my media is on external harddrives

---

### Post by TheFu on 2015-01-24
Solved?  Plex just needs read access to the directories and files.

---

