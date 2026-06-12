---
title: "nfs locking files?  Cannot open for editing, or open firefox / thunderbird"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by j_galt on 2010-12-12
Server - Ubuntu 10.04.1 lts
Client - Kubuntu 10.10

When I try to open any nfs-mounted file using OpenOffice, I get a pop-up window titled "Document in Use".  The text of the message is:

"Document file 'abcde.odt' is locked for editing by:

Unknown User

Open document read-only or open a copy of the document for editing."

I then have three options - <Open Read-Only>, <Open Copy>, & <Cancel>

If I cp any of these files from the mounted directory to my home dir (not mounted), I can open them without problem.

Also, my firefox & thunderbird date are in this mounted directory as well (sym links to ~dan/.mozilla & ~dan/.thunderbird).  Both of these apps hang when trying to open, leaving two processes behind that need to be manually killed.  Again, cp'ing the data out of the nfs-mounted dir onto a local dir resolves the issue, so I am 100% confident there is nothing missing or corrupted in the firefox &/or thunderbird data...

I've spent hours trying to figure this out - please help...

Thanks,
Dan

----------------------

relevant entry in /etc/fstab:
server:/nfs/dan/Documents    /home/dan/Documents    nfs    defaults    0 0

relevant entry in server's /etc/exports:
/nfs/dan/Documents    client(rw)

---

### Post by gmargo on 2010-12-13
Are the user id numbers for "dan" the same on both machines?  How about group id?

And what about normal command line access?  Can you cd to the directory?  Can you "touch" a file to create it?

---

### Post by j_galt on 2010-12-13
Both the user & group id's on the server & the client are the same.

Yes I can 'cd' to the directory & 'touch' (and modify) a file using vi.

Thanks,
Dan

---

### Post by gmargo on 2010-12-13
Good timing ... I just got a very similar error trying to open a spreadsheet on a nfs mounted filesystem.  Looking in the directory, I see a hidden lock file:

```

$ ls -lagG | grep Computer_costs.ods
-rw-r--r--   1       82 Jun 17 14:23 .~lock.Computer_costs.ods#
-rw-r--r--   1    18787 Jun 17 14:23 Computer_costs.ods

```I removed the lock file ".~lock.Computer_costs.ods#" and now it opens.

---

### Post by j_galt on 2010-12-13
No hidden lock files here...

Still looking for *some* kind of explanation, or a pointer in the right direction...

---

### Post by byrong on 2011-01-21
I have the exact issue.  File permissions are ok.  Not sure what is up.  

It only appears to occur on Open Office files on my NFS.  I changed the file /usr/bin/soffice properties SAL_ENABLE_FILE_LOCKING=0
           export SAL_ENABLE_FILE_LOCKING
Where 0 was 1 I changed to 0 but it had no effect.  I can copy the files to my desktop and work on them but if I copy them back to my NFS drive and try to open them I get the same:
Document is locked by:unknown user.

No hidden lock file.

Any ideas?

Thank you.


Ok, search search search and nothing.  Post on here and I found the answer for me.  [http://forum.synology.com/enu/viewtopic.php?f=14&t=13830](http://forum.synology.com/enu/viewtopic.php?f=14&t=13830)

I ended up putting "nolock" at the end of my nfs mount and it works now.  

Ubuntu rocks.

---

### Post by buck2825 on 2011-03-26
Same issue here, help! anyone?

---

### Post by no-thing on 2011-03-29
help migth be here:
[http://forum.qnap.com/viewtopic.php?f=35&t=42198&p=188876#p188876](http://forum.qnap.com/viewtopic.php?f=35&t=42198&p=188876#p188876)
(see last reply)

this is what helped me to solve my nfs-issue with locked OpenOffice files.

cheerio,
no-thing

---

### Post by buck2825 on 2011-04-14
so the link above didn't open any new doors for me as i'm running 10.04 and already have the package, that the post said to install, installed.  

Regardless, Thank You for your help!!!!

I give up... I'm switching to samba. there seems to be more help out there for samba because of windows and all.  

Tip you will need to 

$sudo apt-get install smbfs

if you want to use samba with some of the directions found in the official Ubuntu documentation.

---

