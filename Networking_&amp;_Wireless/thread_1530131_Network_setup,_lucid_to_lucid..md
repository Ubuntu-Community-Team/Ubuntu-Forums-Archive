---
title: "Network setup, lucid to lucid."
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by DarkAmbient on 2010-07-13
Hi, i've been at network setup for my 2 ubuntu machines for a long time now. First thought would be that this setup I got should make networksetup easy. But I'd never actually got it to work 100%. 

Got Lucix Lynx on both machines, using ext4 filesystem. Their in the same workgroup and all that. And i've got homefolder-shares (just for testing) to work at some points.

But what I really would like to access from this computer is 2 drives on total 3TB on the other computer. Thing is that both have NTFS filesystem. (They have way to much data for me to be able to change to ext3/4 filesystem as of now)
They work fine on the computer they are hooked into. Got both read/write -access there. But could NTFS mess up my network share?

Would be a bless to get some guidance on this matter. Thanks

---

### Post by Morbius1 on 2010-07-13
Way too little information there I'm afraid.

On the machine with the NTFS partitions you want to share we need to know the following:

(1) Since you mention "workgroup" I'm going to assume you're using Samba. We need to know what method of samba your using ( there are 2 ). The output of the following commands will tell us that:
```
net usershare info
sudo net usershare info
testparm -s

```(2) How is that machine that has the NTFS partitions mounting them? Do you mount them using Nautilus or Places or do you have them automount at boot? If you have them automount then post the output of this command so we can see how you set them up:
```
cat /etc/fstab
```

---

### Post by DarkAmbient on 2010-07-13
Thanks for your reply.

I havnt edited fstab since i installed lucid lynx. Both drives gets mounted by ubuntu in /media. 

Forgot to mention that i use Samba. Not to keen about network, what can i try except Samba? 

Anyway, here's the output from those commands on the computer i wanna share the 2 NTFS drives from.

```
$ net usershare info
[1tb]
path=/media/1TB
comment=
usershare_acl=S-1-1-0:R,
guest_ok=y

[2tb]
path=/media/2TB
comment=
usershare_acl=S-1-1-0:R,
guest_ok=y

[bilder]
path=/home/anna/Bilder
comment=
usershare_acl=S-1-1-0:R,
guest_ok=y
```



when i type the same command again but this time using sudo before, nothing shows.


And the last part. As i mentioned, I've changed workgroup on both computers to FAMILY. Read that that was criticall.

```
$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[2TB]"
Processing section "[1TB]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = FAMILY
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = anna
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[2TB]
	path = /media/2TB
	read only = No

[1TB]
	path = /media/1TB
	read only = No

```


Hav'nt touched fstab and I looked into it, only 2 automounts in it is the systems mountpoint and swap memoery.

yet again, thanks for taking your time. This problem of mine have gotten rather annoying.

---

### Post by Morbius1 on 2010-07-13
You've got 2 issues here. 

(1) There are two methods of sharing folders using samba and you're using both and in two cases on the same folder:

Nautilus-share ( Nautilus > Sharing Options ):
[COLOR=Blue]*This will allow guest access with read only permissions.*[/COLOR]
> [2tb]
path=/media/2TB
comment=
usershare_acl=S-1-1-0:R,
guest_ok=yClassic-share:
[COLOR=Blue]* This will allow write access only to those remote users who have the correct username and password.*[/COLOR]
> [2TB]
    path = /media/2TB
    read only = NoYou are doing the same thing on the [1TB] share. Samba is confused. You need to decide what method you want to use: Nautilus-share or Classic-share and use that method exclusively.

(2) Those NTFS partitions, 1TB and 2TB, once mounted through places will mount with read / write permissions to you and only you. Your shares , at least the Nautilus-share shares, allow guest access. Guest is not you so it won't work.

There is a an easy fix:
Open gedit as root:
```
gksu gedit /etc/samba/smb.conf
```And add the folllowing line to the [COLOR=Blue]**[global]**[/COLOR] section of smb.conf:
```
 force user = anna
```[COLOR=Blue]*I'm assuming your local login username is anna*[/COLOR]

Save the file and restart samba:
```
sudo service smbd restart
```

---

### Post by Morbius1 on 2010-07-13
Just noticed something else in your smb.conf. You have a line:
> encrypt passwords = NoYou need to either delete that line entirely or put a # sign in front of it:
> #encrypt passwords = Noso samba will ignore it.

---

### Post by DarkAmbient on 2010-07-14
Edited the smb.conf now, network still wont work at all im sorry. But im pretty sure its an effect of me trying to solve this issue myself (before i asked here). Should have known better, I'm gonna backup some homefolder stuff then reinstall ubuntu and then try this. And I'm sure this will probably make the trick ;-)

Thanks alot for your help kind Morbius1.

---

### Post by Morbius1 on 2010-07-14
If you're reinstalling Ubuntu just because of a samba issue you might consider just reseting yourself to the beginning:

[http://art.ubuntuforums.org/showthread.php?p=9506859](http://art.ubuntuforums.org/showthread.php?p=9506859)

Post #13

---

### Post by DarkAmbient on 2010-07-16
Ah, nice. I'll try that instead. Thank you :-)

---

