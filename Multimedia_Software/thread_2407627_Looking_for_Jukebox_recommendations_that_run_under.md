---
title: "Looking for Jukebox recommendations that run under server"
date: 2018-12-06
forum: Multimedia Software
---

### Post by jjhudak on 2018-12-06
I run ubuntu server 16.04 LTS that has a LAMP configuration and want to install a jukebox server capability on it.  I dont want to have a self contained app that effectively wipes my current ubuntu config and capabilities.
My  general requirements are:

1. Jukebox sw should have web interface so that I can use tablets, phones, PCs etc to configure and play playlists and random selections, as well as totally control the jukebox.
2. The output of the jukebox would be via the Audio(Speaker) out on the server box.  (an alternative, but secondary config, is to play through a BT port)
3. Streaming capability to other network devices via wired or wireless ethernet is desired, but not necessary for this application.

Thanks for any pointers.

---

### Post by TheFu on 2018-12-06
I'm assuming that "jukebox" means music server.

gnump3, Clementine, cmus, Plex Media Server or almost any DLNA Server.
Clementine has a client/server architecture, but for that to work, fairly recent versions of the client and the server are necessary.

There is also mpd which runs on a server. There must be 20 mpd clients.  I've never used any, but when people setup their $50 ARM-based media server devices connected to a nice stereo, they use mpd.  [https://howtoraspberrypi.com/music-server-raspberry-pi-volumio/](https://howtoraspberrypi.com/music-server-raspberry-pi-volumio/)

cmus is what I use. It is a CLI tool - so I ssh into the server to control the playback, track selections, playlists, everything.  The client devices must support ssh for it to work nicely.

I also use BubbleUPnP on android devices to control DLNA servers, clients and renderers.  Just depends on where I want the music playing.

---

### Post by jjhudak on 2018-12-07
Yes, Jukebox should be interpreted as music server.
Thanks, but client server is not exactly what I had in mind. I'd like the application to serve up web pages for any browser enabled device.
Seems like most of the suggestions provided are C-S architecture.  The CLI just doesn't cut it for mobile devices.
I am still hunting for potential solutions.
J

---

### Post by CatKiller on 2018-12-07
The server *can* be controlled by the command line, but you can put any front end on it that you like. I have volumio on one of my Raspberry Pis.

---

### Post by TheFu on 2018-12-07
**kodi** has a web interface that controls all the media available - music, videos, photos. Playback is local to the kodi system.  I'd forgotten about it, because I don't generally use Kodi through the web interface, but there is one and there are client apps or almost any remote control can be used too.

But I bet volumio would be much lighter.

---

### Post by CatKiller on 2018-12-08
The way volumio works is that you have mpd running, and then volumio is a webserver to interface with mpd through any browser. It offers up pages formatted for a mobile device if you visit it with your phone, and more full-featured pages if you visit it with a desktop browser. It really does seem exactly what you're after.

You could either start a VM with one of the pre-configured environments, or copy just the webserver configuration for your normal environment. Either should work fine.

Otherwise, there are a bunch of other mpd front ends for a whole bunch of different platforms, as already mentioned.

---

### Post by CatKiller on 2018-12-09
Wow. My Pi has just been sitting there as an appliance since about the time that volumio was first released. This thread enticed me to put on a newer version, and it's *way* more slick than it was.

Thank you for that, jjhudak. I hope you find what you're looking for.

---

### Post by nik.charles on 2018-12-20
not sure if this is what you need:

[Cherrymusic]("http://fomori.org/cherrymusic") - standalone HTML5 (with flash fallback) music server

---

