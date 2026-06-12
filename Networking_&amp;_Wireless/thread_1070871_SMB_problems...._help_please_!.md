---
title: "SMB problems.... help please !"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by Rooster#1 on 2009-02-15
My son fancied a change after windoze, so we Installed ubuntu... which went swimmingly, even setup the wireless card :P
He can use the internet, via my router, wirelessly and all is well until we try to access a "Landisk"

This is connected to the router via cat5, and ALL the other windows computers can "see" it... and stream movies etc from it.

The Ubuntu PC has access via FTP, so it does know its there... but when we try to browse to it, an Icon appears on the desktop for a second, then vanishes !

I found a solution to a similar problem as:
To access Windows Share folder:

Press : Alt+F2
Type : smb://ipaddress/share (where ipaddress is the IP address of Windows PC and share is the name of the share folder) and click Run. 

This produces the one second icon again !!!! 
Any ideas please ?
TIA

---

### Post by cariboo on 2009-02-15
Open a Applications-->accessories-->Terminal and type:

```
smbclient -L Landisk -U%
```

You should get an output that looks something like this:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	stuff           Disk      misc stuff
	images          Disk      iso images
	updates         Disk      Project Dakota
	data            Disk      Data directory
	music           Disk      Music library
	movies          Disk      TV Shows and Movies
	print$          Disk      Printer Drivers
	HP_LaserJet_5P_LPT_parport0_HPLIP Printer   HP LaserJet 5P
	HP_LaserJet_5P_LPT_1 Printer   HP LaserJet 5P
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

take note of the workgroup, Ubuntu defaults to WORKGROUP, if it is not in the same workgroup as Landisk, press Alt-F2 and type:

```
gksu gconf-editor
```

Then navigate to system-->smb, right-click workgroup in the right panes and select edit, enter the correct workgroup and quit the editor. You should now be able to connect to Landisk.

Jim

---

### Post by Rooster#1 on 2009-02-15
Ill give this a whirl tomorrow... lads in bed at the mo !

But Im pretty sure we are all set to WORKGROUP already  :confused:

---

### Post by dmizer on 2009-02-15
If what cariboo907 posted doesn't work (depending on what version of Landisk you have), FTP may be your best option for Ubuntu. You may look for a firmware update for the Landisk as well as that may help matters.

What you're probably looking at is a conflict in samba versions between the Landisk and Ubuntu (Landisk is old, Ubuntu is new).

---

