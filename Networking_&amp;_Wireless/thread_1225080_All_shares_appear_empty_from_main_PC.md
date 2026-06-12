---
title: "All shares appear empty from main PC"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by sideaway on 2009-07-28
Hey guys, I've currently got a crunchbang install running samba 2:3.3.2 and smbnetfs.

Current home setup; 6 computers.

**Desktop - Crunchbang w/ dual boot W7 setup (main PC)**
Fileserver/Media PC - Vista (HP) + Media Portal
Laptop - Ubuntu (Samba 2:3.3.2)
Laptop - DSL
Laptop - Windows 7
Laptop - Windows 7
Laptop - Vista (Basic)
[B][U]
Issue:[/U][/B]
CrunchBang comes natively with Openbox + PCmanfm + tint2, I decided to try this setup. I quite like it, however the light version comes without samba, which I installed. Samba4, to be precise. That basically did nothing, it only allowed me to view the computers and what folders they'd shared on the network, by mounting with the following script file written:
```
# !/bin/bash
# sambaon
# samba-stuff in ~/samba
mkdir ~/samba
fusesmb ~/samba/
```
and then to unmount
```
# !/bin/bash
# sambaoff
# kill samba-stuff in ~/samba
fusermount -u ~/samba
rm -rf ~/samba
```
*Note I had also installed fusesmb by the time these scripts were written*

After much time and frustration I installed the stable version in the repos, samba 2:3.3.2, which gave me some progress. I now can share files and others can access them.

With the following command, I can see shares of any computer, here is my Ubuntu Laptop;
```
hamish@hamish-desktop:~$ smbclient -L 192.168.1.8
Enter hamish's password: 
Domain=[HAMISH-LAPTOP] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (hamish-laptop server (Samba, Ubuntu))
	print$          Disk      Printer Drivers
	music           Disk      
	pictures        Disk      
	videos          Disk      
	downloads       Disk      
Domain=[HAMISH-LAPTOP] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            HAMISH-LAPTOP
hamish@hamish-desktop:~$ 
```
I can see that much, however when ever I mount the share with one of the above scripts, I can see the shared folders, but can't see their contents. PCmanfm reports the folders empty.

Can someone please help? :popcorn:

---

### Post by sideaway on 2009-07-28
Ok, further progress has been made.

I have managed to copy something from my remote laptop. This proves that Samba is working but somehow is not mounted correctly or just displaying properly through PCmanfm, I think it is my mounting procedure or PCmanfm's setup that is somehow wrong. I still can't browse with PCmanfm. This is my only road block. Why can I not browse?

```
hamish@hamish-desktop:~$ smbclient //hamish-laptop/music -U hamish
Enter hamish's password: 
Domain=[HAMISH-LAPTOP] OS=[Unix] Server=[Samba 3.3.2]
smb: \> get "The Roots - The Seed 2.0.mp3"
getting file \The Roots - The Seed 2.0.mp3 of size 6307782 as The Roots - The Seed 2.0.mp3 (614.8 kb/s) (average 614.8 kb/s)
smb: \> 

```

However I am pleased to know I can communicate with other computers, there is hope!

Am I correct that my original mounting scripts aren't using smbclient?

---

