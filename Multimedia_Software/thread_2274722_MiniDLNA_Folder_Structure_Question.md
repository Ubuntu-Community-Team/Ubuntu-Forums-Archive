---
title: "MiniDLNA Folder Structure Question"
date: 2015-04-21
forum: Multimedia Software
---

### Post by Mirnesc92 on 2015-04-21
Hello,

I have two external USB hard drives connected to an Ubuntu Server (14.04.1) running miniDLNA. I have managed to install and configure everything to work properly; however, I would like to know if it is possible to change the default folder structure which is viewed on the client end..

I have 5.00 TB of video files split across two drives (2TB/3TB). When I open miniDLNA from client side, these two drives each have their own folder because I imported them that way in the minidlna.conf file.[INDENT]
media_dir=V,/media/[COLOR=#00ff00]sdc[/COLOR]/Movies
media_dir=V,/media/[COLOR=#ff0000]sdb[/COLOR]/Movies
media_dir=V,/media/[COLOR=#ff0000]sdb[/COLOR]/Shows
media_dir=V,/media/[COLOR=#ff0000]sdb[/COLOR]/Anime
media_dir=A,/media/[COLOR=#ff0000]sdb[/COLOR]/Music
media_dir=P,/media/[COLOR=#ff0000]sdb[/COLOR]/Photos
[/INDENT]

This creates the following directories under "Video" when being viewed from say for example my ipad (app called "Infuse").[INDENT]
Anime
Movies
Movies
Shows


[/INDENT]
I read somewhere on the forum that creating 'symbolic links' using 'ln -s source destination' will help organize the folders better. So I created a directory and put sym links in it using..
```

ln -s /media/sdb/Movies 3TB
ln -s /media/sdc/Movies 2TB

```
..and then changing the minidlna.conf file to..[INDENT]
media_dir=V,/media/[COLOR=#40e0d0]sdm[/COLOR]/Movies
media_dir=V,/media/[COLOR=#ff0000]sdb[/COLOR]/Shows
media_dir=V,/media/[COLOR=#ff0000]sdb[/COLOR]/Anime
media_dir=A,/media/[COLOR=#ff0000]sdb[/COLOR]/Music
media_dir=P,/media/[COLOR=#ff0000]sdb[/COLOR]/Photos
[/INDENT]


It gets rid of the double occurrence of Movies but still splits the drives up into two folders inside that directory...


[[IMG]http://i.imgur.com/K7pNv4Js.png[/IMG]]("http://imgur.com/K7pNv4J")
[[IMG]http://i.imgur.com/XRTOVIfs.png[/IMG]]("http://imgur.com/XRTOVIf")
[[IMG]http://i.imgur.com/edN8Vk9s.png[/IMG]]("http://imgur.com/edN8Vk9")
[[IMG]http://i.imgur.com/Mm0iJgHs.png[/IMG]]("http://imgur.com/Mm0iJgH")

Does anyone know how I can merge these two folders in one folder? ..without using the "Browse All" folder which will flood the results with all sorts of videos in really long list

---

