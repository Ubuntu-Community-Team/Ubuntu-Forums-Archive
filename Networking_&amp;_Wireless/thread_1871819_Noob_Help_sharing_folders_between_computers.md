---
title: "Noob: Help sharing folders between computers"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by bennettg on 2011-10-29
HI.  I was able to set up folder sharing between 2 different computers with ubuntu on them and an ipad.  it had been some time since i used the ipad to try to connect to the shared folders, and now it keeps asking me for the username and password.  how do i find them on the ubuntu box that the files are stored on?  i thought i made samba anonymous.  can someone helpo?

---

### Post by garvinrick4 on 2011-10-29
Install a samba configuration app and set to let anyone or set to let yourself with username
and password. Can look at samba config and see what you have set now. Will be on bottom
of config file your new samba shares.
```
gedit /etc/samba/smb.conf
```Now this is the samba tool for GUI to set shares and permissions. 
You just use path to set: such as
/home/rick
is my home or

/home/rick/Documents
is just documents

or make your own and then set as a share:
sudo mkdir /home/rick/Shared
Now in Samba make it a shared item.
/home/rick/Shared
and set permissions, (have to set permissions on every share.)

To install gui app for making shares.
```
sudo apt-get install system-config-samba
```Or you can do it by making them in the bottom of config file below others
by hand. See any other shares and copy there's and replace with new share wanted.
gksudo gedit /etc/samba/smb.conf
make share and hit save in upper left corner of gedit.

---

