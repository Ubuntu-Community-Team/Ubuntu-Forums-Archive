---
title: "Paths, paths, paths ..."
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by nickdc on 2013-04-11
Feel such a dummy, but I just can't get this right:

I've set up an external usb drive on my neufbox router and enabled file sharing, so that it behaves like a NAS.
I'm wanting to set up a backup system, perhaps using an rsync script, or the built-in (Ubuntu 12.04) Backup facility, (or anything I can get to work!) but I can't get the path entries right.

I can access the usb drive and read and write to it by going through the following route (using Classic Gnome): Places > Network > Windows Network > Dinick [the workgroup] > neufbox > Lacie1tb   No login, username or password is required. But there is sometimes a pause on the way, or nothing opens and I have to reclick once or twice before the next bit of the path shows up; there's always a long wait for the Lacie1tb itself to open, accompanied by a message "Opening Lacie1tb ... you can cancel ...". Wait long enough and it opens. I'm assuming that may be due to the fact that the neufbox is basically set up for Windows use (nothing else officially supported).
Having arrived at an open directory in the Lacie drive, eg Backup_N, if I click Go > Location I get this as its path: smb://neufbox/lacie1tb/Backup_N

Using the above information I've tried various combinations to get the backup tools to work, but nothing has so far. rsync -av /home/nick smb://neufbox/lacie1tb/Backup_N produces
```
ssh: Could not resolve hostname smb: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(605) [sender=3.0.9]
```

I've tried various other combinations, but to no avail. Similarly I've tried various options in the Storage tab in the Backup app in System Settings, though I'm unclear whether I should be going for "Windows Share", "Custom Location" or even "Local Folder", and having tried all those options, unclear what goes in as "Server" etc and whether I need a username, domain name ...

It's at this point I realise paths and remote locations are something I still need to master :confused:

Another possibility that occurs to me is that the long delay in opening the Lacie usb disk might itself be causing connection problems for these more automated procedures.

Please would someone who understands all this stuff post some advice?

---

### Post by TheFu on 2013-04-11
a) which file sharing method is being used by the remote disk?
b) are you "mount"ing the remote file system before trying to copy/rsync to it?

GUI programs often do not have anything to do with mounts and setup temporary connections.  I'd suggest looking into using a full mount to the system, not some Gnome file browser tool.
**man mount** will explain more.  Here's an article about this topic too: [http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html) I've had to add UTF8 when mounting file systems on Win7, but don't know about router-based shares.  Most routers will be running a stripped down version of samba, if that helps.

To learn more details about rsync, read the man page - **man rsync**.  For example, I wasn't aware that rsync supported smb: protocol.  Yep, checked the man page - no mention at all.  rsync works over ether rsh or ssh connection. Of course, if you mount the remote file system locally, then rsync will be able to perform some magic, but it will treat the remote FS as a local FS and there are very different behaviors in rsync when that happens, some are undesirable.

---

### Post by nickdc on 2013-04-14
Thanks for pitching in.

> a) which file sharing method is being used by the remote disk?

I assume it's a Windows method, as it appears on the LAN as a Windows network item, and the manual for the router seems to imply it's only set up for Windows 7. It's all in French though, and my French is a bit lacking in the technical department.

> b) are you "mount"ing the remote file system before trying to copy/rsync to it?

I think I'd been imagining I could do both at the same time. Having read up on it a bit more, especially that helpful link you posted, I realise this is a more complex process than I'd first imagined.

> GUI programs often do not have anything to do with mounts and setup temporary connections.

That's a useful bit of information I hadn't been aware of. I'd assumed they use the same basic shell commands but behind the scenes, as it were.

> To learn more details about rsync, read the man page - **man rsync**.   For example, I wasn't aware that rsync supported smb: protocol.  Yep,  checked the man page - no mention at all.  rsync works over ether rsh or  ssh connection. Of course, if you mount the remote file system locally,  then rsync will be able to perform some magic, but it will treat the  remote FS as a local FS and there are very different behaviors in rsync  when that happens, some are undesirable.

I have looked at the rsync man page, but clearly need to spend more time on it. I'm clearly more out of my depth here than I thought I was. After reading the link you posted I tried mounting the remote drive, but without success:

