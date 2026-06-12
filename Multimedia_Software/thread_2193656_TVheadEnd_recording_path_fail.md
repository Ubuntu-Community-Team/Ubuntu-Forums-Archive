---
title: "TVheadEnd recording path fail"
date: 2013-12-14
forum: Multimedia Software
---

### Post by tzorge on 2013-12-14
Hello and thanks in advance,

I cannot for the life of me successfully record and change the default recording directory of TVheadend to the one I want. I think it is a matter of permissions on the new target directory.

I have fiddled around a bit 

[LIST]
[*]with the ownership/groups,changing target dir  permissions to
[/LIST]
```
sudo chmod -R 777 LiveTV/
```
[LIST]
[*]adding hts user to my users group
[*]Changed the owner and group of target to hts
[/LIST]

ls -al output of target is  
```
drwxrwxrwx   5 hts    hts     4096 Dec 14 08:29 LiveTV
```

The directory is automounted in my fstab with 
```
UUID=8d214c70-1990-489e-a426-b502204dbba9 /home/username/Videos/LiveTV/   ext4  nodev,nosuid 0 2
```

I have also tried to change the TVheadend user to me in etc/default/tvheadend unsuccessfully. I could not log in to configuration. 

What am I doing wrong?

edit: parent directory did not have rw rights :P

---

