---
title: "Can't &quot;see&quot; samba shares (Ubuntu-&gt;Ubuntu)"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by DFlame on 2009-09-23
A bit of an odd one here. I'm having trouble browsing any of my Samba shares hosted on an Ubuntu machine from my Ubuntu laptop. They work perfectly when browsed from a Windows system, and smbclient has no problems listing them as follows:

[quote=smbclient output]gmac@gmacserv:~$ smbclient -L 192.168.xxx.xxx
Enter gmac's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Prints & Files)
	Main            Disk      Main Drive
	Public          Disk      Public Access
	Spare           Disk      Spare Drive
	Torrent DL      Disk      Torrents
	LPCS            Disk      Business Docs
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------
	GMACSERV             Prints & Files

	Workgroup            Master
	---------            -------
	WORKGROUP            
[/quote]

Browsing to Network -> Windows Network in Nautilus shows nothing at all, or *"Unable to mount location, Failed to retrieve share list from server"* when "WORKGROUP" does appear. My router has its own service called "BT" which works correctly, but only when it appears. I should also add that the 'Main' share is set up to be mounted in fstab, and works fine.

Any ideas? I've tried reinstalling smbfs, smbclient etc but to no effect.

EDIT: Currently have a workaround in effect. Using the address bar to access smb://GMACSERV seems to work for now

---

### Post by Iowan on 2009-09-23
Check [this]("http://ubuntuforums.org/showthread.php?t=1169149") one - in particular the part about **Winbind** and */etc/nsswitch.conf*.

---

### Post by DFlame on 2009-09-24
The need to browse isn't that important, considering that i know the names of my shares. I think I'll put this on the shelf until I have more time to go through it properly.

Thanks for the link, bookmarked it :)

---

