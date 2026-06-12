---
title: "Copying directories to cifs mount fails"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by Lemon on 2009-09-20
I am getting some odd behavior from my ubuntu when trying to copy a file from the ubuntu computer to a mounted cifs drive.

While copying a number of folders to the cifs drive, the first folders are copied successfully, but at some point it fails and the rest of the folders ends up as zero size *files* with the same names as the folders. :confused:

These files:
[LIST]
[*]Can be seen from the Ubuntu computer
[*]Cannot be deleted from the ubuntu computer
[*]Cannot be seen from a windows computer
[*]Can only be deleted if i unmount the drive (usb drive connected to NAS), mount the drive on a windows computer and run the disk error checking feature in windows.
[/LIST]
This is the line in fstab that mounts the disk:
[SIZE="2"][COLOR="Blue"][FONT="Courier New"]//192.168.15.1/netdisk /home/user/Netdisk   cifs  username=user,password=pass,iocharset=utf8,nounix,file_mode=0777,dir_mode=0777 0 0[/FONT][/COLOR][/SIZE]

---

### Post by callan79 on 2009-09-20
> **Lemon said:**
> While copying a number of folders to the cifs drive, the first folders are copied successfully, but at some point it fails and the rest of the folders ends up as zero size

This is the line in fstab that mounts the disk:
//192.168.15.1/netdisk /home/user/Netdisk   cifs  username=user,password=pass,iocharset=utf8,nounix,file_mode=0777,dir_mode=0777 0 0



Hi Lemon,

I had a similar problem a while back, in could quite possibly be the same issue.

Here's my fstab line ...

```
//192.168.7.2/media /media/media cifs auto,user=me,password=mine,uid=myuser,gid=mygroup,dir_mode=0770,file_mode=0770,nounix 0 0
```

You'll notice the UID and GID options in there. You'ce already got file_mode and dir_mode=0777 which is cool, but using the uid and gid actually can make the mount point owned by you, instead of root. And then file/dir mode 0770 prevents anyone else accessing it.

But the big one for me was the NOUNIX option. Without this, ubuntu would try to negotiate permissions with my NAS. Of course the NAS does not support full samba, only partial samba, hence it would all fail. With NOUNIX it works fine.

Also just a tip - I noticed you put your fstab line in blue. It's probably best to put that between CODE and /CODE tags instead, like I have. Reember to put [ and ] around the CODE and /CODE.

Let us know how the NOUNIX thing goes!

Cheers
Callan

---

### Post by dmizer on 2009-09-20
If that doesn't work, please see the troubleshooting section in my CIFS tutorial. It's the second link in my sig.

---

### Post by Lemon on 2009-09-22
> **callan79 said:**
> You'll notice the UID and GID options in there. You'ce already got file_mode and dir_mode=0777 which is cool, but using the uid and gid actually can make the mount point owned by you, instead of root. And then file/dir mode 0770 prevents anyone else accessing it.

I already found the NOUNIX option, which made the whole browsing experience much quicker.

The UID and GID options are nice too... unfortunately i still have the same problem.

**dmizer**: your guide was the one i followed in the first place, getting the hint of NOUNIX.

What i see happening is:

[LIST]
[*]Ubuntu creates directory.
[*]Directory ends up not existing, neither as a directory nor as a file.
[*]copying the files halfway succeeds: The data is copied, but can't be found anywhere on the disk - except when doing the disk scan in windows afterwards.
[/LIST]

**EDIT**: I just tried copying some files using Midnight Commander - that seemed to work. Maybe it's just Nautilus that gives me trouble?

**2. EDIT**: No, as soon as i left the directory and entered it again, the folders had reverted to non-files.

**3. EDIT**: I must conclude that whatever error i'm getting, it's not caused directly by the Ubuntu box. When copying the directories they look okay at first, both from Ubuntu *and looking from a windows computer* - but after a moment they are dead files and not directories. So the ubuntu computer is doint it's part but the NAS is messing it up afterwards.

---

### Post by dmizer on 2009-09-22
Ah hah. You're using a NAS device? What NAS device are you using (make and model)?

---

### Post by Lemon on 2009-09-29
I WAS using a Linksys WRT610N with firmware 1.00.03.15. The linksys has a TrekStor eksternal USB harddrive attached.

Now i've downgraded to firmware 1.00.00.18 instead, and it seems to work fine (although slightly slower).

Edit: No luck - apparently the problem persist in a slightly other form: the directories that i copy are empty from the ubuntu box, and not accessible from the windows box.

---

### Post by dmizer on 2009-10-01
So the WRT610N has a USB port for attaching a hard drive?

If so, does the WRT610N support FTP access to the USB drive?

Edit:
Answered my own questions.

Yes, your router does have a USB port for external storage. And, yes your router does support FTP access to your disk.

So, I suggest that you try FTP instead of Samba for this. You won't have to open any ports on the router, FTP access will only be available on your LAN. The manual for your router should give you more information about this. If you don't know where it is, you can get a copy here: [http://www.linksysbycisco.com/US/en/support/WRT610N/download](http://www.linksysbycisco.com/US/en/support/WRT610N/download) (chapter 3)

---

