---
title: "Strange behaviour mounting Samba shares from an old machine"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by UbuFunky on 2011-04-05
Hi Everybody, I've tried to seach everywere on the net, but I couldn't find anything about this problem... 

I have an old server running RedHat 6.2 and Samba 2.0.6, sharing the users home directories. The scurity level for this Samba is set to "share". I can access the shares with Windows with no problem at all...

Trying to mount those shares with smbmount on Ubuntu gives me some problems. I used the following command to mount the share:

sudo smbmount //192.168.0.50/user_share/ /mnt/voyager/ -o user=****,password=****,uid=1000,gid=1000,file_mode=0777,dir_mode=0777,rw

Now I can login into the share, I can navigate the directory structure on the remote machine, I can even create and remove directories, but I CANNOT read or write any file... 

I've tried any option i could find and I tried with 2 different Ubuntu clients (Hardy and Lucid) with the same results...

The strange thing is that I can access (with read/write permissions) with smbclient and with gnome network system...

Can nybody help me?
Thanks in advance.

---

### Post by UbuFunky on 2011-04-05
P.S.: sorry for my poor english! :)

---

### Post by Morbius1 on 2011-04-05
2 suggestions:

[1] Add one more option to your list of mount options:
```
nounix
```[2] You could also mount it the gvfs way:
```
gvfs-mount smb://192.168.0.50/user_share
```It will create a mountpoint at:
> /home/your-user-name/.gvfs/user_share on 192.168.0.50 This mount point is incredibly inconvenient so you can either live with it in a hidden directory or create a symlink to /mnt/voyager.

---

### Post by UbuFunky on 2011-04-05
Thank you Morbius. I've already tried the "nounix" option, along with a dozen of other options, with no results...

I'll give the gvfs a try, but it sounds so strange to me that I can't use samba!

---

### Post by UbuFunky on 2011-04-06
I can't find any solution to the problem... gvfs-mount says that the volume doesn support mount, so I'm stuck!

I tried to run smbstatus on the server while connected with smbmount and with smbclent... I get the same user and same group, so it's very strange... I have total control using smclient but I cannot even read any file with smbmount...

Whatt's wrong with it?? Please help me!  :)

---

### Post by Morbius1 on 2011-04-07
> "Error mounting location: volume doesn't implement mount"You normally get that error when you don't have the following package installed:
```
sudo apt-get install gvfs-fuse
```And you haven't added yourself to the fuse group:
```
sudo gpasswd -a your_user_name fuse
```You need to logout and login again for the group add to take affect.

---

