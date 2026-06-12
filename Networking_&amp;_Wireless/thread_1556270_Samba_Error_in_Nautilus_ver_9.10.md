---
title: "Samba Error in Nautilus ver 9.10"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by justaguy168 on 2010-08-19
I am running Ubuntu 9.10.  I am trying to make a folder shareable so a windows XP computer can have both read and write access to the folder.  I am using Nautilus to configure access and I get the error:  
> Samba's testparm returned error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
    No such file or directory
Error loading services.
This is the screen before selecting read/write access
[ATTACH]166880[/ATTACH]

This is the screen after unsuccessfully selecting read/write access.
[ATTACH]166881[/ATTACH]

I have attempted this before using this facility and I do have read access to the folder using the windows computer.  But I need **read/write** access.

I've tried to RTFM and look through the forums.  The samba service is running:
> kjen@LinuxServer:~$ sudo service samba status
 * nmbd is running
 * smbd is running
kjen@LinuxServer:~$At the command line Samba's testparm command kicked out many errors.  This is puzzling because I did not edit the smb.conf file, Nautilus did.  The parameters that testparm complains about appear to have correct syntax according to the [COLOR=Blue][Samba Team Website]("http://www.samba.org/samba/docs/using_samba/ch06.html")[/COLOR] .

I also went into the Synaptic package manager and tried to re-install Samba with no effect.  I would install the 10.04 LTS version but I've heard that has problems too.

Is this a permissions issue?  The user I am logged onto has "permission to configure the system" checked under system-->administration-->users and groups.

Advice?  Please.

---

### Post by Morbius1 on 2010-08-19
Open up synaptic ( package manager ) and make sure the following package is installed:
```
samba-common-bin
```

---

### Post by sadiepaige01 on 2010-08-19
I'd hardly call manually restarting Nautilus after it has crashed a work-around. 
 You could perhaps write a quick script which checks user-space for the existence of the Nautilus process every so many seconds, and starts it again after the process disappears. Again, not a workaround, but would make crash recovery more seamless.

---

### Post by justaguy168 on 2010-08-19
sadiepaige01 I'm not sure I understand your reply.  I'm not sure how to check or restart the nautilus process.

---

### Post by justaguy168 on 2010-08-19
Morbius1,  There appears to be an updating problem.  I tried to follow your suggestion and then some and updated all packages having to do with samba.  The ones I checked  were:
> samba
samba-doc
samba-common
samba-doc-pdf
samba-dbg
samba-common-bin
samba-tools
libpam-smbpass
python-smbc
smbfs
smbclient
nautilus-share
libsmbclient
libsmbclient-dev
I then got many messages like this one:
> 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.3_i386.deb)
  404  Not Found [IP: 91.189.88.30 80]
I then tried to update my software and got many error messages one of which was exactly the same as above.

How do I resolve this problem?

---

