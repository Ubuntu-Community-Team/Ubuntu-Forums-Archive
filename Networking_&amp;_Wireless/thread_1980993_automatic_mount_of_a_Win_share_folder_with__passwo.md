---
title: "automatic mount of a Win share folder with  password"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by tuuk on 2012-05-16
I would like to mount a remote Windows share folder upon boot. So, I have a fstab entry such as

<remote folder>  <local folder>  cifs   filemode=0700,...,credentials=<local file> 0 0

where <local file> contains my username and password on the remote server.

So, in the current solution, I have my cleartext password (albeit, only readable by me and sudoers) on the disk. 

I am not worried about the other legit users of the system, however, as this is a workplace machine, if someone gets physical access to the machine, they can easily read this cleartext password, an outcome I would like to prevent if possible. ;)

So, is there a way I can have automatic mount during booting without a cleartext password file. Perhaps, something like an encrypted password file, although that sounds difficult as the system needs to know how to decrypt that file and root-access could give that power to anyone else too.

Thanks in advance for any help.
t

---

### Post by Kobalt on 2012-05-16
Unfortunately neither samba server nore cifs deamon support encrypted passwords... 
You can still use the embedded "Connect to server" option from Nautilus, and place a shortcut in the Nautilus left bar : this way your credentials will be safely stored within seahorse. But mounting shares this does have drawbacks...

---

### Post by tuuk on 2012-05-16
Thanks very much for the information.
If you don't mind, could you briefly expand on what you are referring to by
"...But mounting shares this does have drawbacks..."?
Thanks,
Tugkan

---

### Post by Morbius1 on 2012-05-16
If you mount a samba share using nautilus it runs the following generic command:
```
gvfs-mount smb://server/share
```If the share requires credentials you will be promted for them and if you select "Remember Forever" it is placed in the keyring and encrypted. If you want to have that run automatically at boot I would suggest Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

The only downside to all this is the mountpoint gvfs creates for this purpose. It's at /home/user-name/.gvfs. That may or may not be an issue for you. You can make life simpler by creating a bookmark to the .gvfs location so your applications can find it better:
```
nautilus $HOME/.gvfs
```Once nautilus opens up, select Bookmarks > Add Bookmark.

Gigolo will do it's job of automounting the remote share and the bookmark becomes a link to the mountpoint.

---

### Post by Kobalt on 2012-05-16
The drawback I was referring to is what's described by Morbius1 : the created mount point via smbfs cannot be easily accessed by all application (browsers for example)... 
I was not aware of this workaround though, I'll look into it.

---

