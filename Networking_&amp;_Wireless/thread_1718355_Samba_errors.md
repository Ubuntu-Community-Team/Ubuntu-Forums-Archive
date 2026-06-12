---
title: "Samba errors"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by computerx138 on 2011-03-31
Hi,

Samba is making me lose my temper. This isn't a surprise because I've lost my temper every time I've gone near it. This time, I can't get it working through research, trial-and-error, blind luck or prayer.

**A little about how it WAS setup:**

marc-desktop, vikki-desktop connected to 1 router with static IPs. marc-desktop connects to two shares on vikki-desktop: /media/storage is local NTFS, /media/external is a USB drive. Both storage and external are setup with UUID in fstab and work perfectly.

**vikki-desktop fstab**
```
# External Drive
UUID=28F84198F84164E2 /media/external ntfs-3g defaults,uid=vikki 0 0

# NTFS Storage Partition
UUID=B668134A681308AF /media/storage ntfs-3g defaults,uid=vikki 0 0
```

**marc-desktop fstab**
```
//192.168.0.83/external 			/media/external 	cifs 		username=workgroup/vikki,password=xxxx,rw,uid=computerx 	0	0
//192.168.0.83/storage				/media/storage 		cifs 		username=workgroup/vikki,password=xxxx,rw,uid=computerx 	0	0
```

This worked perfectly.

**What went wrong?**

My darling wife wiped her hard drive and reinstalled Ubuntu. I copied her fstab, but forgot to check the folder setup in /media and forgot to copy the smb.conf. Her PC is setup with the same username and password.

**vikki-desktop smb.conf**
I added:
```
[noparse][mytemplate]
        writeable = yes
        browseable = yes
        valid users = vikki

[storage]
        path = /media/storage
        copy = mytemplate

[external]
        path = /media/external
        copy = mytemplate
[/noparse]
```

**smbusers**
```
vikki = vikki
```

And I ran:```
smbpasswd -a vikki
```
... and added vikki-desktop to my hosts.

This works through Gnome's Places | Network, if I browse to the share. It doesn't work through mount, taking the fstab values.

If I use the IP in fstab, I get error -6.
If I use vikki-desktop in fstab, I get error -22.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-31
Setting:

valid users = vikki

on all shares will only allow Vikki access. Try removing that.

Please could you post the rest of your smb.conf aswell, seeing the:

[globals]

section would help tremendously :)

---

### Post by computerx138 on 2011-03-31
Edit: Now irrelevant, see below

---

### Post by computerx138 on 2011-03-31
I ran a diff between the vikki-desktop smb.conf and the fileserver's smb.conf, and updated the vikki-desktop one to match the settings, except the shares and paths, ofc.

It still doesn't work, error -22 with the hostname, -13 with the IP.

I need the valid users line, because the children's PC shouldn't have access to it.

```
[global]
	workgroup = WORKGROUP
	server string = %h server (Samba, Ubuntu)
	dns proxy = no
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	obey pam restrictions = yes
	unix password sync = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes
	map to guest = bad user
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user

[storage]
	path = /media/storage
	writeable = yes
	valid users = vikki

[external]
	path = /media/external
	writeable = yes
	valid users = vikki


```

---

### Post by computerx138 on 2011-03-31
OK, I got it working with the above .conf. I removed the "workgroup/" from the user= in the fstab. My question is: Why would this have worked on her previous installation but not now?

---

### Post by Morbius1 on 2011-03-31
I cannot answer that but I do know that this would never work:
> [mytemplate]
        writeable = yes
        browseable = yes
        valid users = vikki

[storage]
        path = /media/storage
        copy = mytemplate

[external]
        path = /media/external
        copy = mytemplateThe copy command creates a clone of a working share. "mytemplate is not a working share since it has no path. Had you run the following command on the original smb.conf you published :
```
testparm -s
```it would have told you that samba marked [mytemplate] as "available = No" and therefore all the rest of them would have been marked that way.

---

### Post by doas777 on 2011-03-31
> **computerx138 said:**
> OK, I got it working with the above .conf. I removed the "workgroup/" from the user= in the fstab. My question is: Why would this have worked on her previous installation but not now?
heed morbius' advice. he is quite knowledgable.

as for your specific question, try flipping your slash around. windows UNC naming uses backslashes 
```
Domain\User
```

---

### Post by computerx138 on 2011-04-01
I did eventually run testparm and noticed something was up, hence the rewrite, minus copy. I wasn't sure of the exact details, so thanks for the clarification.

The UNC forward slash was put in before I bought my bash scripting book and began to understand the basics, though it's still odd that it used to work.

Since I'm in this thread, I was wondering if I could extend the original question a little...

I also have a fileserver (Ubuntu Desktop 9.10 - yes, I like ssh -X sometimes) which I was hoping to access purely over SSH (and sshfs). I've been forced to setup Samba on it (which ironically worked first time) because my wife bought a evil Windows laptop.

(I'd consider a dist upgrade but then I'd have to spend a long time locking packages and recompiling stuff..)

My fstab line is:
```
sshfs#marc@fileserver:/home/storage 		/media/fileserver 	fuse		uid=computerx,gid=computerx,umask=0,allow_other			0	0

```

If I run: "sudo mount /media/fileserver" it works perfectly.

When I restart, I get an error mounting. Both computerx and root have a password-less key login.

Any ideas?

---
Edit, further question RE samba vs ssh

The fileserver is only going to read and write large files (movies, mp3s etc) 99% of the time over the network to 3 other Ubuntu PCs. User privledges are essential, because I'd like to leave my children will full access to it, and know they won't watch horror movies for a good few years (the groups and permissions are already setup).

Is there a benefit to samba instead of SSH for this type of use? What if I start putting my workspace there, being around 20,000 files over 15gb requiring regular random access.

---

