---
title: "autofs won't mount nfs shares: .hidden?"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by MyD0j0 on 2012-02-11
hey, all, looking for some assistance in getting some nfs shares to mount using autofs (i'm on a laptop and can't use fstab).  The shares mount manually.

when i issue automount -f -v and try to access any of the mounts, i wind up with 

```

attempting to mount entry /mnt/CentralD0j0/.hidden
key ".hidden" not found in map source(s).
failed to mount /mnt/CentralD0j0/.hidden
attempting to mount entry /mnt/Eric/.hidden
key ".hidden" not found in map source(s).
failed to mount /mnt/Eric/.hidden

```auto.master
```

/mnt/CentralD0j0    /etc/auto.centrald0j0
/mnt/Eric        /etc/auto.eric

```auto.eric
```

/mnt/Eric    -fstype=nfs4    192.168.1.100:BigDisk/NetUsers/Eric

```auto.centrald0j0
```

/mnt/CentralD0j0    -fstype=nfs4    192.168.1.100:BigDisk/MultiMedia

```

---

### Post by MyD0j0 on 2012-02-11
bump

---

### Post by MyD0j0 on 2012-02-13
no help for such a common tool?

---

### Post by MyD0j0 on 2012-02-29
Could having symbolic links pointing to /mnt/CentralD0j0 and /mnt/Eric have anything to do with the problems?

---

### Post by Anubis on 2013-05-01
I'm not having any luck either.

key ".hidden" not found in map source(s).
Starting automounter version 5.0.7, master map /etc/auto.master
using kernel protocol version 5.02
mounted indirect on /home/anubis/Music with timeout 300, freq 75 seconds
attempting to mount entry /home/anubis/Music/.hidden
key ".hidden" not found in map source(s).
failed to mount /home/anubis/Music/.hidden
re-reading map for /home/anubis/Music

[https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/1050021](https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/1050021)

13.04

---

### Post by Anubis on 2013-05-01
I got further.

It mounts the share in the dir but in a folder named .hidden?!?

Why?:confused:

---

### Post by MyD0j0 on 2013-05-02
> **Anubis said:**
> I got further.

It mounts the share in the dir but in a folder named .hidden?!?

Why?:confused:


I wound up getting help from someone who gave me the following instructions and it works for me with far, far less hassle:

[CODE]
Run:

gksudo gedit /usr/bin/mountsambashares; sudo chmod +x /usr/bin/mountsambashares


Add these 3 lines:


#!/bin/bash
sleep 30
mount -t cifs //<server>/<share1>  /mnt/<share1> -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
mount -t cifs //<server>/<share2>  /mnt/<share2> -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
mount -t cifs //<server>/<share3>  /mnt/<share3> -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777


Save the new file and close gedit, then run:


gksudo gedit /etc/rc.local


and ABOVE the exit 0 line add:


mountsambashares &


The ampersand is important. This will make the script run as root (needed for mounts which users cannot do at CLI) but if the script is not backgrounded (which is what the ampersand does) then it will simply delay the boot 30 seconds and nothing more. By backgrounding the script, it gives the OS enough time to get loaded and network manager to do it's thing. If the sleep is not long enough, simply edit the value.
[CODE]

Good luck.  If you get autofs to work fully, though, I'd like to know about it for future use.

---

