---
title: "Unable to export mounted NTFS folders over NFS"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by sdgiffin on 2013-04-11
I have several Ubuntu machines, one of which, a former Wndows machine converted to ubuntu, acts as a fileserver. From it, I have several shares available consisting of Minecraft saved games, movies, MP3s, etc. On client machines, [FONT=courier new]showmount -e 1.2.3.4[/FONT] does show all the shares as being available, but I can't mount the shares from the NTFS partitions. Folders shared from the EXT4 partitions mount fine when I type 

[FONT=courier new]sudo mount -t nfs 1.2.3.4:ext4-minecraft-share /home/user001/.minecaft[/FONT]

but if I attempt 

[SIZE=2][FONT=courier new]sudo mount -t nfs 1.2.3.4:ntfs-minecraft-share /home/user002/.minecraft[/FONT][/SIZE]

I get the error

[FONT=courier new]mount.nfs: access denied by server while mounting 1.2.3.4:ntfs-minecraft-share[/FONT]

I followed the suggestions in the "NFS with NTFS" article located at [http://ubuntuforums.org/showthread.php?t=1791330](http://ubuntuforums.org/showthread.php?t=1791330) and it's still not working. The exports all appear, as I said, when queried with showmount, but they can't be mounted on the client machines if they are hosted on the server's NTFS partition.

Using Ubuntu 12.10, x64 on the server, and Ubuntu 12.10 x32 on the clients.

---

