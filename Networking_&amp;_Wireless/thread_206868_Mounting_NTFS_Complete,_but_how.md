---
title: "Mounting NTFS Complete, but how?"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by EWek1 on 2006-06-30
I have mounted NTFS following directions found here on the forum pages...My question is why does this work?  
What are the reasons for the entries in fstab?
For example, I made this entry in fstab:
/dev/hdb1 /media/windows ntfs nls=utf8,umask=0222 0 0
What does this all mean (after the ntfs part, that is)
I am a very n00bie here, and am trying to learn about what's going on under the hood.  Is this explained somewhere?  Can you shed some light on it for me?
TIA, hopefully I can learn enough quickly enough to be able to remove the need for an NTFS partition all together!  So far so good, and it just wouldn't be possible without the forums, that's for sure! ;)

---

### Post by dalonso on 2006-06-30
from a shell type 'man fstab' without the quotes. It explains all options.

---

### Post by woedend on 2006-06-30
after ntfs is where the arguments go.  roughly/quickly
nls is national language support.  utf8 is 8 bit character encoding compatible with ascii.  This requires a lot of reading to understand(search for eithier national language support or utf8 if interested). 
umask sets the default file permissions(ie who can read, who can write, who can execute).  Im not wise enough to remember these values so I just look them up when needed.  The last two numbers are dump and pass.
Dump is a utility that examines and backs up ext2 filesystems.  I've never used it or seen it used personally.  0 means skip this, 1 means make dump use this filesystem.  Ive always used 0.
Pass is what order to check the filesystem in. (fsck)
0 means don't check, 1 should be root filesystem if you want it checked, all others can use 2(Which means do root filessytem first).  I normally use 0 here also as I don't necessarily need this feature.

---

### Post by EWek1 on 2006-06-30
OK, that's a great start.  Thanks for pointing me in the right direction.  Lots o' reading to do!

---

