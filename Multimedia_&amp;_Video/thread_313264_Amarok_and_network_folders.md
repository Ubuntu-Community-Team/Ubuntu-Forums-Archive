---
title: "Amarok and network folders"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by deadspeak on 2006-12-05
i'm currently trying to set up amarok in edgy, but all my music is on a windows networked drive that i use to store all my media. when i go to build my collection, the networked folders are nit in the folder tree, now i've mounted my drives by going into places and connect to server, then navigated to the drive right clicked and connected to the server, the icon as appered on my desktop and i can access it quite happyly by double clicking. if i use rythm box the folders do appear in the folder tree, but no in amarok.

Hope someone can help
cheers

---

### Post by Cryptic1911 on 2006-12-06
I had a problem with this last night actually.. I wasn't using a windows server though, so I had permission issues as well as not being able to browse through amarok to it. Anyways, to fix my problem I had to mount the smb share to a folder with a command like this:

mount -t smbfs -o username=blahblah,password=blahblah,workgroup=blahblah //server/folder /mountpath

in my case I also had to have fmask=777,dmask777 to allow me write access.. otherwise it mounted in readonly mode.

One other thing too is that I later added an entry into the /etc/fstab folder with that same info (formatted properly for fstab of course) and now it automounts on bootup, and also creates the desktop link. With /srv mounted to my server, I can browse it with amarok now.

---

