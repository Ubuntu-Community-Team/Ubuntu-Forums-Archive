---
title: "autofs mount help"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by alastairpjb on 2012-05-14
[SIZE=3]**ubuntu 12.04 - I was using 10.04**[/SIZE]

[COLOR=Red]**Please help me mount my nas with autofs! I just need the code to put in the auto.master file.**[/COLOR]

I have previously connected to my nas with fstab but that creates alot of filemanger problems and etc/fstab has disappeared in ubuntu 12.04. It was suggested I use autofs to mount my nas or use nautilus.
[U]
**I tried nautilus first: **[/U]

[COLOR=DimGray]gksudo nautilus
Then clicked Go>Network 
[/COLOR][COLOR=DimGray]I was the presented with error message:
"[COLOR=SlateGray]Could not display network[/COLOR]" "[COLOR=SlateGray]Nautilus cannot handle network locations[/COLOR]"[/COLOR]

Nautilus cannot handle networks it says, so I though I would try the autofs mount. I read the [ubuntu help autofs]("https://help.ubuntu.com/community/Autofs") info and found it really was beyond me. I manged to install autofs but thats it. :)

[COLOR=Red]**Please help me mount my nas with autofs! I just need the code to put in the auto.master file.**[/COLOR]

**_My network info is as follows:-_**

Nas ip             = 192.168.2.65
Nas username = myusername
Nas Password   = mypassword

smbtree result info:-

[COLOR=Gray]MEGADRIVE
    \\MEGADRIVE              Megadrive Network Storage
        \\MEGADRIVE\IPC$               IPC Service (Megadrive Network Storage)
        \\MEGADRIVE\public             Folder Share for public
        \\MEGADRIVE\mega               
        \\MEGADRIVE\megadrive [/COLOR]

My previous fstab connection line ubuntu 10.04(now using 12.04)

[COLOR=Gray]//192.168.2.65/megadrive /megadrive cifs username=myusername,password=mypassword,dir_mode=0777,file_mode=0666,nounix 0 0

[COLOR=DarkGreen][B][I]Any help would be really appreciated!

[/I][/B][/COLOR][/COLOR](nas) network area storage

---

### Post by papibe on 2012-05-14
Hi alastairpjb.

I would recommend to start by testing if the share can be mounted manually before trying to set autofs.

Try this:
```
mkdir mnt

sudo mount -t cifs //MEGADRIVE/megadrive  mnt/ -ouser=myusername,password=mypassword
```
to undo the mount:
```
sudo unmount mnt/
```
Once you are sure that is working OK, I would start configuring autofs.

Regards.

---

### Post by alastairpjb on 2012-05-14
Here is the output from the above command tried! did not work,:( 

[COLOR=DarkRed]user@user-System-Product-Name:~$[/COLOR] [COLOR=DimGray]sudo mount -t cifs //MEGADRIVE/megadrive  mnt/ -ouser=myusername,password=mypassword[/COLOR]
[COLOR=DarkRed][sudo] password for user: 
[COLOR=Black]mount: wrong fs type, bad option, bad superblock on //MEGADRIVE/megadrive,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/COLOR][/COLOR]
[COLOR=DarkRed]
user@user-System-Product-Name:~$[/COLOR] [COLOR=DimGray]dmesg | tail[/COLOR]
[23808.974726] sd 7:0:0:0: [sdd] Mode Sense: 43 00 00 00
[23808.975842] sd 7:0:0:0: [sdd] No Caching mode page present
[23808.975847] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[23808.979968] sd 7:0:0:0: [sdd] No Caching mode page present
[23808.979972] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[23809.033744]  sdd: sdd1
[23809.037219] sd 7:0:0:0: [sdd] No Caching mode page present
[23809.037222] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[23809.037225] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[23882.346579] CIFS VFS: cifs_mount failed w/return code = -22
[B][SIZE=2]
Thanx for the quick reply papibe!:)[/SIZE][/B]

---

### Post by papibe on 2012-05-14
Did you install the extra samba package to be able to mount shares?

