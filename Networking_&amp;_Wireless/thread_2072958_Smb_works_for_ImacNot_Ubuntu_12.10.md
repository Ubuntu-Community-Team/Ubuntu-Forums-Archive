---
title: "Smb works for Imac/Not Ubuntu 12.10"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by JustinAlf on 2012-10-18
I simply cannot understand this.  My networking worked in 12.04, not 12.10

I dualboot on a 27 inch iMac.  In Mac OSX, I type in smb://mediabox  and I connect to my mediabox server.  

I type the same thing in nautalis and get "error: Failed to retrieave share list from server"

They both use SMB and samba, why does one work and one not?

---

### Post by markdavidoff on 2012-10-19
I noticed that Ubuntu 12.10 removed the smbfs package.

Go to the terminal and install it using:
sudo apt-get install smbfs

Hopefully, that will fix your issues.

---

### Post by JustinAlf on 2012-10-19
> **markdavidoff said:**
> I noticed that Ubuntu 12.10 removed the smbfs package.

Go to the terminal and install it using:
sudo apt-get install smbfs

Hopefully, that will fix your issues.

This is the result of that command:

sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cifs-utils

E: Package 'smbfs' has no installation candidate

---

### Post by markdavidoff on 2012-10-19
in that case,
sudo apt-get install cifs-utils

also, can you ping your media server?

---

### Post by JustinAlf on 2012-10-19
> **markdavidoff said:**
> in that case,
sudo apt-get install cifs-utils

also, can you ping your media server?

I have installed cifs-utlis.

I can connect to the mediabox server now via it's IP address.  However, I cannot connect to it through it's name "mediabox" as it is on the server.

I need to connect to another server titled "officeserver" and don't know the IP address for it.  Is there perhaps a problem with the way Ubuntu is recognizing the text of the server names?

---

### Post by markdavidoff on 2012-10-19
what is the output of the command smbtree?

Also, you may want to take a look here:
[http://ubuntuforums.org/showthread.php?t=909020](http://ubuntuforums.org/showthread.php?t=909020)

---

### Post by JustinAlf on 2012-10-19
> **markdavidoff said:**
> what is the output of the command smbtree?

Also, you may want to take a look here:
[http://ubuntuforums.org/showthread.php?t=909020](http://ubuntuforums.org/showthread.php?t=909020)

I aprreciated all your help with this.

My smbtree is as follows:

justin@justin-iMac:~$ smbtree
Ignoring unknown parameter "update encrypted"
Ignoring unknown parameter "server role"
Enter justin's password:

---

### Post by JustinAlf on 2012-10-19
I can also Not Ping the "officeserver".  Very frustrating as I need to connect to this server for work.

---

### Post by markdavidoff on 2012-10-20
and after you enter your password?

From [http://ubuntuforums.org/showthread.php?t=909020](http://ubuntuforums.org/showthread.php?t=909020) :

> **Peter09 said:**
> You need to install winbind

```
sudo apt-get install winbind
```

then edit 

/etc/nsswitch.conf and add 'wins' so that the hosts line looks something like this (order matters)

```
hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4 
```

then restart winbind with

```
sudo /etc/init.d/winbind restart
```

that should do it.

PC

> **Peter09 said:**
> Just remebered in your /etc/samba/smb.conf file you need the line

```
    name resolve order = lmhosts wins bcast host
```

you may already have some of that line but you will need the wins bit as well.

Try this.
Also, what is the output of:

smbclient -L localhost

---

### Post by djoh on 2012-10-21
Hi,

I faced the same issue after upgrading from 12.04 to 12.10.
Installed the package cifs-utils fixed it !

sudo apt-get install cifs-utils

---

### Post by JustinAlf on 2012-10-22
> **markdavidoff said:**
> and after you enter your password?

From [http://ubuntuforums.org/showthread.php?t=909020](http://ubuntuforums.org/showthread.php?t=909020) :





Try this.
Also, what is the output of:

It shows my networked printers but not the "workserver" that I need to connect to.

smbclient -L localhost

smbclient -L localhost
WARNING: The "password level" option is deprecated
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Unknown parameter encountered: "server role"
Ignoring unknown parameter "server role"
Enter justin's password: 
Domain=[MOGOP] OS=[Unix] Server=[Samba 3.6.6]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Samba file and print server)
	sysvol          Disk      
	pdf-printer     Printer   PDF Printer Service
	pdf-documents   Disk      Converted PDF Documents
	profiles        Disk      User Profiles
	netlogon        Disk      Network Logon Service
	homes           Disk      Home Directories
	Hewlett-Packard-HP-LaserJet-P4015 Printer   Hewlett-Packard HP LaserJet P4015-1
	Ricoh-Aficio-MP-C4500 Printer   Ricoh Aficio MP C4500
	justin          Disk      Home Directories
Domain=[MOGOP] OS=[Unix] Server=[Samba 3.6.6]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            PRINTSERVER

---

### Post by JustinAlf on 2012-10-23
One of the worst things to happen when trying to fix something is when you make tons of changes, and then it works, and you can't figure out which change actually made it happen!  I can now connect to my windows server through IP.  And I think this is how I made it happen:


In /etc/samba/smb.conf add the following to the bottom of the [global] section:

client lanman auth = yes
client ntlmv2 auth = no

---

