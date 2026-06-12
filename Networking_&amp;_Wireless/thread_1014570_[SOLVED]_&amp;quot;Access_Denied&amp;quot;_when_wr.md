---
title: "[SOLVED] &amp;quot;Access Denied&amp;quot; when writing to samba shares from applications"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by gdselzer on 2008-12-18
I am hoping that someone can point me to some small, dumb thing I'm missing here.  I find that I am mostly unable to write directly to a samba share I have setup from applications.  However, if I access the share through Nautilus, I can write, delete, etc. with no problems.

For example, I would like to rip a couple CDs directly to the music directory on my network samba share.  From Sound Juicer, I get the following error popup when I hit "Extract."

> Sound Juicer could not extract this CD.
Reason: Could not open vfs file "file:///entertainment/music/Midnight_Oil_-_Diesel_and_Dust/.01._Midnight_Oil_-_Beds_Are_Burning.flac" for writing: Access denied.

But, and here's the part I REALLY don't get.  If I wait 30 seconds or so, an empty folder with the right name shows up in the directory.  Then, if I hit extract again, it rips without errors.  Huh!?  I like that it works, but this is a silly way to do things.  Do I have a setting wrong somewhere?

The relevant line from /etc/fstab is:
```
//homeserver/entertainment	/entertainment	cifs	credentials=/root/.smbcreds,nobrl,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
```

Thanks for the help.

---

### Post by gdselzer on 2008-12-19
bump

---

### Post by gdselzer on 2008-12-20
bump

---

### Post by mpokrywka on 2008-12-20
Try changing "homeserver" in fstab to real server IP, like:
//192.168.0.1/entertainment	/entertainment	cifs	credentials=/root/.smbcreds,nobrl,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
Maybe smb name resolving is slow?

---

### Post by gdselzer on 2008-12-20
Made the change, re-booted to make sure everything was fresh, and I still get the same error and results.

---

### Post by mpokrywka on 2008-12-21
Sorry, I missed most important part: works in nautilu w/o problem.
So server name should stay as //homeserver/entertainment

Maybe try adding "noperm" to mount options - after **man mount.cifs** - typically only needed when the server supports the CIFS Unix Extensions but the UIDs/GIDs on the client and server system do not match.

---

### Post by gdselzer on 2008-12-21
Ah ha!  mpokrywka, you are a genius!  That seemed to have done it.  I knew it was some small dumb thing I was doing.

Just so I understand, by default the client machine will try to manage permissions?  So I have to pass noperm if the UIDs and GIDs on the client machine are different than the host?  Then that will allow the server to manage things?

Thanks so much

---

