---
title: "SMb Share/ Mount issues"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by neuman1812 on 2012-11-05
So I've searched the forums and tried everthing I could find on mounting.   But I just cant seem to get this to work.

Im trying to mount a share on a network drive.

Server= 192.168.1.101 (Shares)

I start with this command:
```
sudo mount -t cifs -o username=Mysmbuser,password=***** //192.168.1.101/shares/music /mnt/music
```

That gets me:
```
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Syslog shows:
```
kernel: [11954.131608] CIFS VFS: cifs_mount failed w/return code = -6
```

So I tried it this way:
```
sudo mount -t cifs //192.168.1.101/shares/music /mnt/music -o username=mysmbuser,password=*****
```
and get the same response 

I can ping the 192.168.1.101
I Can access the share using Places-Network-Shares
Usign Ubuntu 12.04  to connect to a Ubuntu 12.04 headless server.

---

### Post by dannyboy79 on 2012-11-05
let me see the smb.conf from the server.

also, have you tried running smbtree or findsmb?

also, have you added your user to smbpasswd?

here's some help if you are having trouble. [http://opensuse.swerdna.org/susesambacifs.html#tempsec](http://opensuse.swerdna.org/susesambacifs.html#tempsec)

---

### Post by klein de usa on 2012-11-05
i just did this to day, it may be your mount point shouldn't it be ~/mnt/music

---

### Post by neuman1812 on 2012-11-05
> **dannyboy79 said:**
> let me see the smb.conf from the server.

also, have you tried running smbtree or findsmb?

also, have you added your user to smbpasswd?

here's some help if you are having trouble. [http://opensuse.swerdna.org/susesambacifs.html#tempsec](http://opensuse.swerdna.org/susesambacifs.html#tempsec)


[smb.conf PasteBin Link ]("http://pastebin.com/wcCfn0ty")

smbtree
$ smbtree
```
Enter neumans password: 
LHOME
	\\shares        		shares server (Samba, Ubuntu)
	\\shares\IPC$          	IPC Service (shares server (Samba, Ubuntu))
	\\shares\print$         	Printer Drivers
	\\shares\Storage        	
	\\shares\music            	
	

```
I verified the user has access to that share. I dont seem to have an smbpasswd file
```
/etc/samba# ls
dhcp.conf  gdbcommands  smb.conf
```



I also verified Im not mounting to ~/music   Im mounting to /mnt/music.

---

### Post by klein de usa on 2012-11-05
on the computer where the files are there needs to be:
samba ```
sudo apt-get install samba
```

samba password ```
sudo smbpasswd -a USERNAME
```

sambafs ```
sudo apt-get install smbfs
```

go to 
[https://help.ubuntu.com/community/Samba/SambaClientGuide]("https://help.ubuntu.com/community/Samba/SambaClientGuide") half way down the page look for or search    Connecting using CIFS    that is what i used this morning, 


~/mnt/music   ~ is short hand for your home dir = /home/user

---

### Post by neuman1812 on 2012-11-05
> **klein de usa said:**
> on the computer where the files are there needs to be:
samba ```
sudo apt-get install samba
```

samba password ```
sudo smbpasswd -a USERNAME
```

sambafs ```
sudo apt-get install smbfs
```

go to 
[https://help.ubuntu.com/community/Samba/SambaClientGuide]("https://help.ubuntu.com/community/Samba/SambaClientGuide") half way down the page look for or search    Connecting using CIFS    that is what i used this morning, 


~/mnt/music   ~ is short hand for your home dir = /home/user

Samba and smbfs are already installed on the server.  
Im well aware of what ~/  is and Im not trying to mount it there.
I have run the smbpasswd -a command.

---

### Post by klein de usa on 2012-11-05
ok computer with original files just needs the dir shared i believe. the computer i did this on has 10.04 desktop running on it.

what is the os your trying to mout the share on ?

if it is linux or ubuntu you have to do those things to that computer.

---

### Post by dannyboy79 on 2012-11-05
> **klein de usa said:**
> ok computer with original files just needs the dir shared i believe. the computer i did this on has 10.04 desktop running on it.

what is the os your trying to mout the share on ?

if it is linux or ubuntu you have to do those things to that computer.as he already showed us (via smbtree), the shares are being "shared" from LHOME already.

since you added the user to the smbpasswd file, can you now mount the share?

who owns the folder /mnt/music? and what are the permissions?

what does your smb.conf look like on the server? what are the share options?

have you tried this?
```
sudo mount -t cifs //192.168.1.101/music /mnt/music -o username=mysmbuser,password=*****
```

---

