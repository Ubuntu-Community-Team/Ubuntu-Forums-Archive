---
title: "need help in setting up a shared folder between Xubuntu and Win 7 laptop"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by s1baker on 2012-10-20
hi,

I am having trouble getting my Ubuntu desktop to allow my windows 7 laptop share a folder on the desktop.
It use to work, but now it doesn't

My setup is this:
Desktop = 12.04.01 running Xubuntu with xfce.
It is 6 years old and does not have wireless networking built in so it is connected by ethernet cable to the wireless router.
My laptop is Windows 7 that connects wirelessly to the router.

I want a folder on my desktop that I can use to transfer files back and forth between it and the laptop. 
This use to work, but I have bought a USB wifi adaptor, plugged it into the desktop and it worked just fine,
except not I don't have my shared folder anymore, whether of not I have the desktop connected wired or wireless.
( also samba is installed, can see it running by doing a 'sudo netstat -atulpen' or 'ps -A' )

When I try to right click on the folder that I want to share I get this:
```
'net usershare' returned error 255: net usershare add: failed to add share xu7. Error was Operation not permitted
```   

I can sudo nautilus and do it, just can't do it as a user.

Any help appreciated.

---

### Post by Morbius1 on 2012-10-20
It sounds like you are not a member of the right group. Run the following command and see if you are a member of the sambashare group:
```
id
```If you are not add youself:
```
sudo gpasswd -a your_user_name sambashare
```Then logoff and logon again.

---

### Post by s1baker on 2012-10-20
i ran 'ID' and it shows that I am a member of sambashare

---

### Post by Morbius1 on 2012-10-20
Is it at all possible that it is already shared but by someone else. Run the following command and see if you already have a samba share:
```
ls -al /var/lib/samba/usershares
```

---

### Post by s1baker on 2012-10-20
here is what 'ls -al /var/lib/samba/usershares' shows:

```

drwxrwxrwt 2 root users 4096 Oct 20 17:56 .
drwxr-xr-x 4 root root  4096 Oct  6 20:13 ..
-rw-r--r-- 1 root root   120 Oct 19 19:43 temp
-rw-r--r-- 1 root root   107 Oct 20 17:15 usershares
-rw-r--r-- 1 root root    98 Oct 19 22:21 xpshare
-rw-r--r-- 1 root root    90 Oct 19 22:22 xu7

```

---

### Post by Morbius1 on 2012-10-21
You won't as a regular user be able to create a share called xu7 because one already exists and it's owned by root. You can't overwrite something created by root:
> -rw-r--r-- 1 root root    90 Oct 19 22:22 xu7

---

### Post by s1baker on 2012-10-21
I did a 'sudo nautilus' and went and released root as owner of my two folder 'xu7'.
Then I went went and I right clicked my mouse on the folder and I was able to set up the
sharing options for the folders.

But I still do not see the folders on my laptop.

---

### Post by s1baker on 2012-10-28
Just for the record, I got my shared folder to work by:

1) putting 'force = (my home folder)' in the  /etc/samba/smb.conf file under [global]

2) I had to 'sudo ufw disable' on my firewall

3) I then had to do a 'sudo service smbd restart' and
'sudo service nmbd restart'

Then my win7 laptop was able to see the shared folder on my ubuntu box.

---

