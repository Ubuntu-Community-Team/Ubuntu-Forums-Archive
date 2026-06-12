---
title: "minidlna not working properly on my headless precise pangolin server"
date: 2012-12-01
forum: Multimedia Software
---

### Post by mathgirl on 2012-12-01
I have two DLNA servers, one that came built into my router (SSID_MediaMover) and the other is my server running minidlna (JBs DLNA server). The former shows up on a PS3 and the latter doesn't. The closest I can get to seeing a difference is by mounting them with djmount. Everything looks fine on JBs DLNA server, but the moment I try to play a file, the connection is dropped.

Here's my [/etc/minidlna.conf]("http://paste.ubuntu.com/1384201/")

Here's what happens when I try to use djmount:
```

root@localmachine:/home/username# djmount upnp
[I] Charset : successfully initialised charset='UTF-8'
root@localmachine:/home/username# cd upnp
root@localmachine:/home/username/upnp# ls
devices  JBs DLNA server  SSID_MediaMover
root@localmachine:/home/username/upnp# cd SSID_MediaMover/
root@localmachine:/home/username/upnp/SSID_MediaMover# ls
_search
root@localmachine:/home/username/upnp/SSID_MediaMover# cd _search/
root@localmachine:/home/username/upnp/SSID_MediaMover/_search# ls
search_capabilities  search_help.txt
root@localmachine:/home/username/upnp/SSID_MediaMover/_search# file search_help.txt 
search_help.txt: ASCII text
root@localmachine:/home/username/upnp/SSID_MediaMover/_search# cd ../../JBs\ DLNA\ server/
root@localmachine:/home/username/upnp/JBs DLNA server# ls
Browse Folders  Music  Pictures  Video
root@localmachine:/home/username/upnp/JBs DLNA server# cd Music/
root@localmachine:/home/username/upnp/JBs DLNA server/Music# ls
Album  All Music  Artist  Folders  Genre  Playlists
root@localmachine:/home/username/upnp/JBs DLNA server/Music# cd All\ Music/
root@localmachine:/home/username/upnp/JBs DLNA server/Music/All Music# ls
Etude no. 10.mp3  Etude no. 2.mp3  Etude no. 4.mp3  Etude no. 6.mp3  Etude no. 8.mp3
Etude no. 1.mp3   Etude no. 3.mp3  Etude no. 5.mp3  Etude no. 7.mp3  Etude no. 9.mp3
root@localmachine:/home/username/upnp/JBs DLNA server/Music/All Music# file Etude\ no.\ 1.mp3
Etude no. 1.mp3: ERROR: cannot read `Etude no. 1.mp3' (Transport endpoint is not connected)
root@localmachine:/home/username/upnp/JBs DLNA server/Music/All Music# ls
ls: cannot open directory .: Transport endpoint is not connected
root@localmachine:/home/username/upnp/JBs DLNA server/Music/All Music# cd ..
root@localmachine:/home/username/upnp/JBs DLNA server/Music# ls
ls: cannot open directory .: Transport endpoint is not connected
root@localmachine:/home/username/upnp/JBs DLNA server/Music# cd ..
root@localmachine:/home/username/upnp/JBs DLNA server# ls
ls: cannot open directory .: Transport endpoint is not connected
root@localmachine:/home/username/upnp/JBs DLNA server# pwd
/home/username/upnp/JBs DLNA server
root@localmachine:/home/username/upnp/JBs DLNA server# cd ..
root@localmachine:/home/username/upnp# ls
ls: cannot open directory .: Transport endpoint is not connected
root@localmachine:/home/username/upnp# ls
ls: cannot open directory .: Transport endpoint is not connected
root@localmachine:/home/username/upnp#

```

---

