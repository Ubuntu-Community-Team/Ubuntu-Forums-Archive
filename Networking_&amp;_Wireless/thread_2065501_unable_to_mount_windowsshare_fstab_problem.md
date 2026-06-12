---
title: "unable to mount windowsshare: fstab problem"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by steffenzi on 2012-10-02
I am having a problem with a windows share which I want to mount into a folder. I'm running ubuntu 12.04.

I'm able to connect to this Windows share via the "Connect to Server" dialog, using the following information as input.

server=server.name.de
folder=/path/to/sharefolder
domain name=AD\
username=shareusername
password=sharepassword

Now I want to mount it using the terminal, or better, automatically during boot. I created the folder /media/folder (smbfs is installed) and I modified my fstab by adding the following line:

//server.name.de/path/to/sharefolder /media/folder cifs auto,user,username=shareusername,password=sharepassword 0 0
# last line

(normally using credentials file for password, just for simplicity here...) I get "permission denied". The share shows up in my media list, but I can't access it. It works for the smb: link though. I tried specifying a "domain=AD"  argument, but it doesnt work. What's the problem here, why am I not able to connect to this share via fstab? also not working with sudo mount -a.

I would be glad for any kind of suggestions what the problem is...
Cheers!

---

