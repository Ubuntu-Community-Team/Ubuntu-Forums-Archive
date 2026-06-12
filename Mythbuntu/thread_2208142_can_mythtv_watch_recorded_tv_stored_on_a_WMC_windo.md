---
title: "can mythtv watch recorded tv stored on a WMC windows 7 PC?"
date: 2014-02-26
forum: Mythbuntu
---

### Post by sdowney717 on 2014-02-26
The location is a folder called recordedtv.

smb://lr-pc/users/Public/recordedtv is the smb folder location.

I can access it from ubuntu and play recordedtv with VLC or smplayer.

Well, I tried it and mythtv does not like it.

Is there a path name can be used?

---

### Post by sdowney717 on 2014-02-26
scott@scott-P5QC:~$ sudo mount -t cifs -o username=lr //192.168.1.7/'users/public/Recorded Tv' /mnt
Password for lr@//192.168.1.7/users/public/Recorded Tv: 
scott@scott-P5QC:~$ 

got it mounted, instructions here
[http://ubuntuforums.org/showthread.php?t=1528206](http://ubuntuforums.org/showthread.php?t=1528206)

For space in folder name, all you need do is 'folder name'

There is not a password on windows7 pc, so it prompted for password, I hit enter and it mounts in /mnt all the recorded tv

Also was hitting wall until i installed these
```
scott@scott-P5QC:~$ sudo apt-get install samba-client samba-common cifs-utils -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'smbclient' instead of 'samba-client'
```

---

### Post by sdowney717 on 2014-02-26
I can play the files in /mnt

mythtv says directory is not writable, do you know what your doing?

no, but maybe says that because it is not writable, does that matter?

---

### Post by sdowney717 on 2014-02-26
not showing up in mythtv under recorded tv

here they are in /mnt

---

