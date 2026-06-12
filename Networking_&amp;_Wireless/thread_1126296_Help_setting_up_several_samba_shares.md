---
title: "Help setting up several samba shares"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Ankhwatcher on 2009-04-15
Hi there.

I use my Ubuntu Server as a media server for my network.

I would like to have it set up thusly:

[I]A Media_Library folder that houses all of my media is shared (read only) with my network.
Media_Library is also shared under password protection so I can edit my files, send over freshly ripped music etc.

Media_Library also exists as a UPNP server that my Xbox360 and any other UPNP devices can connect to.

A Backup folder is also shared with password protection so I can backup my pc to it.[/I]

I've been able to set up some of this, but I'm having trouble with samba, and ushare is bugging me.

thanks in advance,
Ankhwatcher

---

### Post by dmizer on 2009-04-16
For UpNP, you'll need a different server. [MythTV](https://help.ubuntu.com/community/MythTV) will do it.

For the rest of your share configurations, please see the first link in my sig. Once you get it set up with password access, then post back here and I'll help you include password free RO access for the Media_Library folder.

---

### Post by uncle-c on 2009-04-16
Excellent samba / files sharing HOWTOS dmizer. I also found the "Samba-3 by Example"  from the samba.org website very useful.

---

### Post by Ankhwatcher on 2009-06-25
Here is what I worked out:

In order to share /media_library with my LAN as a read only, but also be able to edit files and add to it; I created two shares.

Firstly I added this to /etc/samba/smb.conf
```
[media_control]
   comment = Editing and Control for Zubuntu Media Library
   path = /media_library
   guest ok = no
   read only = no
   create mask = 0777
   directory mask = 0777


[media_library]
   comment = Media Library on Zubunt
   path = /media_library
   guest ok = yes
   browseable = yes
   read only = yes
   create mask = 0600
   directory mask = 0700
```

Then I ran:
```
sudo chown -R username:username /media_library
```
which gave me ownership of /media_library

Finally I restarted samba with:
```
sudo /etc/init.d/samba restart
```

---

