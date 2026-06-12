---
title: "Having problems mounting win shares on new install"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by schwim on 2009-10-16
Hi there everyone,

I've got a brand spanking new install of Ubu and am trying to get it up to speed before retiring my old machine.  One of the things I need to do is to mount three win shares.  I opened up /etc/fstab on my current work machine and copied/pasted the info into ubu's:

> 
//192.168.0.199/Websites /mnt/websites cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
//192.168.0.199/Audio /mnt/audio cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
//192.168.0.199/General /mnt/storage cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0


saved and ran sudo mount -a:

> 
mount: wrong fs type, bad option, bad superblock on //192.168.1.199/Websites,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //192.168.1.199/Audio,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //192.168.1.199/General,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I'm guessing that I've neglected to install a needed dep or app to do this, but am not sure what it is.

Could someone help me with what I need to do to mount these shares?

thanks,
json

---

### Post by schwim on 2009-10-16
Sorry, I should have added:

dmesg output:

> 
[13162.328295]  CIFS VFS: No username specified
[13162.328298]  CIFS VFS: cifs_mount failed w/return code = -22
[13162.328477] CIFS: Unknown mount option codepage
[13162.328480] CIFS: Unknown mount option unicode
[13162.328481]  CIFS VFS: No username specified
[13162.328483]  CIFS VFS: cifs_mount failed w/return code = -22
[13162.328556] CIFS: Unknown mount option codepage
[13162.328559] CIFS: Unknown mount option unicode
[13162.328560]  CIFS VFS: No username specified
[13162.328562]  CIFS VFS: cifs_mount failed w/return code = -22


the fstab entries I posted work fine for mounting the share onto my Dreamlinux install and also worked in Linux Mint.

thanks,
json

---

### Post by sirtrent on 2009-10-16
Make sure you have smbfs installed, also try removing the 'codepage=unicode' option from fstab, and you may need to add the option 'username=guest' or so

---

### Post by schwim on 2009-10-16
The installation of smbfs solved my problem.  Thanks so much for your help!

thanks,
json

---

### Post by steve745 on 2011-07-31
This answer worked on Natty for me Thanks

---

### Post by perry6272 on 2012-01-17
Thanks sirtrent.  I was having the exact same issue as the poster and smbfs worked immediately for me.

---

### Post by llllskywalker on 2012-01-28
good call - installing smbfs worked for me too!

---

