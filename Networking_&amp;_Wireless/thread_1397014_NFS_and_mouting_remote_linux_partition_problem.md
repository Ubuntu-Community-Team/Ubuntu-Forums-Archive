---
title: "NFS and mouting remote linux partition problem"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by eagle136 on 2010-02-02
Hi,
I'm running Ubuntu (8.10) and wish to connect to my Ubuntu Server and mount directories from there to my client.

I can do this with one directory but not the another, which when I try with this one (it's the homes directory on the server) ...

If I use nfs then I get the "nfs:mount internal error" error message.

If I use nautilus (and hence I assume samba) I get "Unable to mount location Failed to mount windows share"

smb.conf has the same data:
[homes]
  writeable = yes
  path = /home/simon
[intranet]
  writeable = yes
  path = /var/www

login to the client and teh server uses the same username and password.  I can ssh to the server successfully.

Any thoughts gratefully received as I need to get access to files on my homes directory asap!

Thanks

Simon

---

### Post by suseendran.rengabashyam on 2010-02-03
Hi,


       A samba password is needed for each users to access their respective  home directory, you can generate a samba password using the following  command


       ```
sudo smbpasswd -a <user_name>
```
       A minor edit is needed in your /etc/samba/smb.conf file, comment out  the line "path = /home/simon" and restart the samba daemon for the  changes to take effect.


       To access the home directory from your Ubuntu Desktop Machine enter  the following in the Location column of Nautilus


       ```
smb://<ip_address_ubuntu_server>/<user_name>
```
       You can follow the steps mentioned in this thread [http://ubuntuforums.org/showthread.php?t=1396847](http://ubuntuforums.org/showthread.php?t=1396847)  to get your nfs-server and nfs-client working.

---

### Post by eagle136 on 2010-02-04
Thanks very much that was the business :-)

---

### Post by suseendran.rengabashyam on 2010-02-05
Hi,
  
Please mark the thread as solved so that it will be useful for others.

---

