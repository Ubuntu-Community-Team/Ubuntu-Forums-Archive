---
title: "How do i sync netbook / nas/ laptop  file changes"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by geekyhawkes on 2009-02-13
Hi all;

im still getting to grips with ubuntu after using it as my only os for about 6 months.  I have a netbook and laptop (main PC) that use wireless to connect to my nas  (mounted at /media/nas on each machine).  

I work away often and I would like someway that when i bring my netbook back it can "sync" a folder that is local, with a folder on the nas.Ideally I would like the process to be automatic when the netbook reconnects to my home wireless (in the same way as my nas auto-mounts once my wireless is in range).

Thanks for your help, Im sure there must be a script or offline folder style setting, im just too stupid to find it.

---

### Post by k3rnelmustard on 2009-02-13
I'm not totally sure how to do it, but maybe I can push you in the right direction.  The app you want is probably rsync, it reads/copies incremental changes.  Use it like this:

```

rsync -rt /folder/to/sync/from /folder/to/sync/to

```

The r makes it recursive, the t preserves timestamps.  It will only copy what's different.

As far as having this work automatically, try adding ur rysnc command to /usr/libexec/hal-system-storage-mount or whatever it's called on ubuntu.  Hopefully this is helpful!

---

### Post by geekyhawkes on 2009-02-15
Thanks, this sounds like roughly the thing im after.  Im just not sure where to add the command in ubuntu to get it working automatically?  

Also, presumably i need 2 statements, one to pull the files from the nas and one to push the files from the laptop?

---

### Post by eldragon on 2009-02-15
unsion is the software you are looking for, it does just that, syncs changes bothways.

im not sure how to have it done automatically with the NM, but it should be easy to include it in a script.

---

### Post by geekyhawkes on 2009-02-17
Thanks I will give unsion a go and see how i get on.  I feel some google-ing of linux scripts coming on!

EDIT:  Where can i find Unsion?  Its not listed in my add remove, do you have the repository to hand?

---

### Post by geekyhawkes on 2009-02-19
Can anyone help me find unsion?

---

### Post by jonobr on 2009-02-19
Go to System->Administration- Synapitc package manager 
if you type unison in search you should see it.

---

### Post by k3rnelmustard on 2009-02-19
I believe it was a typo.  Try 'unison'

---

### Post by geekyhawkes on 2009-02-20
Thanks, makes more sence now!

---

### Post by funacide on 2009-09-08
I have s very similar question, did you get Unison to work for you and if so how?

Thanks

---

### Post by exup1000 on 2010-02-10
Hi

I tried to use the command above but connecting to a network share on a windows machine. I can browse the drive in Nautilus ok so its not a permission thing, maybe just how I should define the command.

rsync -rt smb://testmce01/d$/TESTBACKUPMCE /media/windows2/TESTBACKUP

Theres a long pause then I get the error

ssh: connect to host smb port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(600) [receiver=3.0.6]

I get the funny feeling I need to use SSH. (Which I know nothing about) 
All I am trying to do is back up network files to my Ubuntu machines.

I looked at Unison which starts off ok but then the tutorial says if you want to back up network drives use SSH, the link then takes you to a tutorial on SSH and the learning curve suddenly goes through the roof.

All I was thinking of was Robocopy type commands within a batch file.

Any suggestions.

Cheers

---

### Post by k3rnelmustard on 2010-02-10
You'll need to mount that samba share first, then you can use rsync just like robocopy.

mount.cifs //testmce01/d\$/TESTBACKUPMCE /mnt/mySMBFolder -o user=YOURSMBUSERNAME

* NOTE: the '\' preceding the $ may or may not be necessary to escape it.

then, you can just rsync -rt filesToBackup /mnt/mySMBFolder.  You could also set up an ssh server on the windows machine with the smb share, but this is probably simpler, you just may need to install something to get the mount.cifs command.

---

### Post by exup1000 on 2010-02-12
Hi k3rnelmustard

many thanks, got it to work nicely, great tips. I have now started to build my backup script. 
Anyway I quickly looked up how to create a batch like file.
I execute it from a command line and works well but its a bit blind, so my question is....

how do I pipe the progress of the sync to the terminal window?

Below is my code

```
rsync -rt /mnt/TESTL/Users/USERX/Documents /media/windows2/TESTBACKUP

```

Being new to Linux and Ubuntu its great fun starting to learn this stuff. 

Cheers

##Edit - I answered it myself googled the options and I have not the following code

```
rsync -rt --progress -vv /mnt/TESTL/Users/USERX/Documents /media/windows2/TESTBACKUP

```

Still it would be nice to calculate the over all progress of the entire copy but that would be next to impossible?

---

### Post by k3rnelmustard on 2010-02-12
yeah, I'm not sure about that one.  If it's not obvious from the rsync options, I'm not really sure what you might do about it.  My guess is that it just checks / runs files in that order, one-at-a-time.  Meaning, it's not going to go through the entire list of possible files and get a list of what needs to be changed, then go through this new list updated them.  I'm guess instead it only goes through all the possible files one time, only changing what needs to change.  If that's true (I'm certainly not sure that it is) there's no way for it to know how much longer it has to go.  Just a guess though.

---

### Post by h0bbe on 2010-10-15
I would love a HOWTO on this...

---

