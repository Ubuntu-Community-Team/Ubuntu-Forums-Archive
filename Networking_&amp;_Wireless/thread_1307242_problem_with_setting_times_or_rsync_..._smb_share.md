---
title: "problem with setting times or rsync? ... smb share"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by cedentary on 2009-10-30
I have shared a directory from the server using the 'shares-admin'
program -- it is read/write

but I get problems - for instance:

if i issue the command 'touch testfile' on the directory I get touch:
setting times of `testfile': Permission denied

If i try to untar an archive (tar -xvf) I get multiple messages
(sample):

Cannot utime: Operation not permitted
bdeditor.css
tar: bdeditor.css: Cannot utime: Operation not permitted
BdEditor-mined.js
tar: BdEditor-mined.js: Cannot utime: Operation not permitted
bgmusic.js
tar: bgmusic.js: Cannot utime: Operation not permitted
blank.html

the last (relevant) line of my fstab file on the client machine looks
like this :

//username-desktop/keep /home/username/keep smbfs rw 0 0

Can anyone advise me as to what is the problem -- something to do with
rsync yes?

---

### Post by Aearenda on 2009-11-02
Your fstab line looks too simple to me - you are not telling it what username and password to use. Maybe this will help: see the manual mount section in [this howto]("http://ubuntuforums.org/showthread.php?t=288534"), and when you have read-write access convert what works into an fstab entry.

---

### Post by cedentary on 2009-11-02
> **Aearenda said:**
> Your fstab line looks too simple to me - you are not telling it what username and password to use. Maybe this will help: see the manual mount section in [this howto]("http://ubuntuforums.org/showthread.php?t=288534"), and when you have read-write access convert what works into an fstab entry.

but it connected and worked *partially*  this to me indicates that it is not a -- username and password issue but like I said a 'timing' issue ... I have to go to sleep now but I did see something on the server (a radio check tag) that is checked for rsync (on one of the tabs for the smb share from 'shares-admin' -- I was thinking of reverting to smb to try to get it working from my NFS which I also cannot get completely working to try this out ... would that be an idea anyone ... 

l8r zzzzz - ty for responding

---

### Post by Aearenda on 2009-11-02
It probably connected as a guest, so no read-write access.

Don't forget the disk files on the server need to have write access for the user samba is using, as well as write access through the share - just like on a Windows server, where the user gets the most restrictive of the NTFS file system permissions and the share permissions.

Sleep well!

---

### Post by cedentary on 2009-11-02
//username-desktop/keep /home/username/keep smbfs rw 0 0

i think this also requires the option 'sync' as in (rw,sync):

//username-desktop/keep /home/username/keep smbfs (rw,sync) 0 0

will try it shortly

---

### Post by cedentary on 2009-11-02
> **cedentary said:**
> //username-desktop/keep /home/username/keep smbfs rw 0 0

i think this also requires the option 'sync' as in (rw,sync):

//username-desktop/keep /home/username/keep smbfs (rw,sync) 0 0

will try it shortly


ok -- have tried it -- works --- should have used the line above 

thanks for feedback aearenda

should have read the nfs HOWTO for advice on how to manually configure the client

---

