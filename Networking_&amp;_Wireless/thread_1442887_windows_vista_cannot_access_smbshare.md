---
title: "windows vista cannot access smbshare"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by voltaic on 2010-03-30
I am having an issue setting up (or rather accessing) a samba share, I have installed samba and created a share a follows:

> 
[smbshare]
        comment = 1TB Drive Share
        path = /media/1TB\ EXT\ eSATA/SMBshare
	browsable = yes
        read only = no


I then added a user to the server using:

> 
sudo useradd smbuser --shell /bin/false


and then added this to the smbuser list with:

> 
sudo smbpasswd -a smbuser


So everything seems to work fine here, I can see the server from my windows vista laptop, open the server and see the shared folder, but when I try to open the folder I enter username 'smbuser' and password 'xxxxxx' and get a windows error saying "not accessible you might not have permission to use this service"

I have even tried to set this up as a public share with full guest privileges and get the same error, any help here would be greatly appreciated :)

---

### Post by 98cwitr on 2010-03-30
both machines on the same WORKGROUP?

---

### Post by Morbius1 on 2010-03-30
>          path = /media/1TB\ EXT\ eSATA/SMBshareWhat are the file permissions on that path? ( ls -dl /*media/...* )

And how is that mount point that contains that share formatted?

File sharing permissions come in pairs. Samba determines who may have access, Linux file permissions determines who can have access.

If it's an EXT3/4 formatted partition then issuing a chmod 0777 to the path of the mount point should resolve the issue.

If it's an NTFS partition then adding the following line is one way to fix it:

> [smbshare]
        comment = 1TB Drive Share
        path = /media/1TB\ EXT\ eSATA/SMBshare
    browsable = yes
        read only = no                      
[COLOR=Blue]force user = morbius[/COLOR][COLOR=Blue]*Change morbius to your local login user name*[/COLOR]

[COLOR=DarkGreen]EDIT[/COLOR]: And don't forget to restart samba: **sudo service samba restart**

What that will do is act as a mask converting the remote user to you as far as that share is concerned.

---

### Post by voltaic on 2010-03-30
Thanks for the responses guys.

98cwitr: Yes the machines are in the same workgroup

Morbius1:

File permissions are:
> 
daniel@tesla-sci:/var/lib/samba$ ls -dl /media/1TB\ EXT\ eSATA/SMBshare/
drwx------ 1 daniel daniel 0 2010-03-30 18:19 /media/1TB EXT eSATA/SMBshare/


The format is NTFS, so I added 'force user = daniel' to the end of the share.

Still getting the same error :(

---

### Post by voltaic on 2010-03-30
OK, so just as a test I created a new share which is not on an NTFS drive, just on the native filesystem:

> 
[testshare]
	comment = Test Share
	path = /home/daniel/sharetest
	browsable = yes
	read only = no


This share works fine (although I still need to get the other one working)

---

### Post by Morbius1 on 2010-03-30
That's interesting.

> drwx------ 1 daniel daniel 
That's definitely the problem. Only daniel can access the target directory.

> The format is NTFS, so I added 'force user = daniel' to the end of the share.
And that should have fixed it.

I assume you restarted the samba service?

If you did can you post the output of the following two commands please:

**net usershare info**
**testparm -s**

---

### Post by voltaic on 2010-03-30
Yeah, the service was restarted after force user was added. Here's the output of those commands as requested:

> 
daniel@tesla-sci:~$ net usershare info
daniel@tesla-sci:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[smbshare]"
Processing section "[testshare]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[smbshare]
	comment = 1TB Drive Share
	path = /media/1TB\ EXT\ eSATA/SMBshare
	force user = daniel
	read only = No

[testshare]
	comment = Test Share
	path = /home/daniel/sharetest
	read only = No
daniel@tesla-sci:~$ 


---

### Post by Morbius1 on 2010-03-30
I just did a little experiment and created the following share:
> [Documents and Settings]
    path = /windows/D/Documents and Settings
     writeable = no
     browseable = yes
    guest ok = yesIt works just fine. Then I did it this way:
> [Documents and Settings]
    path = /windows/D/Documents\ and\ Settings
     writeable = no
     browseable = yes
    guest ok = yesIt won't let me in. I understand why you used the "\" for spaces and any reasonable person would  have thought that was the way it should be done. Try it with out it and see if it makes any difference.

---

### Post by voltaic on 2010-03-30
Oddly enough, if I remove the '\'s then I can't even open the server from the windows computer! Strange that it should work for you but not for me.

Just as a workaround I'm going to rename the drive to something without spaces...although I am still curious as to why it doesn't work.

---

### Post by voltaic on 2010-03-30
OMFG.... changed the partition name to 1TBext, then changed the share description in smb.conf to reflect this, restarted samba... and I'm still getting the same error?!

The test share still works.

edit: I have a feeling this has to do with the permissions associated with the drive, which it doesn't seem to want to let me change:

> 
daniel@tesla-sci:/media/1TBext$ ls -l
total 32
drwx------ 1 daniel daniel     0 2010-03-30 20:46 incoming
drwx------ 1 daniel daniel     0 2008-12-30 00:57 ISO
drwx------ 1 daniel daniel     0 2009-04-05 18:54 media
drwx------ 1 daniel daniel     0 2010-03-30 19:33 repository
drwx------ 1 daniel daniel     0 2010-03-30 18:19 SMBshare
drwx------ 1 daniel daniel 32768 2009-11-28 17:13 sort
daniel@tesla-sci:/media/1TBext$ sudo chmod a+rw ./SMBshare/
daniel@tesla-sci:/media/1TBext$ ls -l
total 32
drwx------ 1 daniel daniel     0 2010-03-30 20:46 incoming
drwx------ 1 daniel daniel     0 2008-12-30 00:57 ISO
drwx------ 1 daniel daniel     0 2009-04-05 18:54 media
drwx------ 1 daniel daniel     0 2010-03-30 19:33 repository
drwx------ 1 daniel daniel     0 2010-03-30 18:19 SMBshare
drwx------ 1 daniel daniel 32768 2009-11-28 17:13 sort
daniel@tesla-sci:/media/1TBext$ 


edit2: actually that's obvious as it's NTFS, but the force-user, as you said, should take care of that... still stumped.

---

### Post by Morbius1 on 2010-03-30
Damn, there isn't some kind of on-board encryption mechanism or something like that on that device is there?

From the Vista Machine:

Open **Command Prompt**
Type **net view** **\\tesla-sci**

I'm guessing that's the correct machine name. See if it gives you a better error message.

[COLOR=Blue]Edit: didn't see your edit. You can't change ntfs permissions using chmod. You can only change permissions using a mount or in fstab. With the force user you shouldn't need to change permissions. If you can access the device as daniel so should the remote user.
[/COLOR]

---

### Post by voltaic on 2010-03-30
I didn't see your post until just now, as I was hitting refresh on the original thread but it's gone to page 2 and I didn't notice.. doh.

I'll check the vista machine now and let you know.

---

### Post by voltaic on 2010-03-30
output is here:

> 
C:\Users\Voltaic>net view \\tesla-sci
Shared resources at \\tesla-sci

tesla-sci server (Samba, Ubuntu)

Share name    Type   Used as  Comment

-------------------------------------------------------------
smbshare      Disk   (UNC)    1TB Drive Share
Stylus-SX200  Print           EPSON Stylus SX200
testshare     Disk   (UNC)    Test Share
The command completed successfully.



---

### Post by Morbius1 on 2010-03-30
This one's got me stumped.

If Vista couldn't access any shares it would be a different matter.

There's something about the esata drive that I just can't figure out. I've been thinking of it as an external USB drive. Maybe there's something I'm not familiar with about esata that's preventing sharing but for the life of me I don't know what that is. 

I'll see what I can find out about this and report back - have to start on it tomorrow though. Sorry.

---

### Post by voltaic on 2010-03-30
Hopefully you catch this before you think about it too mich - it was labelled as an eSATA drive but it;s actually a SATA drive in a USB dock.. so it is USB.

Thanks for all the help thus far, I'll work on it through the night and I sort it out I'll post back to let you know.

---

### Post by voltaic on 2010-03-30
YYYYAAAASSSS!!!!!111

ok solved it, although it's a bit messy and I need to clean it up and do it through fstab rather than manually, but here is my fix:

> 
daniel@tesla-sci:~$ sudo mkdir /media/1TBext
daniel@tesla-sci:~$ sudo mount /dev/sdb1 /media/1TBext -t ntfs -r -o umask=0000


---

### Post by voltaic on 2010-03-30
Well I was too enthusiastic, this solution causes problems with local permissions, but I'm going to bed... back to it tomorrow.

---

### Post by Morbius1 on 2010-03-31
You know I thought about this overnight ( I have no real life ) and came to the same idea you did. Mount it manually to bypass the automount feature built into the system. I thought that maybe there was some kind of anomaly with eSata at the time. Since it's really USB this becomes even stranger.

There's a problem with your mount command, I think:
> sudo mount /dev/sdb1 /media/1TBext -t ntfs [COLOR=Blue]-r[/COLOR] -o umask=0000                      The "[COLOR=Blue]-r[/COLOR]" option mount the filesystem as read-only 
The umask=0000 mounts with read / write to everyone

Not sure which option has priority or if the system will ignore both but I would suggest getting rid of the "[COLOR=Blue]-r[/COLOR]" option.

Just curious, Is this dirve in an enclosure that you placed your own drive into, or is it an off the shelf pre-assembled external drive? Maybe there's something about the enclosure that's gumming things up.

---

### Post by voltaic on 2010-03-31
haha I don't have any real life either so no judgement there. It's my own drive in an external enclosure, so there's no weird proprietary crap in there (that I know of anyway...). I'm not sure why I had the -r in there, other than that I was  half asleep. I'm going to try it again without the -r and report back.

---

### Post by voltaic on 2010-03-31
This works :)

but now there's another issue (joy) although I think this is probably a minor one, I'm just not sure about how to fix it; since it's an external drive the /dev/xxx is going to change randomly on reboots... for instance last night it was /dev/sdb but now (as I rebooted) it's /dev/sdd as there are other usb devices and it seems to assign them in a random order. Obviously this drive will need to have the same /dev/xxx name every time or I will not be able to add it to fstab, and although I could mount it manually every time I reboot, I'd rather not... any ideas?

---

### Post by Morbius1 on 2010-03-31
[B]error
[/B]

---

### Post by Morbius1 on 2010-03-31
I've got two you can try:

By Label:
>                               sudo mount -L 1TBext /media/1TBext -t ntfs -o umask=0000                      I generally don't like having the label and the mount point name match but linux does this by default when it automounts so ........

By UUID:
>                              sudo mount -U 5D51B07367FFE9AD /media/1TBext -t ntfs -o umask=0000  The UUID number will be unique but will change if you reformat the drive.

You can find the UUID number by issuing the following command:

[B]sudo blkid -c /dev/null


[COLOR=Blue]EDIT: The syntax in fstab is slightly different from this:

[/COLOR][/B][COLOR=Blue][COLOR=Black]For example:[/COLOR][/COLOR][B][COLOR=Blue][COLOR=Black] 

[/COLOR][/COLOR][/B][COLOR=Blue][COLOR=Black]/dev/sdb1 /media/[/COLOR][/COLOR]1TBext ntfs ....................

Becomes:

LABEL=1TBext /media/1TBext ntfs .......................
OR
UUID=5D51B07367FFE9AD /media/1TBext ntfs ..................
[B][COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR][/B]

---

### Post by voltaic on 2010-03-31
Awesom, I've never really done much with fstab so just to make sure, is this what the entry should look like:

> 
UUID=286C96716C963990 /media/1TBext ntfs auto,umask=0000 0 0


Thanks again for all your help on this :)

---

### Post by Morbius1 on 2010-03-31
> **voltaic said:**
> Awesom, I've never really done much with fstab so just to make sure, is this what the entry should look like:



Thanks again for all your help on this :)

That should work. I prefer to use "defaults" to "auto" though.

---

### Post by Morbius1 on 2010-03-31
I should have mentioned this earlier but because of quirk in ntfs you will loose the ability of plug and play when you add an entry in fstab for an external USB device. Something to do with ntfs-3g and fuse or something like that. The external drive will have to be plugged in before you boot for this to work. If you plug it in after you will get an error.

If it were FAT32 you'd be able to add a line in fstab that has the "noauto" and "user" option:

```
LABEL=CORSAIR /home/morbius/CORSAIR vfat user,umask=007,utf8,flush,noauto 0 0
```Then when you plugged it in it would mount automatically to your mount point. This doesn't work with ntfs - you'll get a permissions error.

So for ntfs the external drive will have to be "on" before you boot.

---

### Post by voltaic on 2010-03-31
> **Morbius1 said:**
> I should have mentioned this earlier but because of quirk in ntfs you will loose the ability of plug and play when you add an entry in fstab for an external USB device. Something to do with ntfs-3g and fuse or something like that. The external drive will have to be plugged in before you boot for this to work. If you plug it in after you will get an error.

If it were FAT32 you'd be able to add a line in fstab that has the "noauto" and "user" option:

```
LABEL=CORSAIR /home/morbius/CORSAIR vfat user,umask=007,utf8,flush,noauto 0 0
```Then when you plugged it in it would mount automatically to your mount point. This doesn't work with ntfs - you'll get a permissions error.

So for ntfs the external drive will have to be "on" before you boot.

Handy to know this, I don't think it should be a problem as the drive has it's own power supply and if I reboot the PC the drive will stay on. This is only a temporary set up anyway until I can get some cash set aside to build a standalone server.

---

