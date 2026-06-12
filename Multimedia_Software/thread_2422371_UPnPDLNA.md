---
title: "UPnP/DLNA"
date: 2019-07-06
forum: Multimedia Software
---

### Post by janne-m-boman on 2019-07-06
Hello
can someone point me towards a idiotproof guide to setup UPnP/DLNA on my ubuntu server so that I can connect to it from PS4, TV, etc clients?
I tried MiniDLNA, but I ended up in endless troubleshooting and "nothing works".... (yes I RTFM'd, etc...)
Basically, I'm a UPnP/DLNA noob with a very short attention span.
Thanks

---

### Post by TheFu on 2019-07-06
"idiotproof" is impossible. We've been taught that no matter how simple something is, $deity will always make someone who doesn't understand.  Earlier today, it was me trying to get something working. After 30 minutes, I gave up. This was the 3rd attempt over the last 4 yrs where I failed.

miniDLNA is pretty simple.  Did you open the firewall ports it needs and tell it to scan/update the media location you specified?  The only trick I know with miniDLNA is that we have to manually tell it to update the library after changes.  Be certain that miniDLNA isn't installed as a Snap.  Use the normal package so it can access your media files (which you must configure), regardless of where they are stored.

All the other solutions are much more complicated.  UPnP is **very** different from DLNA, though some clients seem to mix the names, incorrectly.
I use Plex Media Server for my DLNA server. It is a hog and it is NOT F/LOSS, so I'd rather use something else, but it is very capable and popular. The only tricks with it is to
a) leave enough room in /var/lib/plex* to hold all the images, metadata, DBs, and other cruft outside the actual media files
b) allow port 43200/tcp inbound for the plexserver website in the plex machine firewall
c) visit http://{LAN-IP}:32400/web from your browser and work through all the config options. Mainly, just touch the library directory locations.
d) Split and organize your content correctly - Music, Movies, TV, Pictures ....   There are specific directory layouts for each.  Plex Server and Kodi follow the same directory layout for media files.
e) Allow at least read-only access to the media files you want Plex to serve.
Of course, you'll need to have DLNA "renderers" and a "client/controller" to work with the server and renderer.  

VLC has a DLNA client/render, but it has been flaky until v3.x.  Look under Tools/Playlists.
Kodi is a nice DLNA client+renderer.
On Android, I use BubbleUPnP for the controller and renderer - mixing and matching that to control Kodi on different players around the house.

I have the free BubbleUPnP app installed and no Plex accounts at all.

Is that idiotproof enough?

---

### Post by SeijiSensei on 2019-07-06
Other than adding the appropriate directory list to minidlna.conf, I haven't had to do anything else to see the server from a variety of clients.

The server and the clients all share the same network subnet, right? Are you using a firewall that blocks access from those local machines?

---

