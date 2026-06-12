---
title: "connecting to a NAS server"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by TheValk on 2011-09-06
I have a LG N2A2DD NAS connected via an ethernet switch to my Ubuntu 10.04 PC.
If I login via the Places/Network I can achieve an upload from PC to NAS of around 19.5MB/s
However I wanted to auto-login on boot so I followed a procedure outlined in a thread in General Help which is as follows.
-----
Open a terminal and type:
sudo mkdir -p /media/NAS
gksudo gedit /etc/samba/credentials

Add two lines to this file:

username=NAS_username_here

password=NAS_password_here

Save & Quit.

Continue with these commands:

sudo chmod 600 /etc/samba/credentials
gksudo gedit /etc/fstab

Append these two lines at the end of file fstab:

# NAS
//NAS_name_or_IP_address_here/share_here /media/NAS cifs credentials=/etc/samba/credentials,uid=1000,gid=1000 0 0

Save & Quit.

Finally type this command and check if the NAS folder is mounted:

sudo mount -a

-----

It worked a treat but my upload speed dropped to 6.8MB/s.

What have I done wrong?

---

### Post by alexthunder on 2011-12-02
I guess you have found a solution and use gigolo, right?
[http://ubuntuforums.org/showpost.php?p=11224520&postcount=44](http://ubuntuforums.org/showpost.php?p=11224520&postcount=44)

---

