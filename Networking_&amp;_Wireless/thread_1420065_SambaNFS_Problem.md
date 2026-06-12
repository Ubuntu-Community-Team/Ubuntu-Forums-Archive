---
title: "Samba/NFS Problem"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by tracyandskye on 2010-03-02
I have just recently setup our network with an Ubuntu server which is being accessed by one Ubuntu workstation with nfs, & one XP workstation with Samba.  Following instructions from the web, I set permissions like this:

sudo chmod 777 /media/Data

sudo chown -R curley:curley /media/Data

The problem is that files created in Samba are locked from nfs & vice/versa.  I am assuming I need to add the nfs network share to the Curley group or use something more global than curley to make this work?

Samba is working ok from Ubuntu when browsing through Nautilus, but there is no access to shares when doing things like uploading or downloading files to the web (the "save file" window only shows local folders).  So I guess I wouldn't mind just using Samba if I could map a folder in Samba to solve that problem.

---

### Post by Morbius1 on 2010-03-02
> **tracyandskye said:**
> Samba is working ok from Ubuntu when browsing through Nautilus, but there is no access to shares when doing things like uploading or downloading files to the web (the "save file" window only shows local folders).  So I guess I wouldn't mind just using Samba if I could map a folder in Samba to solve that problem.

The nautilus method ( GVFS ) actually creates a mount point but it's hidden. You have to enable Nautilus to "see" that directory by going to:
Nautilus > Edit > Preferences > View > Show hidden and backup files.

The actual mount point is at :
/home/your_user_name/.gvfs 

Some applications can see that hidden location, some have to be configured to see them, and some will never see them.

In firefox or gedit for example, after selecting "save as" , right click the right side panel of the "save as " box and select "show hidden files".

In some cases the only way out is to create a symlink to a "real" folder. For example:

Type **mkdir /home/your_user_name/ShareMount**
Type** ln -s /home/your_user_name/.gvfs /home/your_user_name/ShareMount**

---

### Post by tracyandskye on 2010-03-13
Thanks Morbius!

---

