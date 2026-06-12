---
title: "Ubuntu 8.10 and Time Capsule Samba"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by zenobiaflex on 2009-03-02
So I have followed the procedures outline that I can find for mounting my Time Capsule as a Samba share... I always get an error, though:

zenobiaflex@zenobiaflex-desktop:~$ sudo mount.cifs //192.168.0.195/"PocketUniverse"/STUFF /media/capsule -o pass=123456
[sudo] password for zenobiaflex:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

I created that capsule directory based on the help I could find out there... but just can't get this to work. I was using Linux Mint, but switched to Ubuntu to see if going "home" would help... it did help with some problems I had that are unrelated, but this problem is sticking around... I really want to be able to transfer files to the Time Capsule share!

Any insight would really help.:confused:

---

### Post by cariboo on 2009-03-02
Open a terminal and type:

```
smbclient -L 192.168.0.195 -U%
```

If you shared directory is setup properly you should see something like this:

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
	WIN-MCLEESE           

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

Jim

---

### Post by kenlars99 on 2009-07-15
This is what worked for me:

First I looked the the airport utility to get the IP address (192.168.1.65)
Then from my Ubuntu machine I used nmblookup to find the netbios name given the IP address.  
My netbios name turned out to be KEN-LARSONS-TI

ken@swami:~$ nmblookup -A 192.168.1.65
Looking up status of 192.168.1.65
    KEN-LARSONS-TI  <00> -         B <ACTIVE> <PERMANENT> 
    WORKGROUP       <00> - <GROUP> B <ACTIVE> <PERMANENT> 
    KEN-LARSONS-TI  <20> -         B <ACTIVE> <PERMANENT> 

    MAC Address = ....


Then I used smbclient to list the shares, and found that the share was called Data:
ken@swami:~$ smbclient -L //KEN-LARSONS-TI
Password: 
Domain=[WORKGROUP] OS=[Apple Base Station] Server=[CIFS 4.32]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       
    Data            Disk      
...


Then I was able to mount it as follows:
sudo mount.cifs //192.168.1.65/Data /media/capsule -o pass=secretpassword

---

### Post by serialbumpy on 2009-12-03
> **kenlars99 said:**
> This is what worked for me:

First I looked the the airport utility to get the IP address (192.168.1.65)
Then from my Ubuntu machine I used nmblookup to find the netbios name given the IP address.  
My netbios name turned out to be KEN-LARSONS-TI

ken@swami:~$ nmblookup -A 192.168.1.65
Looking up status of 192.168.1.65
    KEN-LARSONS-TI  <00> -         B <ACTIVE> <PERMANENT> 
    WORKGROUP       <00> - <GROUP> B <ACTIVE> <PERMANENT> 
    KEN-LARSONS-TI  <20> -         B <ACTIVE> <PERMANENT> 

    MAC Address = ....


Then I used smbclient to list the shares, and found that the share was called Data:
ken@swami:~$ smbclient -L //KEN-LARSONS-TI
Password: 
Domain=[WORKGROUP] OS=[Apple Base Station] Server=[CIFS 4.32]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       
    Data            Disk      
...


Then I was able to mount it as follows:
sudo mount.cifs //192.168.1.65/Data /media/capsule -o pass=secretpassword

Thanks this helped a lot. I've got my time capsule mounted; however, the files/directories are not visible. But using the terminal, I can cd into the directories that I've created on the time capsule with my XP and OSX boxes and copy files FROM the time capsule.

Unfortunately, whenver I try to write to a text file on the time capsule, it reads "@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@" (etc) after saving (trust me, that is NOT what I wrote).

This is the generic command I used to connect to the time capsule:
```
sudo mount.cifs //10.0.1.1/"Time Capsule" /media/s -o pass=password
```

Does anybody know what's wrong with this setup? By the way I'm actually using 9.10. Thanks.

---

### Post by komputes on 2010-01-22
I am able to mount the CIFS share using this command:
```
sudo mount.cifs //10.0.1.1/"Time Capsule"/ /media/capsule -o pass=password

```However, once mounted, the mountpoint directory is empty. I believe the cause of this issue is explained in Bug #406466.

[http://bugs.launchpad.net/bugs/406466]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/406466")

@serialbumpy - until this bug is resolved, I would not be writing to a share where you cannot see files (unless there is absolutely nothing on the drive). The reason I say this is that I am fearing corruption.


Workaround:
There is a community project called afpfs-ng, which is a client for the Apple Filing Protocol (AFP). It will let you access shared volumes on Mac OS X Servers. It is developed by Alex deVries ([alexthepuffin]("http://ubuntuforums.org/member.php?u=251106"), active in ubuntuforums). afpfs-ng packages for Ubuntu can be found here:  
[http://sourceforge.net/projects/afpfs-ng/files/](http://sourceforge.net/projects/afpfs-ng/files/)

Once installed, this is how it should be used: 
```
 $ sudo mount_afp afp://user:passwd@10.0.1.1/"Time Capsule" /media/capsule 

```Once this is done, you can use the command line to move file to the Time Capsule. You can also graphically read files/write file from/to the Time Capsule as root. This is done as follows: 
```
$ sudo -s 
# cd /media/capsule 
# nautilus . 

```Unfortunately, it does not add a feature in GNOME's "Places > Connect to server" but perhaps there is a way to mount it that way though "Custom Location" in the pull-down menu.

---

