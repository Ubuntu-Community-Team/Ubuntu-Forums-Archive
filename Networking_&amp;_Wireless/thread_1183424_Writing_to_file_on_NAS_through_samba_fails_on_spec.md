---
title: "Writing to file on NAS through samba fails on specific applications."
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by wkimberly on 2009-06-10
Writing to file on NAS through samba fails on specific applications.

I have a 1Tb Network Attach Storage (NAS) and I access it using SMB. Strangely some applications (e.g. Amarok, Gedit, Open Office, mp3tags) Fail to successfully write to any file, on Open Office returns error Drive Full. If I use Vim or Emacs to edit any file of any size (from several bytes to several Megabytes) they never fails.

When editing mp3 Tags, the tag data cached in the file system but not committed to the NAS. If I check the mp3 tag in Ubuntu, the tags are modified. If I check the same file on another machine the tag has the old information. When unmounting and remounting the drive all the info is lost.

To mount the drive I run:
```
sudo mount -t cifs --verbose -o guest,uid=wk,gid=wk,noexec,file_mode=0660,async //192.168.1.1/PUBLIC ~/samba_1tera
```

Let's check the size:
```
df -h samba_1tera/
Filesystem            Size  Used Avail Use% Mounted on
//192.168.1.1/PUBLIC  932G  271G  661G  30% /home/wk/samba_1tera
```

I try to write to a file using gedit or Open Office and it fails. It also fails to change mp3 tags using any mp3 program (Amarok, mp3blast, Rhythmbox) and changes don't get committed to the drive. Files can be easily moved around with these programs (i.e. Auto organize mp3 with artist/album/song folder structure). Gedit and Open Office created some temporary files (.gedit-save-UXC4UU or *.swo and *.swp respectively).


Running dmesg shows several interesting messages:
```
CIFS VFS: No response for cmd 50 mid 524
CIFS VFS: No response for cmd 50 mid 896
CIFS VFS: No response for cmd 50 mid 941
CIFS VFS: server not responding
CIFS VFS: No response for cmd 50 mid 1092
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: No response for cmd 162 mid 2448
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: No response to cmd 4 mid 2458
CIFS VFS: Send error in Close = -11
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: No response for cmd 162 mid 2490
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: Send error in Close = -5
CIFS VFS: Send error in Close = -5
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: Send error in Close = -5
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: Send error in Close = -5
CIFS VFS: Write2 ret -28, wrote 0
CIFS VFS: No response to cmd 4 mid 3006
CIFS VFS: Send error in Close = -11
CIFS VFS: Write2 ret -28, wrote 0
```

If I try to write to a file using Emacs or Vim, no problem. File is written to disk and I can see it in other computers or after I umount/mount the drive.

The drive is obviously not full, what is the problem? How can I make all the programs work using the NAS?

I've tried with and without the 'async' flag in 'mount -f cifs' but I still encounter the same problem. Also tried what is suggested in this link [http://forum.buffalo.nas-central.org/viewtopic.php?f=22&t=3525](http://forum.buffalo.nas-central.org/viewtopic.php?f=22&t=3525) with no success.

I've tried this on several Ubuntu machines running 8.04 and 8.10 with the same result. This issue does not come up in either Windows or Mac OS X machines connected to the NAS, they create files and modify them with no problems.

Any help to solve this is appreciated.

William.

---

### Post by wkimberly on 2009-06-10
* Test updates *

If I save the file as a new file on the NAS using Gedit or Open Office the file is saved. Then, If I modify the same file (with out closing it) and try to save it again it fails.

It never fails with Emacs or Vim, I'm thinking these applications always write the whole buffer to disk. While the other applications might do seeks to only write the modified data.

Open Office gives two errors:
- There is no space left on device
- General Error. General Input/Output Error.

Any ideas?

---

### Post by dixonstalbert on 2009-06-10
I have a dlink network drive that I set up with its windows XP software with ntfs.

"Simple Backup" and vim have no problem writing to drive, but I cannot write using gedit

Nautilus reports the file  user/group as 501-user#501 for files on the NAS

I dont have a user/ group called '501' so I will have to look into this

maybe your problem is related to file/folder permissions and/or ntfs filesystem

---

### Post by wkimberly on 2009-06-10
NFS ans SMB are different protocols. I'm not dealing with NFS.

I don't think it is because of permissions. On mounting the partition you can set the file permissions, I had them with "file_mode=0660" in the example. Other permissions (like 0777) didn't fix the problem.

That error message of "No space left on device" makes me wonder how can this happen if there is 661Gbytes available.

---

### Post by cjsg on 2009-07-30
Did you solve this in the end? I seem to have reproduced the same problem in both Kubuntu 9.04 and Mint 7 (based off 9.04).

---

### Post by wkimberly on 2009-07-30
No, I haven't solved this problem. My NAS (an Iomega Network Drive) has the capability of connecting to it using Ethernet or USB. In order to freely change files in Ubuntu I connected the drive using USB to the Linux box. Then setup Ubuntu to share the 1TB drive using samba.

It's not the optimal solution because if I need to reboot the Ubuntu box access or active transfers are denied/canceled. Also, to get good transfers speeds Ubuntu needs to be wired to the router. No wireless connection because of this :(

If anyone figures out how to solve this please post the solution.

---

