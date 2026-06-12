---
title: "Samba share from Mythbuntu to Ubuntu and Windows machines"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by Bugy6 on 2011-09-14
Hi,

I know there is a million and one guides, how tos and posts about samba and its setup/config, but I'm afraid I'm still stuck so if anyone could help me it would be great and my girlfriend will be very pleased as she can have me back out of the clutches of my computers.

So my setup.

I have just setup mythbuntu on an old laptop which is ethernetted (if thats a word) straight into the router, the files that it accesses are on three external hard drives, a 250gb NTFS, a 500gb FAT32 and a 2tb FAT32. These drives are mounted on boot to /home/rool/ and then the Music, Pictures and Videos folders, this also works fine and I have given these folders all read, write and execute permissions for owner, user and group.

Now the problem comes when I try to share these folders with samba to my ubuntu and windows laptops. Nothing seems to appear in the WORKGROUP on either machine.

So now i will post my conf files for fstab and smb.conf in the hope that someone will be able to see what is wrong.

Thanks in advance.
Bugsy

fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=37c3074e-b03b-4341-8813-b0bc1e91e302 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=116f0658-374f-4d26-b1d7-117242f89dfa none            swap    sw              0       0
# external drive 250gb
UUID=2B2B-53AD  /home/rool/Pictures     vfat    defaults,uid=1000,gid=1000,umask=000,dmask=000,fmask=111            0       0
# external drive 500gb
UUID=10D8-132E  /home/rool/Music        vfat    defaults,uid=1000,gid=1000,umask=000,dmask=000,fmask=111            0       0
# external drive 2tb
UUID=1C69-A979  /home/rool/Videos       vfat    defaults,uid=1000,gid=1000,umask=000,dmask=000,fmask=111            0       0
``` 

smb.conf
```
[global]
	workgroup = WORKGROUP
	netbios name = rool
	server string = %h server (Samba, Mythbuntu)
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action.%d
	dns proxy = no
	security = user

[Recordings]
	comment = TV Recordings
	path = /home/rool/Videos/recordings
	public = yes
	browsable = yes
	writable = yes
	force user = rool
	force group = rool

[Pictures]
	comment = Pictures
	path = /home/rool/Pictures
	public = yes
	browsable = yes	
	writable = yes
	force user = rool
        force group = rool

[Music]
	comment = Music
	path = /home/rool/Music
	public = yes
	browsable = yes
	writable = yes
	force user = rool
        force group = rool

[Videos]
	comment = Videos
	path = /home/rool/Videos
	public = yes
	browsable = yes
	writable = yes
	force user = rool
        force group = rool



```

---

