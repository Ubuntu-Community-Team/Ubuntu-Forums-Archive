---
title: "[SOLVED] smb share - access of .avi files"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by FDPOD on 2008-12-13
Hi,
after spending now hours setting up a NAS Server with SME, everything is running smoothly, SMB-Shares work, I can see the shared folder in the Ubuntu File Browser, copy files back and forth ....

**BUT** if I try to run a video file directly off the NAS SMB-Shared Folder by double-clicking I get the following error from Totem:

[I][INDENT]Totem could not play 'smb://littlepackrat/movies_1/files/Movies1/The Love Twins.avi'.
There is no input plugin to handle the location of this movie[/INDENT][/I]

I'm kind of at a loss here ... :confused:
JPGs work fine i.e. 
Is this a Totem config problem, Network problem, .... ?
Any (simple) suggestions ?

Tx
FD

---

### Post by FDPOD on 2008-12-13
So, no feedback is coming in and I have to keep googling - funny what you come up with when you start spelling things out:

Anyways, the only thing that I could think of is that I have to mount the darn thing first, so I tried:

[I][INDENT][B]fdpod@Ubuntufdpod:~$ sudo mount -t smbfs -o username=fdpod,password=Shitisgonnahappen0! //littlepackrat/movies_1/files/Movies1 /mnt/NAS_Movies
[COLOR="Red"]Error[/COLOR]: Could not resolve mount point /mnt/NAS_Movies[/B][/INDENT][/I]

So- this seems to be since the mount point is not there !
created it with : *[INDENT]**sudo mkdir /mnt/NAS_Movies**[/INDENT]*

Next thing I get :

[I][INDENT][B]fdpod@Ubuntufdpod:~$ sudo mount -t smbfs -o username=fdpod,password=Shitisgonnahappen0! //littlepackrat/movies_1/files/Movies1 /mnt/NAS_Movies
[COLOR="Red"]Error[/COLOR]: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)[/B][/INDENT]
[/I]

Crap !
This now turned out to be that I was trying to mount a folder on a drive rather than the drive alone.
[I][INDENT]**fdpod@Ubuntufdpod:~$ sudo mount -t smbfs -o username=fdpod,password=Shitisgonnahappen0! //littlepackrat/movies_1 /mnt/NAS_Movies**
[/INDENT][/I]

And voila ! 
Now the double-clicking works as well.):P

---