It is called 'cifs-utils'. You can check if it is installed like this:
```
apt-cache policy cifs-utils
```
If it is not installed, do it by running:
```
sudo apt-get install cifs-utils
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by alastairpjb on 2012-05-14
[COLOR=DarkRed][SIZE=2][COLOR=Black]It was not installed, I installed it, now I have a new error[/COLOR][/SIZE] :(

user@user-System-Product-Name:~$[/COLOR][COLOR=DimGray] apt-cache policy cifs-utils[/COLOR]
cifs-utils:
  Installed: (none)
  Candidate: 2:5.1-1ubuntu1
  Version table:
     2:5.1-1ubuntu1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages

[COLOR=DarkRed]user@user-System-Product-Name:~$[/COLOR] [COLOR=DimGray]sudo apt-get install cifs-utils[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  keyutils
Suggested packages:
  winbind
The following NEW packages will be installed
  cifs-utils keyutils
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 103 kB of archives.
After this operation, 333 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main cifs-utils amd64 2:5.1-1ubuntu1 [67.5 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main keyutils amd64 1.5.2-2 [35.6 kB]
Fetched 103 kB in 0s (450 kB/s)    
Selecting previously unselected package cifs-utils.
(Reading database ... 167494 files and directories currently installed.)
Unpacking cifs-utils (from .../cifs-utils_2%3a5.1-1ubuntu1_amd64.deb) ...
Selecting previously unselected package keyutils.
Unpacking keyutils (from .../keyutils_1.5.2-2_amd64.deb) ...
Processing triggers for man-db ...
Setting up cifs-utils (2:5.1-1ubuntu1) ...
Setting up keyutils (1.5.2-2) ...

[COLOR=DarkRed]user@user-System-Product-Name:~$[/COLOR] [COLOR=DimGray]sudo mount -t cifs //MEGADRIVE/megadrive  mnt/ -ouser=my username,password=mypassword[/COLOR]
mount error: could not resolve address for MEGADRIVE: Unknown error

[B]
Thanx again for the quick response![/B]

---

### Post by papibe on 2012-05-14
> **alastairpjb said:**
> mount error: could not resolve address for MEGADRIVE: Unknown error

That's an improvement. We now have a problem with the hostname. Try lowercase or its IP address.

For instance, this:
```
sudo mount -t cifs //megadrive/megadrive mnt/ -ouser=my username,password=mypassword
```
or this:
```
sudo mount -t cifs //192.168.2.65/megadrive mnt/ -ouser=my username,password=mypassword
```
Regards.

---

### Post by bryanl on 2012-05-14
make sure the NAS is named in /etc/hosts

install the autofs and cifs packages

edit /etc/auto.master to enable the line with the mount point and its related script for the type of mount (smb or whatever)

create a credentials file for the file system access (e.g. auto.smb.NASname)
that has three lines for ID, password, and domain

now here is where I get into trouble. I have ended up using an auto.smb from a while back as I haven't had much luck with recent ones. If auto.smb is executed as root then you should get something like
```

-fstype=cifs,nounix,nobrl,credentials=/etc/auto.smb.ngrnas \
	 /www ://ngrnas/www \
	 /rsc ://ngrnas/rsc \
	 /photos ://ngrnas/photos \

```
my NAS is 'ngrnas' and the shares are www, rsc, and photos. Note the options I put into the auto.smb file to help get past privilege and permission problems.

what gives me pause in this situation is that nautilus can't access the network share via .gvfs - that indicates that there is something in the way. If I understand right, this approach doesn't use the cifs package and should identify the network nodes and present you with a login prompt if login is needed to access one.

The mount test suggested by papibe is another way to make sure things are working as they should. That does use the cifs stuff.

note. auto,smb is run with the file server name as an argument. The mount point in auto.master does not need to exist as it is created by autofs as is its subdirectories when needed. When mounted, the file system will be under, for example, /mountpoint/servername/sharename .

---

### Post by alastairpjb on 2012-05-14
[COLOR=DarkRed][COLOR=Black]**No****[SIZE=2] error! :) I have no idea where the mount is? Found it![/SIZE]**[/COLOR]

user@user-System-Product-Name:~$[/COLOR] [COLOR=DimGray]sudo mount -t cifs //192.168.2.65/megadrive mnt/ -ouser=myusername,password=my password[/COLOR]
[sudo] password for user: 
[COLOR=DarkRed]user@user-System-Product-Name:~$ [/COLOR]

[SIZE=2][B][COLOR=Black]Thanx again papibe

Thanx also bryanl I have not tried your method yet but will try tomorrow (11:30pm here)[/COLOR][/B][/SIZE][B][.]("http://ubuntuforums.org/member.php?u=47506")

Regards
[ ]("http://ubuntuforums.org/member.php?u=47506")[/B]

---

### Post by papibe on 2012-05-14
> **alastairpjb said:**
> [COLOR=Black]**No****[SIZE=2] error! :)[/SIZE]**[/COLOR]

Great!

> **alastairpjb said:**
> [COLOR=Black]**No****[SIZE=2] error! :) I have no idea where the mount is?[/SIZE]**[/COLOR]

It is in your home under the 'mnt' directory (that you created following steps from post #2). 

Regards.

---

