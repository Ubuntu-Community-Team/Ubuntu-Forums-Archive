---
title: "mounting a network drive"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by dogbert176 on 2011-12-24
I have a network drive "MYBOOKLIVE", connected to my router, on a ubuntu system.

In a terminal:

frank@frank-P5K-SE ~ $ smbclient -L //192.168.0.105
Enter frank's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (frank-P5K-SE server (Samba, LinuxMint))
	print$          Disk      Printer Drivers
	Print_to_PDF    Printer   Print to a PDF File
	DESKJET-930C    Printer   HEWLETT-PACKARD DESKJET 930C
	DCP145C         Printer   DCP145C
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]

	Server               Comment
	---------            -------
	FRANK-P5K-SE         frank-P5K-SE server (Samba, Ubuntu)
	MYBOOKLIVE           My Book Live Network Storage

	Workgroup            Master
	---------            -------
	WORKGROUP            FRANK-P5K-SE

1/
What's the terminal command to mount "MYBOOKLIVE" on the directory /media/shared_documents?

I tried 
"mount -t cifs //192.168.0.105/mybooklive /media/shared_documents" 

and some variations I found on google, but I must do something wrong.

2/
Can I put a line in fstab to mount the network drive automatically to the /media/shared_documents directory?

TIA

---

### Post by collisionystm on 2011-12-24
If you want to use CIFS to mount your drive, you must install smbfs

sudo apt-get install smbfs

---

### Post by collisionystm on 2011-12-24
AND

If you are connecting to an ubuntu server from ubuntu, DONT USE SAMBA! It is slower than ssh and only ever invented to communicate with windows.

use SSH to mount the share.

You can either do this in nautilus by using CONNECT TO SERVER and saving a bookmark or in your /etc/fstab ( ill have to look this one up )

---

### Post by dogbert176 on 2011-12-24
Yes - I know; smbfs is installed

---

### Post by collisionystm on 2011-12-24
From what I can see in your output above, mybooklive should be capitalized. 

mount -t cifs //192.168.0.105/MYBOOKLIVE /media/shared_documents

Is there a password on the share?

Here is how mine are mounted ( to windows servers )


//172.16.65.119/D$ /media/usb0/HRServer/D cifs sec=ntlmv2,credentials=/root/.hrcred,iocharset=utf8,file_mode=0777,dir_mode=0777 0

I have a file in /root called .hrcred that has the username and password.
It looks like

username=USER
password=PASSWORD

Once you edit your fstab 

type

sudo mount -a

type df  to see if it mounted

---

### Post by Morbius1 on 2011-12-24
Does it have to mount to /media/shared_documents ?

In a terminal:
```
gvfs-mount smb://192.168.0.105/mybooklive
```Now open up Nautilus and go to:** /home/your-user-name/.gvfs**

You should see the mounted share at : **mybooklive on 192.168.0.105**

If that works for you you can have this automount at login using Gigolo:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by dogbert176 on 2011-12-24
yes - I used this command, but it gives me an error:


Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

---

### Post by collisionystm on 2011-12-24
> **dogbert176 said:**
> yes - I used this command, but it gives me an error:


Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Open file browser

go to file, connect to server

change type to windows server

connect to your ubuntu IP

can you see your share?

---

### Post by dogbert176 on 2011-12-24
OK - thank you
the drive is mounted at /home/your-user-name/.gvfs

good enough for me.

thanks

---

### Post by dogbert176 on 2011-12-24
@ morbius1: thanks for the gigolo-link.
cool program.

---

