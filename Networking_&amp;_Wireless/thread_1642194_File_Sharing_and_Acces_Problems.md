---
title: "File Sharing and Acces Problems"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by finito on 2010-12-10
I have a 64-bit Maverick Install

I am sharing two folders over the network.

One of these is a new Folder (After Format) My Downloads Folder in Home.

This is fine and can be accessed normally.

There is another Folder in another Drive that was static as in The Drive wasn't formatted. The Videos Folder.

When trying to access this folder it goes into a loop asking the authentication credentials over and over again.

I don't get it.

I tried to apt-purge samba.

No use.

this is the Error in /var/log/samba/

[2010/12/08 14:33:17.889394,  0] param/loadparm.c:8686(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/videos failed. Permission denied


Password is correct cause it works for the other share.

Any help is appreciated.

---

### Post by finito on 2010-12-10
Found Solution
[http://ubuntuforums.org/showthread.php?t=1636803&highlight=samba+problems](http://ubuntuforums.org/showthread.php?t=1636803&highlight=samba+problems)

sudo smbpasswd -a [username]

---

