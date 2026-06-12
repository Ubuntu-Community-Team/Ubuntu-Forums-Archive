---
title: "ltsp client mounting webdav folder"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by miguel.antonio.168 on 2010-03-05
[SIZE=3][FONT=Arial]need help on configuring our ltsp server so that each client station will have it's own copy of _/etc/fstab_ that contains entry for webdav mounting to user specific folder under it's own home directory. below will be the [COLOR=Sienna]***suppose entry***[/COLOR]:[/FONT][/SIZE][B][SIZE=2][FONT=Arial]

   [COLOR=Sienna]*[http://host/webdav_folder](http://host/webdav_folder)  ~/mount_dir davfs user,rw,noauto 0 0*[/COLOR][/FONT][/SIZE][/B]

[SIZE=3][FONT=Arial]below is our _/etc/fstab_ entry that works in our ubuntu desktop machine (not a ltsp client) :
[/FONT][/SIZE][B][SIZE=2][FONT=Arial]
   [http://host/webdav_folder](http://host/webdav_folder)  /home/user/mount_dir davfs user,rw,noauto 0 0[/FONT][/SIZE][/B]
[SIZE=3][FONT=Arial]
we want to configure our ltsp server to provide each client with each own copy of _/etc/fstab_ with the corresponding [COLOR=Sienna]***suppose entry***[/COLOR] as specifed above.

does it work if we modify the _fstab_ under the _/opt/ltsp/i386/etc/ _directory in the [COLOR=RoyalBlue]**ltsp server**[/COLOR], then we execute an image update?

anyway, the copy of the _fstab_ file under _/opt/ltsp/i386/etc/ _does not have any entries.

hope anybody can help us on this...

thanks ...[/FONT][/SIZE]

---

