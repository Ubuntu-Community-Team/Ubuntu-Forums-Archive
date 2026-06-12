---
title: "read only files when copied from a windows machine"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by samcoinc on 2011-04-01
I am sharing a directory on my lucid lynx install.  I just right clicked on a directory (/home/samco/emc2/nc_files) and set it to share, and checked all the check boxes (read/write and guest).  I ended up having to chown the emc2 directory to 777 before I could even connect to the volume.  (just enough to be dangerous ;))

anyway - I can connect to the share from the windows machine - but when I drop files into it - the files are read only.  (if I drag them to the desktop then back in to the nc_files directory - they are not readonly anymore.)  

Am I making any sense?

thanks
sam

---

### Post by Morbius1 on 2011-04-01
The files that are being placed in your share from windows are saving with owner = nobody, group = nogroup, and permissions of 644. "Nobody" ( which would be all your remote users ) can read and write to the file but "nobody" is not "samco" ( which I hope is your actual login user name ).

The easiest way to fix this is to add a line to the [global] section of /etc/samba/smb.conf:
```
force user = samco
```Then restart samba:
```
sudo service smbd restart
```What this will do is convert "nobody" to "sameco" for every new file / folder that is saved by the remote guest.

---

### Post by samcoinc on 2011-04-01
That makes perfect sense.  I will try it this weekend.

thanks!
sam

> **Morbius1 said:**
> The files that are being placed in your share from windows are saving with owner = nobody, group = nogroup, and permissions of 644. "Nobody" ( which would be all your remote users ) can read and write to the file but "nobody" is not "samco" ( which I hope is your actual login user name ).

The easiest way to fix this is to add a line to the [global] section of /etc/samba/smb.conf:
```
force user = samco
```Then restart samba:
```
sudo service smbd restart
```What this will do is convert "nobody" to "sameco" for every new file / folder that is saved by the remote guest.

---

### Post by samcoinc on 2011-04-18
That worked great! thanks!

sam

---

