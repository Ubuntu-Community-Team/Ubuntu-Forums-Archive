---
title: "Personal File Sharing in Ubuntu, no packages installed"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by Rsxhawk on 2013-02-14
I am trying to enable personal file sharing on my Ubuntu 12.04 install but when I access the Personal File Sharing menu it tells me the necessary packages are not installed.  What exactly is it looking for and why is this not installed by default?  Seems like a very basic thing to include in an operating system.

And as much as I love setting up samba shares, sometimes it would be nice to just right click a folder and choose sharing options.  Can anyone assist?

---

### Post by TheFu on 2013-02-14
I am not a GUI user, so take this from that point of view.

Historically, file sharing has been controlled by the administrator. Users didn't have the authority to do this because file ownership and groups were more complex that the average user wanted to know.  For example, the normal file sharing method on UNIX machines is NFS. NFS provides almost complete UNIX permissions over the network. Users, groups, read, write, execute for user, group and other are all supported.  Even set-uid or set-gid permissions work.  There are a few caveats to this level of seamless access - uid and gids need to match between the systems sharing files.  That also means that to an end user, the normal directory and file permissions that they already know (and love?) work perfectly.  An end user can set the permissions on remote files and absolutely KNOW what the permissions are on the local machine or from the remote machine. There are not 2 different permission like there are with "other operating systems" which behave differently if you accessing files local vs remote.

Samba is not the preferred method to share files between UNIX systems for the reasons that I outlined above. It works with the limitations that CIFS has. That can be fine for pure data shared storage, but compared to NFS, it is lacking.

NFS has liabilities too. It is not suitable for use over a WAN connection. It should only be used on trusted networks, just like CIFS/smb should. If you want a secure method to connect over a WAN that is 100% controlled by each user, check into **sshfs**.  This method has some limitations because it is a FUSE file system,  but it is really cool because it uses ssh and ssh credentials for authentication.  Key-based mounts over the internet - completely secure. Obviously, mounting storage over a WAN connection will be slower than over a LAN, but that can be useful regardless.

BTW, I'm running 12.04, but not with gnome or unity, so the "Personal File Sharing" that you mention is definitely not a core feature.  I think that is the correct decision, but you disagree.

Google found this: [https://apps.ubuntu.com/cat/applications/precise/gnome-user-share/](https://apps.ubuntu.com/cat/applications/precise/gnome-user-share/)
Seems to cover what you desire.

---

### Post by Morbius1 on 2013-02-14
**Personal File Sharing is not Samba**

If you want to create a share on your system open Nautilus and right click a folder and select "Sharing Options".

---

### Post by Rsxhawk on 2013-02-14
BTW, I'm running 12.04, but not with gnome or unity, so the "Personal File Sharing" that you mention is definitely not a core feature.  I think that is the correct decision, but you disagree.

Google found this: [https://apps.ubuntu.com/cat/applications/precise/gnome-user-share/](https://apps.ubuntu.com/cat/applications/precise/gnome-user-share/)
Seems to cover what you desire.[/QUOTE]

Thank you for your reply.  I'm not running Unity either, I'm actually using the Cinnamon desktop and yes, the Personal File Sharing from the Ubuntu software center is what I have installed, however the portion of it that allows files to be shared over the network tells me that its not installed.  I have attached a photo of it.  Whats odd is that Linux Mint appears to have this functionality built into it and it works quite well as I have it installed on my other laptop so I'm not sure what dependencies if any are missing.

Also, I have a Macbook Pro that I was able to share out a folder on using SMB.  This was very simple to set up and I was able to connect to the macbook from my ubuntu box and use my credentials to mount the share.  I could see the files, but when I tried transferring them, it simply said "invalid argument" or something like that and failed to transfer.  

I've never used NFS before so I suppose I could look into that.

---

### Post by Morbius1 on 2013-02-14
You need to install the following packages:
```
apache2.2-bin
libapache2-mod-dnssd
```It doesn't work very well and if you are trying to share it with a Windows machine well .. good luck.

And it doesn't share just any folder it only shares the Public folder in your home folder.

---

### Post by Rsxhawk on 2013-02-14
That did it Morbius, thanks!.  I'll play around with it and see how well it works.  As I said in my original post simply right clicking the folders themselves did not work, there was no "sharing options" available to click.

---

### Post by Morbius1 on 2013-02-14
"Sharing options" in nautilus comes from the package nautilus-share.
"Sharing options" in nemo ( if you are using the complete Cinnamon DE ) comes from nemo-share.

Just in case you want to explore that.

---

### Post by Rsxhawk on 2013-02-14
Will I need to reboot after installing nemo-share for it to take effect?

---

### Post by Morbius1 on 2013-02-14
You know, I don't know. I don't think so but you mignt have to close nemo and start it up again.

---

