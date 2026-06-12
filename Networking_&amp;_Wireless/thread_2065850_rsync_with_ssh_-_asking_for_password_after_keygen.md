---
title: "rsync with ssh - asking for password after keygen"
date: 2012-10-03
forum: Networking &amp; Wireless
---

### Post by kpholmes on 2012-10-03
ive set up passwordless ssh by running ssh-keygen , then swapped keys using ssh-copy-id . i can login without being asked for a password if i just type in ssh [email]user@remote.com[/email] , but when running this rsync command i get prompted for a password on the remote machine. im transferring data from a  remote machine to a local computer, and im running rsync from the local machine. 

sudo rsync --delete --progress  -azvv -e ssh [email]desktop@remote.com[/email]:/home/remote/Documents/ /home/local/Documents/

could it be that when i created the keys i didnt add these options? and thats whats causing the problems? ssh-keygen -t rsa

---

### Post by 2F4U on 2012-10-03
Maybe these articles help:

[http://ubuntuforums.org/showthread.php?t=238672](http://ubuntuforums.org/showthread.php?t=238672)
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[http://myubuntublog.wordpress.com/2009/08/31/backup-using-rsync-ssh-cron/](http://myubuntublog.wordpress.com/2009/08/31/backup-using-rsync-ssh-cron/)

---

### Post by Lars Noodén on 2012-10-03
You probably have to specify the key in rsync, too.

```

sudo rsync --delete --progress  -azvv **-e 'ssh -i */home/desktop/.ssh/key_rsa*' **desktop@remote.com:/home/remote/Documents/ /home/local/Documents/

```

Obviously fill in the right path for your own key.

---

### Post by albandy on 2012-10-03
> **kpholmes said:**
> ive set up passwordless ssh by running ssh-keygen , then swapped keys using ssh-copy-id . i can login without being asked for a password if i just type in ssh [email]user@remote.com[/email] , but when running this rsync command i get prompted for a password on the remote machine. im transferring data from a  remote machine to a local computer, and im running rsync from the local machine. 

sudo rsync --delete --progress  -azvv -e ssh [email]desktop@remote.com[/email]:/home/remote/Documents/ /home/local/Documents/

could it be that when i created the keys i didnt add these options? and thats whats causing the problems? ssh-keygen -t rsa

If you're running rsync with sudo, ssh keys should be installed in the root ssh folder /root/.ssh/

---

