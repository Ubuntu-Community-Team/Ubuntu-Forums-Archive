---
title: "mouting samba drive"
date: 2006-05-19
forum: Networking &amp; Wireless
---

### Post by resnostyle on 2006-05-19
i have used the following commands and show the errors I have recieved:

mount -t smbfs -o username=administrator //server/share /mnt/samba

10685: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


mount -t cifs -o username=administrator //server/share /mnt/samba

mount error 13=permission denied
refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

i imagine because i havent set permissions to it?

---

### Post by resnostyle on 2006-05-19
does no one know how to mount a samba drive?

---

### Post by JNowka on 2006-05-20
Ok I see the command you are using and I am going to suggest using sudo with it as follows.

sudo mount -t smbfs -o username=administrator //server/share /mnt/samba

make sure you have put your login name instead of administrator, server is your computers hostname, and share is what you want the folder to be called.

before you put in the command enter "cd /mnt" into the terminal and make sure the samba directory exists.  if not enter "sudo mkdir samba" into the terminal.

I have not used the smbfs mount command myself but I have been setting up a samba workgroup at my house, and its working quite well. I hope I have helped.

---

### Post by DarkNemesis618 on 2006-05-24
I get this message

mount: wrong fs type, bad option, bad superblock on //kpwserver/music,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

any ideas?  my share is being hosted on a Fedora Core 5 machine with Samba

---

### Post by ramdez on 2006-06-01
are you sure you have smbfs installed on your client machine?

---

### Post by mike4ubuntu on 2006-06-20
Word has it, that everybody is supposed to switch to CIFS instead of SMBFS.  SMBFS is being depricated in newer versions of the kernel.

see

[HTML]<a href="http://lwn.net/Articles/183693/">Future of SMBFS</a>[/HTML]

---

### Post by liamspelman07 on 2007-02-03
> **resnostyle said:**
> i have used the following commands and show the errors I have recieved:

mount -t smbfs -o username=administrator //server/share /mnt/samba

10685: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


mount -t cifs -o username=administrator //server/share /mnt/samba

mount error 13=permission denied
refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

i imagine because i havent set permissions to it?

Are You running this as root?

---

