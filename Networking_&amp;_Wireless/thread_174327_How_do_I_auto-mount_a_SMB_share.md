---
title: "How do I auto-mount a SMB share?"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by pbb on 2006-05-11
I've got the following line in /etc/fstab:

```
//p4-3000/D /media/fat smbfs guest,uid=peter,iocharset=utf8,codepage=unicode,unicode  0  0
```

As far as I understood it, this should auto-mount the share. However, when I reboot the machine, the mount isn't there. I have to issue "sudo mount -a" to get the mount into place.

Is there anything I am overlooking? The P4-3000 machine is already running before the Ubuntu machine is booted.

(To be precise, it is actually Kubuntu running inside VMWare on the P4-3000 machine, but I don't think that should make any difference.)

---

### Post by louis_nichols on 2006-05-11
add "auto" after the last unicode, like this:

```
//p4-3000/D /media/fat smbfs guest,uid=peter,iocharset=utf8,codepage=unicode,unicode,auto  0  0
```

---

### Post by pbb on 2006-05-11
Okay thanks, I didn't know it was that simple. Do you realize that actually neither UbuntuGuide nor the Ubuntu Wiki mention this "auto" parameter in the chapters on auto-mounting shares ...... ?

---

### Post by louis_nichols on 2006-05-11
They probably have a good reason. The network might not always be up and then you run the risk of your pc freezing at startup because it's unable to mount samba shares.

I get this when my network connection is down at the step where my pc tries to sync the clock with an ntp server. I press Ctrl+C to skip that. In case you need this...

---

### Post by louis_nichols on 2006-05-11
ooops. double post.

---

### Post by pbb on 2006-05-15
Hmm... I modified the line in fstab, it now reads

```
//p4-3000/D     /media/fat      smbfs   guest,uid=peter,iocharset=utf8,codepage=unicode,unicode,auto  0  0
```

But the network share is still not automounted on startup. Am I overlooking anything?

---

### Post by louis_nichols on 2006-05-15
[QUOTE=pbb]Hmm... I modified the line in fstab, it now reads

```
//p4-3000/D     /media/fat      smbfs   guest,uid=peter,iocharset=utf8,codepage=unicode,unicode,auto  0  0
```

But the network share is still not automounted on startup. Am I overlooking anything?[/QUOTE]
according to [this page]("http://gentoo-wiki.com/HOWTO_Setup_Samba") it looks ok. The onlly difference is that here auto is the first option. I wondr if that could be it.... I can't test, unfortunatelly.

---

### Post by pbb on 2006-05-15
No, also with "auto" as first parameter, it doesn't auto-mount. Maybe a VMWare specific problem?

But, since I can mount using "sudo mount -a", is there a way to "autoexecute" this command on system startup?

---

### Post by Cadeucean on 2006-05-16
I have tried this but when I do the "sudo mount -a" command I get the following error:

mount: wrong fs type, bad option, bad superblock on //TECH-GLENS/Share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any ideas what I'm doing wrong?

---

### Post by changlinn on 2006-05-16
//server/share /mnt/share smbfs credentials=/home/me/logon,uid=1000,gid=106 0 0
Where uid=1000 is my username and gid=106 is the admin group. The folder pre mounting in the /mnt directory is owned by me and group owned by root.
In the logon file in me's home directory is the below
username=smbusername
password=smbpassword

This all works fine and mounts on boot.

---

### Post by tflanders on 2006-06-11
None of these options work to "auto" mount my shares because I use ethtool inside my /etc/rc.local which causes the network to be unavailable when it tried to mount these shares within /etc/fstab.

Using the above with mounts inside fstab I added a auto mount from gnome sessions options

System->Preferences->Sessions

I added a command like this to echo my sudo password to the sudo command

yoursudopassword > sudo mount -a

Example:
secretpasswd > sudo mount -a

This will then mount whatever is in your /etc/fstab when gnome starts.

---

### Post by changlinn on 2006-06-12
I don't think it is such a good idea to put your sudo password in a file maybe just write a script to mount the shares and have an icon that calls gksudo "script"

---

### Post by shujimi on 2006-06-27
[QUOTE=Cadeucean]I have tried this but when I do the "sudo mount -a" command I get the following error:

mount: wrong fs type, bad option, bad superblock on //TECH-GLENS/Share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any ideas what I'm doing wrong?[/QUOTE]

I may be way off here because this is my first post but I was having the same problem but I realized I didn't have the smbfs installed.  I installed it and everything started working.

Here's the command:
sudo apt-get install smbfs

---

### Post by l.capriotti on 2006-06-28
May I advice to use smb4k, that can auto-mount SMB shares automatically at startup?

Cheers,

Luigi

---

