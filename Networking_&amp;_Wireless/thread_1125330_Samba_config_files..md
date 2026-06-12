---
title: "Samba config files."
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by Arlo on 2009-04-14
I'm looking for the samba config file(s). I know that when setting up a server most of the configuration setting are set in /etc/samba/smb.conf

How when I create a share via the GUI (by right clicking a folder and selecting "Sharing Options" and "Share this folder") does samba pickup on that. Where is the share definition being stored? I am not prompted for a sudo password when I create the share so I would think the config file would be in ~. I would also need (I think) root access to restart the samba daemon to to pick up on the changed config file.

I thought I would find it in /etc/samba/smb.conf or I would find some include statements pointing to ~/.samba/smb.conf (or something).


At this point I'm not trying to accomplish any particular goal, I just want to know how it works.

Any help to that end would be appreciated.  


I've read the ubuntu [samba guide]("https://help.ubuntu.com/community/SettingUpSamba") but it looks like it's more for server set ups.

testparam does not show the share definition. 

I'm running Ubuntu 8.04 

Thanks.

---

### Post by dmizer on 2009-04-14
There are two ways of configuring samba shares in Ubuntu.

1) Via Nautilus right clicking a folder and selecting "Sharing Options" and "Share this folder"

This creates a share in userspace (that's why it doesn't need a password) via [gvfs](http://en.wikipedia.org/wiki/GVFS). Advantage to this is that it's dead easy. Disadvantage is that you can only share folders in your own home directory, and your share is not available unless you are logged in. Also, configuration options are very limited.

Frankly, I don't advocate this method of sharing because people run into too many usability problems with it. And, since the file system is virtual, I'm not sure that there are any editable configuration files anywhere.

2) Configuring a full samba server.

This method creates a full fledged samba server that runs in it's own account. There are many advantages to this but the main one is that this means that your share is available as long as the computer is turned on. You'll also experience faster file transfer speeds and better availablity. Disadvantage to this is that it's much more difficult to configure.

---

### Post by Arlo on 2009-04-14
Thanks for the info. That was bugging me.

---

### Post by Iowan on 2009-04-14
> **dmizer said:**
> 1) Via Nautilus right clicking a folder and selecting "Sharing Options" and "Share this folder"Is that the way that stores it's configuration in */var/lib/samba/usershares*?

---

