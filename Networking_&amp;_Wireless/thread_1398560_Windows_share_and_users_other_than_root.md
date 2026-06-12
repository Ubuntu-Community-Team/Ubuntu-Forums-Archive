---
title: "Windows share and users other than root"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by sdemills on 2010-02-04
I have mounted a Windows share on Ubuntu Linux and I also have a short cut to the same location on my user desktop.

Now using the desktop short cut (one I already had created by browsing the network with file manager) I have full access to all of the files on the share: read, write, and execute.

However, with the mount created in fstab I can only have read access from my account - only the root account has write access.

It is mounted like this...

mount -t cifs //192.168.11.2/share /media/DriveL -o defaults,pass=""

or in fstab it looks like this...

//192.168.11.2/share /media/DriveL cifs  pass="",rw,user,exec   0       0

So how can I mount drives like this, at boot time, in fstab, and have full rw access to them in my normal user account?

Thanks for your help,
Steve

---

### Post by suseendran.rengabashyam on 2010-02-05
Hi,

       Try the following steps in your Ubuntu machine and let me know if it  works
     
1) Open a Terminal and enter the following:
       
```
sudo id user_name
```The output will be something similar to:
       
```
uid=1000(user_name) gid=1000(user_name) groups=...


```Make a note of the uid and gid.
       
2) Make the following entry in your /etc/fstab file :
     
If you don't need a user name and password to access a samba share  add this line:
     
```
//server_name/share_name  /mount_path  cifs  defaults,uid=1000,gid=1000   0  0
```If you need a user name and password to access a samba share add  this line and proceed to the next 2 steps:
       
```
//server_name/share_name  /mount_path  cifs     defaults,uid=1000,gid=1000,credentials=/root/.smbcredentials  0  0
       
```Don't forget to modify the server_name, share_name, mount_path, UID  value and GID 
value.
     
4) Add the following in /root/.smbcredentials:
     
```
username=myusername
password=mypassword
       
```Where myusername and mypassword is the user name and password to  access the samba share.
     
5) Set the following permission to /root/.smbcredentials
     
```
chmod 600 /root/.smbcredentials
```Reboot your machine and log in to see whether you can access and write to the  share.
                   [URL="http://10.10.43.151:3000/issues/show/158#"]
[/URL]

---

### Post by dmizer on 2010-02-05
Please see the 2nd link in my sig, complete with troubleshooting steps.

---

### Post by sdemills on 2010-02-05
Thanks - that worked.

I did some reading and found the following: you are supposed to be able to simply quote the gid to give access to everyone in the group - that option didn't work. Quoting the uid does work and my user now has full access.

Thanks very much for the tip.

Kind Regards
Steve

---

