---
title: "mount a server partition with normal user access"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by gush on 2010-01-26
Hello,
Sorry if this issue has already resolved, I searched for it but I didn't find it.

I need to mount a partition that is on a server (via samba).

I am doing the following in my fstab 
> 
//server/www /media/www cifs rw,user,allow_other,default_permissions,credentials=/root/.smbcredentials,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0


I can mount it but it just allows me to access with the root user.
How can I do it to get access with any user?

Additional Data: I added "rw,user,allow_other,default_permissions" because I thought that would solve de problem but it didn't.

Thanks in advance.

---

### Post by suseendran.rengabashyam on 2010-01-28
Hi,

Try the following steps and let me know if it works

1) Open a Terminal and enter the following:
   
    ```
id
```    The output will be something similar to:

    ```
uid=1000(karmic) gid=1000(karmic) groups=...
```    Make a note of your uid and gid.

2) Add the following line to your /etc/fstab file  :
       
    ```
//servername/sharename  /mountpath  cifs  defaults,uid=1000,gid=1000,credentials=/root/.smbcredentials  0  0
```    Modify the servername, sharename, mountpath, etc.

4) Add the following in /root/.smbcredentials:
       ```
username=myusername
password=mypassword
```  Where myusername and mypassword is the user name and password to access the     samba share.   

5) Set the following permission to /root/.smbcredentials
       
    ```
chmod 600 /root/.smbcredentials
```6) Also confirm whether the Server Share has the write permissions.
                   [URL="http://10.10.43.151:3000/issues/show/106#"]
[/URL]

---

