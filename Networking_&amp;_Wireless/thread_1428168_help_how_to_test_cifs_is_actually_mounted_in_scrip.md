---
title: "help: how to test cifs is actually mounted in script file"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2010-03-12
I have searched around for a while without so much as a hint of how to do what I'm looking for.  Perhaps I'm using the wrong keywords in my searches?

I would like to be able to test that a network mounted cifs(samba) share is actually mounted in a script file to do backups.  I want to do this so that when my automatic backups run they actually go to the remote location or fail.  Currently, if there is a network problem that prevents the network share from mounting, the files simply get copied to the folder (e.g. /media/backupmount) and end up filling up my small local hard drive.

---

### Post by capscrew on 2010-03-12
> **senor_smile said:**
> I have searched around for a while without so much as a hint of how to do what I'm looking for.  Perhaps I'm using the wrong keywords in my searches?

I would like to be able to test that a network mounted cifs(samba) share is actually mounted in a script file to do backups.  I want to do this so that when my automatic backups run they actually go to the remote location or fail.  Currently, if there is a network problem that prevents the network share from mounting, the files simply get copied to the folder (e.g. /media/backupmount) and end up filling up my small local hard drive.

I do this type of verification before I mount the drive (partition).  You certainly can use the same technique to verify your mounted partition.

What I do is create a [FONT="Courier New"]**readme.1st **[/FONT]text file in the directory that I am using as a mount point.  Since the file is not visible when the partition is mounted you can you a simple "if, then, else" to launch whatever.

The logic works like this: 
```
**If **the readme.1st file exists **then**
  Warn me that the drive is not powered up    
**else**
  Perform the mount routine
```


You could just as easily script this:

```
**If **the readme.1st file exists **then**
  print warning "Backup partition not mounted -- BACKUP WILL NOT CONTINUE"    
**else**
  Perform backup routine
```

Sorry for being so vague, but I am not at the host where the script is at the moment.  If you need more details I can provide them in a few hours.

---

### Post by senor_smile on 2010-03-12
> **capscrew said:**
> I do this type of verification before I mount the drive (partition).  You certainly can use the same technique to verify your mounted partition.

What I do is create a [FONT="Courier New"]**readme.1st **[/FONT]text file in the directory that I am using as a mount point.  Since the file is not visible when the partition is mounted you can you a simple "if, then, else" to launch whatever.

The logic works like this: 
```
**If **the readme.1st file exists **then**
  Warn me that the drive is not powered up    
**else**
  Perform the mount routine
```


You could just as easily script this:

```
**If **the readme.1st file exists **then**
  print warning "Backup partition not mounted -- BACKUP WILL NOT CONTINUE"    
**else**
  Perform backup routine
```

Sorry for being so vague, but I am not at the host where the script is at the moment.  If you need more details I can provide them in a few hours.

I hadn't thought of doing that.  Exactly what I needed.  Thanks!

---

### Post by capscrew on 2010-03-12
> **senor_smile said:**
> I hadn't thought of doing that.  Exactly what I needed.  Thanks!

If you need the script I can dig it up in a few hours and post it here.

---

