---
title: "Multimedia and UPnP"
date: 2009-08-30
forum: Multimedia Software
---

### Post by Hozza on 2009-08-30
Hi,

me and my house mate have got a collection of 23GiB of music :D 

so it is impractical to have a copy of all the music on every computer in the house.

We decided we needed a media server for all the music, videos and pictures. I did some research and came across a Daap server (music sharing server similar to iTunes shop [http://www.fireflymediaserver.org/]("http://www.fireflymediaserver.org/")). This was good but did not support the videos and we would have to connect to the ip address and port number everytime we opened Rythembox. (not good)

so... i came across UPnP [http://en.wikipedia.org/wiki/Universal_Plug_and_Play]("http://en.wikipedia.org/wiki/Universal_Plug_and_Play"). Then i came across in Linux Format Mag a UPnP server guide (this server will serve video, music and pictures). The program is called MediaTomb.


I got it installed and all working. i then when to install the python-coherence app to allow the UPnP plugin in Rythem box to install and be usable and then the totem-plugins-extra app to alow the UPnP plugin in totem (Movie Player) box to install and be usable.

It all works but in both totem and rythembox it shows 2 MediaTomb servers one with just a folder called PC Directory and no files and the other with all the media in it.

why does it show 2 mediatomb servers and is there a way to fix it?

thanks for any help


p.s. if anyone have any better media server ideas please let me know.

---

### Post by AndyCee on 2009-09-06
This may be a stupid question, but on your server if you type:

```

ps -A | grep mediatomb

```

Do you have only one or two servers running?

---

### Post by Hozza on 2009-09-06
Ah, no I haven't tryed that yet.I will the second I get home

---

