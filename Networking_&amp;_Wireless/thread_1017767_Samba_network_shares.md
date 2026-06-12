---
title: "Samba network shares"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by chrisinspace on 2008-12-21
I'm having a weird issue with samba shares.  I can map the network drives from my W2k3 Server just fine.  I can access the files and folders.  The issue is that I have full permissions to some sub-folders in a shared folder and restricted permissions to others.  The permissions are applied at the top level folder and inherited by the sub-folders so there isn't any variation to assigned permissions.  I used a smbcredentials file to apply an administrator username and password when Ubuntu mounts the folders and gave all accounts the full read/write permission using chmod 777.  I am attaching a screen cap.  The folders with red X's are the folders with reduced permissions.  I am also pasting my fstab file below.

-------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=87202c58-5e69-42ed-894b-1b9aa5d45e4f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=184fecc5-02a8-49c3-a6c8-3f30f5481927 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2	/media/share	ext3	defaults,relatime	0	0
//homeserver/Files	/mnt/network	cifs	credentials=/root/.smbcredentials,file_mode=0777,dir_mode=0777	0	0
//homeserver/Media    /mnt/media cifs  credentials=/root/.smbcredentials,file_mode=0777,dir_mode=0777  0    0
none	/proc/bus/usb	usbfs	devgid=1000,devmode=664	0	0

---

### Post by chrisinspace on 2008-12-29
Has anyone seen this issue or anything similar?  It's not a show-stopper for me, but it is rather annoying.

---

### Post by chrisinspace on 2009-01-07
Week 2, bump 2.  

Can anyone help?  I'm at a loss...

---

### Post by jimv on 2009-01-07
These folders are on the Win2k3 Server?  If so, get on your server and pull up the Properties screen on the parent folder, and click the Security tab.  Click the Advanced button, and check the box that says "Replace permissions on all child objects with entries shown here that apply to child objects."  Click Apply.

Then check the share from your Ubuntu machine.

---

### Post by chrisinspace on 2009-01-07
Thanks for the response, jimv.  The sub-folders in my Media shared folder were already inheriting their permissions from their parent.  I tried your suggestion just to see what would happen, but there was no change.  I checked the folder permissions on the W2K3 server for 2 folders: one that was having the problem and one that was not.  When I look at the Security tab for those subfolders on the Media share, they look identical. Both are inheriting the permissions of their parent folder 'Our Music'.  Could something be going on with CIFS?  I have seen that there have been updates to the Samba packages lately.  Should I change my fstab to use smbfs?  I was using that originally, but it flaked out on me a couple of years ago.  Someone in the forums suggested I use CIFS and I've been on it ever since.

---

### Post by dmizer on 2009-01-07
Try including the "nounix" opition in your mount string like so:
```
//homeserver/Files /mnt/network cifs credentials=/root/.smbcredentials,[COLOR="Red"]nounix,[/COLOR]file_mode=0777,dir_mode=0777 0 0
```

---

### Post by jimv on 2009-01-08
Switch to FAT32 instead of NTFS, lol.

---

### Post by chrisinspace on 2009-01-08
> **dmizer said:**
> Try including the "nounix" opition in your mount string

I'll give that a shot when I get home tonight.  Thanks for the suggestion.

---

### Post by chrisinspace on 2009-01-08
> **jimv said:**
> Switch to FAT32 instead of NTFS, lol.

I am slowly, but surely, shedding M$ from my life.  Maybe later this year, I'll find the time to switch to EXT4.  :D

First I have to deal with 2 grad school projects and a compliance audit at work.  Oh well...some day...

---

