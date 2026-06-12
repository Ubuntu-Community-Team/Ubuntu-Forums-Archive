---
title: "Need a New Torrent Client"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by Sugi on 2012-01-25
I need a new torrent client, because my current one, Deluge isn't handling well. It's not allowing the open ports, not handling multiple torrents, stopping my router, and freezing.

I am looking for advice on a good bittorent client, that can
 - handle multiple torrents
 - handle mass adding [one click to add like 30 torrents]
 - access my open ports / just work [because most do! utorrent does on my win box]
 - not freeze!

I have reviewed this site, can any of these do this list?
Deluge
Transmission
qBittorrent
Ktorrent
Vuze Client
[http://www.techdrivein.com/2011/01/top-5-bit-torrent-clients-for-ubuntu.html](http://www.techdrivein.com/2011/01/top-5-bit-torrent-clients-for-ubuntu.html)

My Deluge:
Ubuntu 10.10
Client: 1.3.3
Libtorrent: 0.15.8.0

Deluge Stopping Router:
[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=29565](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=29565)

Deluge Freezing:
[http://ubuntuforums.org/showthread.php?t=1838935](http://ubuntuforums.org/showthread.php?t=1838935)

Deluge Not Seeding Torrents:
[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=36695](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=36695)

---

### Post by kerry_s on 2012-01-25
transmissions always worked for me. just need to uncheck nat-pmp which has been broke forever.
for the mass download just setup a watch folder & copy the torrent files there. 
for the port, as long as you setup forwarding on your router right, should be good to go.
as for freezing make sure you adjust for what your router can handle, for example i know mine dies at 300, so i always throttle it at 250 down.

---

### Post by Sugi on 2012-01-26
I use to use transmission on opensuse, and I remember it was quite good.  Though, wasn't it handle to manage lots of torrents with the large text for each torrent file?

---

### Post by pierreyy on 2012-01-26
do you have a firewall enabled? if you do maybe you should check your settings.

if that isnt the problem then you can open the software center and you will find plenty of choices, good luck!

---

### Post by TeoBigusGeekus on 2012-01-26
I use rtorrent.
A bit daunting at the beginning (it's a CLI app after all) but I wouldn't change it for anything.
Even with 5 or 10 torrents of over 20gb each, it does its job without complaints.

---

### Post by Sugi on 2012-01-26
pierreyy, It's not firewall / router related, because it will randomly accept or deny the ports it's suggested or the one's I open.  It's very strange, and it works when it wants.

TeoBigusGeekus, thanks for the suggestion, although,

Does anyone know if any torrent client sort or organize torrents by groups or tracker?

---

### Post by cbanakis on 2012-01-26
I use vuze.

I have not tried any others, but it seems to work well.

TONS of setup options for firewall, bandwidth limiting, etc.

---

### Post by pyroscope on 2012-01-27
If you want to organize by tracker, ruTorrent has autolabel / automove plugins. Or you use my distribution of rTorrent, which has a tracker view, and allows dynamic completion moving.

[http://code.google.com/p/pyroscope/wiki/RtorrentExtendedCanvas#Extended_canvas_explained](http://code.google.com/p/pyroscope/wiki/RtorrentExtendedCanvas#Extended_canvas_explained)
[http://code.google.com/p/pyroscope/wiki/RtControlExamples#Move_on_Completion](http://code.google.com/p/pyroscope/wiki/RtControlExamples#Move_on_Completion)

---