```
~$ sudo mount -t cifs //neufbox/lacie1tb -o username=admin,password=******** /mnt/neufbox
mount: wrong fs type, bad option, bad superblock on //neufbox/lacie1tb,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```
 
dmesg | tail didn't produce anything that looked additionally helpful, so I shall return to the reading. Meanwhile I may just opt for the simpler solution of trying out cloud storage for the backup process.

Thanks again for your help. (It's taken me a while to get back as I've been laid up with 'flu.)

---

### Post by TheFu on 2013-04-14
> **nickdc said:**
> Thanks for pitching in.
From time to time, we all need a little help with our issues. Solving problems is fun!

> **nickdc said:**
> 
I assume it's a Windows method, as it appears on the LAN as a Windows network item, and the manual for the router seems to imply it's only set up for Windows 7. It's all in French though, and my French is a bit lacking in the technical department.  I would assume CIFS/Samba with a very high confidence level.  I would not assume any user/passwords are needed unless you are positive that is the case.

> **nickdc said:**
> 
I think I'd been imagining I could do both at the same time. Having read up on it a bit more, especially that helpful link you posted, I realise this is a more complex process than I'd first imagined.  The GUI programs are designed to make browsing remote file shares easier and use gvfs (I believe), but they only work within themselves. The system method of mounting requires root or a FUSE file system.  The GUI access methods are not system-wide.  Using a **mount -t cifs** would be system-wide.

> **nickdc said:**
> 
That's a useful bit of information I hadn't been aware of. I'd assumed they use the same basic shell commands but behind the scenes, as it were. Nope.  Sorta like the difference in Windows between using Explorer with \\server\sharename and using the CLI to net share D: \\server\sharename.  Does that make sense?

> **nickdc said:**
> 
I have looked at the rsync man page, but clearly need to spend more time on it. I'm clearly more out of my depth here than I thought I was. After reading the link you posted I tried mounting the remote drive, but without success:
rsync is simple AND extremely complex.  We can all spend more time reviewing the man page. ;)  Every time I read it, I learn something new.  Same applies with ssh and bash man pages.

> **nickdc said:**
> 
```
~$ sudo mount -t cifs //neufbox/lacie1tb -o username=admin,password=******** /mnt/neufbox
mount: wrong fs type, bad option, bad superblock on //neufbox/lacie1tb,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Can you ping the "neufbox"?  
Does **smbtree** show it?
Can you connect to it using the **smbclient **program? Any errors? Any log messages?
Is this a Lacie device?  Could it be using HPFS and emulating CIFS? Was it configured by an OS-X machine?

 > **nickdc said:**
> 
dmesg | tail didn't produce anything that looked additionally helpful, so I shall return to the reading. Meanwhile I may just opt for the simpler solution of trying out cloud storage for the backup process.  Things never work, until they do. ;)  I'm not a fan of "cloud" anything. Don't even like centralized services much either.  Federated services like XMPP, NNTP, and SMTP rock, of course.

> **nickdc said:**
> 
Thanks again for your help. (It's taken me a while to get back as I've been laid up with 'flu.)
No problem. I've been on travel the last few weeks myself. It is nice to drink the water from any faucet again.

---

### Post by nickdc on 2013-04-16
> Can you ping the "neufbox"?
Yes, that works.

> Does **smbtree** show it?
No, that doesn't.

> Can you connect to it using the **smbclient **program? Any errors? Any log messages?
Pass. I was somewhat baffled by the smbclient man page. Need to go back to it.

> Is this a Lacie device?  Could it be using HPFS and emulating CIFS? Was it configured by an OS-X machine?

No, it's the usb drive attached that's Lacie branded. The box it's attached to is a piece of proprietary kit produced by neuf/SFR in France. It provides telephone, broadband internet, tv etc all via an adsl line. I've always been aware it had other functionality but never got round to playing with it. That changed the other day when my main NAS went down, so I thought I'd see what the neufbox could do, using the external drive that had been an additional drive on the NAS. I've actually got that main NAS back up now, which is a lot easier to connect to, so I shall return the Lacie drive to it and carry on as before. I've learned a lot from this attempt though, and will probably pick up another usb drive to attach to the neufbox so I can continue probing. As you say:
> Solving problems is fun! ... Things never work, until they do. 

Thanks again for your time and the useful info. :)

---

