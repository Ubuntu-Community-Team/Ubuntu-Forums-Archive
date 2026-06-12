---
title: "Samba Share doesn't automount as file system after updates"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-01-26
I finally left the stone age and updated my Ubuntu 7.04 laptop to 8.04, and probably to 8.10 sometime soon. Everything is working fine so far, except for my samba shares. Under 7.04, I had them automounting as network drives, i.e. they showed up as if they were hard disks in the menus. I kept my /etc/fstab the same as it was with 7.04, so those entries should be accurate. Additionally, if I follow the path to the local folder where the shares mount, I can access them that way; they just don't show up as drives anymore, which means that I can't really save anything to them from other programs (they mount to a folder in the root filesystem at /remote/blackdiamond/ ).

Here is are the relevant lines from my /etc/fstab:
```
//192.168.2.2/dan /remote/blackdiamond/files cifs username=dan,password=xxxxxx 0 0
//192.168.2.2/brandesky20 /remote/blackdiamond/brandesky20 cifs username=dan,password=xxxxxx 0 0
```

Any suggestions on how I can get this back? Thanks!

-Dan

---

### Post by dmizer on 2009-01-26
Have you tried browsing to these share directories with Nautilus. It may be that the shares are mounting, but simply not creating the shortucuts in your menu.

---

### Post by dbsoundman on 2009-01-26
That is what it's doing. I also found that whatever problem there was in 7.04 with Amarok not being able to access those drives from the root folder is no longer a problem. So basically I'm just whining about the lack of conveniently-placed shortcuts...

-Dan

---

### Post by dmizer on 2009-01-26
> **dbsoundman said:**
> That is what it's doing. I also found that whatever problem there was in 7.04 with Amarok not being able to access those drives from the root folder is no longer a problem. So basically I'm just whining about the lack of conveniently-placed shortcuts...

-Dan

So just drag the folders over to the left pane to make a bookmark. I believe the same is true for the Desktop.

Also, if you mount in /media instead of /remote, the shortcuts will be made automatically.

---

