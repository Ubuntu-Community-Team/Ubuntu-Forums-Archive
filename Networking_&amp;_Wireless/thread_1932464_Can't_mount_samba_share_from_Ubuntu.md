---
title: "Can't mount samba share from Ubuntu?"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by the_dingman on 2012-02-27
I have a fileserver set up running Ubuntu 11.10.  The fileserver is accessible by my windows machines, but I have been unable to get either of my other Ubuntu installations to link to the shares.

Connections I am trying are local, wired and from machines that dual-boot, with Windows connecting just fine.

My server IP is 192.168.42.2 (or //theta) with the share being /fileserver.  There are no passwords required.

I have tried the following lines in my fstab file (separately):


//theta/fileserver /home/dingman/theta cifs uid=dingman,user=,password= 0   0

//theta/fileserver /home/dingman/theta cifs guest, 0   0

Any help would be appreciated.

---

### Post by Morbius1 on 2012-02-27
> //theta/fileserver /home/dingman/theta cifs guest, 0   0
Get rif of that last "," after guest:
```
//theta/fileserver /home/dingman/theta cifs guest 0   0
```

---

### Post by the_dingman on 2012-02-27
> **Morbius1 said:**
> Get rif of that last "," after guest:
```
//theta/fileserver /home/dingman/theta cifs guest 0   0
```

No luck.

Thanks for the help.

---

### Post by Morbius1 on 2012-02-27
In a terminal:
```
gvfs-mount smb://theta/fileserver
```Followed by:
```
nautilus /home/dingman/.gvfs
```You should see a folder named: **fileserver on theta**

If all that works then don't use fstab use Gigolo to automount: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by the_dingman on 2012-02-27
Received, after the first command:

Error mounting location: volume doesn't implement mount

:mad:

---

### Post by Morbius1 on 2012-02-27
Please post the output of the following commands - these are to be run from the server:
```
testparm -s
``````
net usershare info --long
```And the output of this command run from a Linux client:
```
smbtree
```

---

### Post by the_dingman on 2012-02-27
> **Morbius1 said:**
> Please post the output of the following commands - these are to be run from the server:
```
testparm -s
``````
net usershare info --long
```And the output of this command run from a Linux client:
```
smbtree
```

```


Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[CD/DVD Disc Drive]"
Processing section "[Fileserver]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = OMEGA
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[CD/DVD Disc Drive]
	comment = Theta CD-ROM Drive
	path = /cdrom
	read only = No
	guest ok = Yes
	locking = No

[Fileserver]
	comment = Theta Shared Folder
	path = /home/theta
	read only = No
	create mask = 0755
	guest ok = Yes

```

net command resulted in no output

```

Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
OMEGA
	\\THETA          		Theta server (Samba, Ubuntu)
		\\THETA\print$         	Printer Drivers
		\\THETA\CD/DVD Disc Drive	Theta CD-ROM Drive
		\\THETA\Fileserver     	Theta Shared Folder
		\\THETA\IPC$           	IPC Service (Theta server (Samba, Ubuntu))
MSHOME
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

```

---

### Post by Morbius1 on 2012-02-27
On the linux client run:
```
testparm -s
```And see if it lists either one of the following lines:
> encrypt passwords = No[COLOR=Blue]*It could also list it as "False"*[/COLOR]
And / Or:
> security = shareIt either or both of those are present:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Look for either or both of the lines above and change them to this:
```
encrypt passwords = Yes
security = user
```Then restart samba:
```
sudo service smbd restart
```And run smbtree again and see if those error messages go away.

---

### Post by the_dingman on 2012-02-27
You list to do these on my client?  Do you mean on my server?

[COLOR="Red"]Edit:
[/COLOR]

Also ran on my client, changed the lines as you stated, still can not connect.

right now it is as follows on my server's smb.conf:

```

encrypt passwords = yes

```

```

#    security = user

```

My understanding is that removing the comment "#" would require a username and password for anyone to access the server.  I do not want that.

---

### Post by Morbius1 on 2012-02-27
The server is fine it's the linux client that's the problem. It's not sending an encrypted password - and yes even an anonymous guest passes a password.

> My understanding is that removing the comment "#" would require a  username and password for anyone to access the server.  I do not want  that.     The default setting of samba is "security = user" so you are running that way anyway. Don't confuse smb.conf with the default settings of samba. smb.conf is a user "exception" config file that adds to or modifies pre-set defaults that you can't see without running a special command.

---

### Post by the_dingman on 2012-02-27
I've made those changes to the client, and I'm still not having luck mounting with either method.

[COLOR="Red"]Edit:[/COLOR]

The main system I'm working with is a mythbuntu install, that's the one we've been working on.

I also have a 'normal' Ubuntu install on my main desktop.  I made the changes to that system, and still can't connect.

Using gvfs, I get a different error

> 
Error mounting location: Failed to mount Windows share


The problems are persisting across different systems.  Could there be an issue with the server or with the network?

---

### Post by Morbius1 on 2012-02-27
Actually, this is getting better. A "Failed to mount" is usually a permissions error. Who owns and what are the permissions on the shared folder:
```
 ls -dl /home/theta
```

---

### Post by the_dingman on 2012-02-27
Result:

> 
drwxr-xr-x 5 nobody nogroup 4096 2012-02-15 21:59 /home/theta


---

### Post by Morbius1 on 2012-02-27
You're killin' me :P

OK, well ... um ... you can try one or both of these things on the server.

Change permissions on the target folder:
```
sudo chmod 777 /home/theta
```And/Or modify the share definition in smb.conf to force all remote users to be nobody ( which they already should be but it's way past my bed time so I'm obviously missing something... ):
> [Fileserver]
    comment = Theta Shared Folder
    path = /home/theta
    read only = No
    create mask = 0755
**[COLOR=Blue]   force user = nobody[/COLOR]**
    guest ok = YesThen restart smbd again.

EDIT: I'm going to have to shut down now - sorry. I'll check on things tomorrow or maybe 2nd shift can take it from here.

---

### Post by the_dingman on 2012-02-27
> **Morbius1 said:**
> You're killin' me :P

OK, well ... um ... you can try one or both of these things on the server.

Change permissions on the target folder:
```
sudo chmod 777 /home/theta
```And/Or modify the share definition in smb.conf to force all remote users to be nobody ( which they already should be but it's way past my bed time so I'm obviously missing something... ):
Then restart smbd again.

EDIT: I'm going to have to shut down now - sorry. I'll check on things tomorrow or maybe 2nd shift can take it from here.

Still encountering the same issues.

Thanks for the help, I greatly appreciate it!  Hopefully we can make some progress.

---

### Post by the_dingman on 2012-02-27
An update, with some success...

I was able to mount the share manually using the following command:

```

$ sudo smbmount //192.168.42.2/Fileserver ~/theta -o guest,rw

```

Interesting that the server's name would not work (Error 115), but the IP did.

From the same instructions I found, I tried the following edit to the fstab file, with no success:

```
//192.168.42.2/Fileserver ~/theta	cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Perhaps that gives insight to a new direction...

---

