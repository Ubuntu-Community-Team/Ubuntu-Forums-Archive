---
title: "Upnp Photos wont display in Windows Media Player"
date: 2012-02-05
forum: Mythbuntu
---

### Post by jdroflet on 2012-02-05
Ubuntu 11.10 with Mythtv 0.24 FE/BE
HVR-1600

From Windows 7, Windows Media Player 12 I can browse and play Music/Videos and Recordings from the Mythbox.

But no photos come up I select pictures.

User rights and directory settings appear correct. Pictures come up in Myth frontend.
Same goes for my older Mythbuntu running 0.21

Any ideas?
Thanks,
John

---

### Post by jdroflet on 2012-02-07
3 days of google on this and nothing yet :( 

I loaded xbmc on a pc and it is the same result: Xbmc can see and add and play Recordings, Video and Music over upnp but attempting to Browse  for Pictures only displays the 3 above folders on the system and not pictures.

I've tried going back to the default option of /var/lib/mythtv/pictures/ in the setup but still nothing.

I see the same results on my old Mythbuntu 021 box. 

[SIZE="2"]Could someone please confirm that viewing pictures with a Upnp client actualy works in Mythtv???[/SIZE]

 mythbackend --upnprebuild
2012-02-07 21:52:38.947 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2012-02-07 21:52:38.947 Using runtime prefix = /usr
2012-02-07 21:52:38.947 Using configuration directory = /root/.mythtv
2012-02-07 21:52:38.947 Empty LocalHostName.
2012-02-07 21:52:38.947 Using localhost value of NAS2
2012-02-07 21:52:38.950 New DB connection, total: 1
2012-02-07 21:52:38.953 Connected to database 'mythconverg' at host: 127.0.0.1
2012-02-07 21:52:38.954 Closing DB connection named 'DBManager0'
2012-02-07 21:52:38.955 Connected to database 'mythconverg' at host: 127.0.0.1
2012-02-07 21:52:38.955 Current locale en_CA
2012-02-07 21:52:38.955 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2012-02-07 21:52:38.960 Rebuilding UPNP Media Map
2012-02-07 21:52:38.961 Enabling Upnpmedia rebuild thread.
2012-02-07 21:52:38.961 New DB connection, total: 2
2012-02-07 21:52:38.961 Connected to database 'mythconverg' at host: 127.0.0.1
2012-02-07 21:52:38.962 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/data2/mythtv/videos:
2012-02-07 21:52:38.963 UPnpMedia: BuildMediaMap Done. Found 1 objects

Thanks,
John

---

### Post by nickrout on 2012-02-08
Don't **shout.**

If you are not getting an answer here then go to the primary source for mythtv support - the mythtv-users mailing list.

---

### Post by mikulator on 2012-02-08
MythGallary is an add-on to the FE and not the BE thats why you don't see it through Upnp

---

### Post by nickrout on 2012-02-08
> **mikulator said:**
> MythGallary is an add-on to the FE and not the BE thats why you don't see it through Upnp

I am not sure that is logical. mythvideo is also a frontend addon, but you can see videos in upnp.

---

### Post by jdroflet on 2012-02-09
> **nickrout said:**
> Don't **shout.**

If you are not getting an answer here then go to the primary source for mythtv support - the mythtv-users mailing list.

Sorry, intent was not shouting. Was just hoping to catch the eye of someone who was just skimming through. 
Yes, I've asked over at the primary source.
Thx,
John.

---

