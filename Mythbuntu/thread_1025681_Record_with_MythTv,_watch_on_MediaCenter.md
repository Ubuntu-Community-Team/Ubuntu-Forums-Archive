---
title: "Record with MythTv, watch on MediaCenter"
date: 2008-12-30
forum: Mythbuntu
---

### Post by abuthemagician on 2008-12-30
I really want to use MythTv as both a front end and backend system, but my wife has insisted that she needs to use the computer for windows related tasks as well, such as organizing photos, using a webcam to talk with her sister, etc. Is it possible to setup a MythTv frontend backend that will record shows then dump them in a shared folder on a server in xvid format? That would be awesome. I have seen that it has a web interface to setup record times but any other info would be great

---

### Post by newlinux on 2008-12-30
You could use mythtvplayer, or just setup your storage directory as a network share (most recording type by default are mpeg-2, but you could setup automatic transcoding if you really need to) using SAMBA/CIFS. You would probably want to use mythrename.pl to give the recordings usable filenames.

[http://www.sudu.dk/mythtvplayer/index.php](http://www.sudu.dk/mythtvplayer/index.php)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.mythtv.org/wiki/index.php/Mythrename.pl](http://www.mythtv.org/wiki/index.php/Mythrename.pl)

---

### Post by freymann on 2008-12-30
> **abuthemagician said:**
> I really want to use MythTv as both a front end and backend system, but my wife has insisted that she needs to use the computer for windows related tasks as well, such as organizing photos, using a webcam to talk with her sister, etc. Is it possible to setup a MythTv frontend backend that will record shows then dump them in a shared folder on a server in xvid format? That would be awesome. I have seen that it has a web interface to setup record times but any other info would be great

I'd vote for the windows mythtvplayer program too. It works well, it skips commercials, and it installs and works ever so simply.

Otherwise, get a barebones box and use that to feed the TV and drop free up the windoze box completely!

---

### Post by abuthemagician on 2008-12-30
thanks for the suggestions, especially the MythTv viewer. I will use that to watch shows and the web interface to schedual recordings. I doubt i will do the conversions though unless i am recording an episode for my inlaws. 

So I can setup a backend only?

---

### Post by newlinux on 2008-12-30
Probably can just setup a backend, although some settings can only be entered from the frontend. Off the top of my head, if all you want to do is view recordings with the windows viewer I think you'd only need to setup the backend and tuners and use mythweb to schedule recordings...

---

