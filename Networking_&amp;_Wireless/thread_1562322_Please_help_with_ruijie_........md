---
title: "Please help with ruijie ......."
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by DrHarshrao on 2010-08-27
i am using ubuntu 10.04 i am having problem connecting to internet b'coz it require authentication with university server . actually the problem solution have been solved on this thread [http://ubuntuforums.org/showthread.php?t=681557&page=2](http://ubuntuforums.org/showthread.php?t=681557&page=2)
but since it was done on older version of ubuntu i am not able to configure it correctly.I have following problems 
1) I am not able to copy the file myxrgsu file to bin folder,i dont know whats the problem .I did it successfully on ylmf OS .
2) also not same problem of copying file with 
libstdc++5 file 

kindly help me

---

### Post by lukeiamyourfather on 2010-08-27
Are you copying the file as root (e.g. with sudo)? Those directories don't have permissions for a regular user.

---

### Post by DrHarshrao on 2010-08-27
i am new to ubuntu .......so i dont know much ......actually i directly copied these file in ylmf os ,it very much like windows xp ........but i dont know how to copy these files in ubuntu......

---

### Post by lukeiamyourfather on 2010-08-27
There are two ways to copy the files. One is to copy the files in a terminal using traditional Linux commands (which I would recommend) and the other is to copy the files using a graphical file manager as the root user.

```
sudo cp /home/user/whateverFile.ext /opt/somewhere/
```

The "sudo" means to run the command as root user (Windows equivalent of Administrator). When it prompts for a password enter the password for the current user (your password). The "cp" part is the copy command. The first path is the source and the second path is the destination. If you run "cp" without the "sudo" then you won't have root privileges.

```
gksudo nautilus
```

Warning! That will launch the graphical file manager in GNOME as the root user. Be extremely careful if you use this method because you can very quickly destroy a system if you don't know what you're doing. The "gksudo" is like "sudo" but for graphical applications. The "nautilus" part is the file manager in GNOME. Again, be extremely careful because this can totally hose a system if you don't know what you're doing.

---

