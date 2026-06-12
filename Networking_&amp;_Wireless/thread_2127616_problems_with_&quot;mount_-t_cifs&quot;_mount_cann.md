---
title: "problems with &quot;mount -t cifs&quot;: mount: cannot mount block device //192.168.1.50/share"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by sanderj on 2013-03-20
Hi,

I have a Windows / Samba share which I can access via Nautilus and via smbclient. See log at the end of this post.

However, I really want to mount it, but that doesn't work:

```
sander@appelboor:~$ sudo mount -t cifs //192.168.1.50/share /home/sander/mnt -o username=nmt,password=1234
mount: block device //192.168.1.50/share is write-protected, mounting read-only
mount: cannot mount block device //192.168.1.50/share read-only
sander@appelboor:~$ 
```

I'm using Ubuntu 13.04.

I googled a lot of sites, but I can't get it working. Tips?



```
sander@appelboor:~$ smbclient //192.168.1.50/share -U nmt 
Enter nmt's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.32]
smb: \> dir
  .                                   D        0  Sun Jan 22 19:54:23 2012
  ..                                  D        0  Mon Apr 12 05:40:49 2010
  lost+found                         DH        0  Thu Aug 12 19:58:01 2010
  Video                               D        0  Thu Aug 12 20:03:34 2010
  Music                               D        0  Thu Aug 12 20:03:34 2010
  Photo                               D        0  Thu Aug 12 20:22:13 2010
  Download                            D        0  Sun Jan  2 02:46:27 2000
  .transmission                      DH        0  Thu Aug 12 20:03:47 2010
  .nzbget                            DH        0  Sat Jan  1 01:03:07 2000
  start_app.sh                        A      703  Sun Jan 22 19:54:12 2012
  DVB Opnames                         D        0  Sat Feb 25 08:16:35 2012
  Kinderen                            D        0  Mon Aug  8 19:23:08 2011
  Apps                                D        0  Sat Jan 21 13:35:37 2012
  tmp                                 D        0  Sat Jan 21 13:02:20 2012
  start_app.sh.bak                    A      703  Mon Aug 23 00:12:40 2010

		43987 blocks of size 33553920. 246 blocks available
smb: \> exit
sander@appelboor:~$ 
```

---

### Post by schragge on 2013-03-20
Can you mount it with smbmount?
```
sudo smbmount //192.168.1.50/share /home/sander/mnt --verbose -o username=nmt,password=1234
``` Also, there's a difference between *smbclient* and *smbmount*: smbmount ignores settings in *smb.conf*

---

### Post by papibe on 2013-03-20
Hi sanderj.

Make sure you have installed the cifs utils:
```
sudo apt-get install cifs-utils
```
Regards.

---

### Post by sanderj on 2013-03-20
> **schragge said:**
> Can you mount it with smbmount?
```
sudo smbmount //192.168.1.50/share /home/sander/mnt --verbose -o username=nmt,password=1234
``` Also, there's a difference between *smbclient* and *smbmount*: smbmount ignores settings in *smb.conf*


```
sander@appelboor:~$ sudo smbmount //192.168.1.50/share /home/sander/mnt --verbose -o username=nmt,password=1234
sudo: smbmount: command not found
sander@appelboor:~$ 
```

Ouch.

[http://packages.ubuntu.com/search?suite=quantal&arch=any&mode=filename&searchon=contents&keywords=smbmount](http://packages.ubuntu.com/search?suite=quantal&arch=any&mode=filename&searchon=contents&keywords=smbmount) tells quantal and raring have no smbmount.

[http://packages.ubuntu.com/search?suite=precise&arch=any&mode=filename&searchon=contents&keywords=smbmount](http://packages.ubuntu.com/search?suite=precise&arch=any&mode=filename&searchon=contents&keywords=smbmount) tells precise still had smbmount.

So ... smbmount depreciated ... ?

---

### Post by sanderj on 2013-03-20
> **papibe said:**
> Hi sanderj.

Make sure you have installed the cifs utils:
```
sudo apt-get install cifs-utils
```
Regards.

I did, and then I get another error message:

```
sander@appelboor:~$ sudo mount -t cifs //192.168.1.50/share /home/sander/mnt -o username=nmt,password=1234
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
sander@appelboor:~$
```

and

```
sander@appelboor:~$ mount.cifs //192.168.1.50/share /home/sander/mnt -o username=nmt,password=1234
mount.cifs: permission denied: no match for /home/sander/mnt found in /etc/fstab
sander@appelboor:~$ 
```

What could be wrong?

---

### Post by sanderj on 2013-03-20
I added this to /etc/fstab:

```
# CLI: //192.168.1.50/share /home/sander/mnt -o username=nmt,password=1234
# example unprotected: //servername/sharename  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
# example protected:   //servername/sharename  /media/windowsshare  cifs  username=msusername,password=mspassword  0  0

//192.168.1.50/share /home/sander/mnt cifs  username=nmt,password=1234  0  0
```

... and rebooted, but that result in this dmesg:

```
[   29.021387] CIFS VFS: Send error in SessSetup = -13
[   29.021554] CIFS VFS: cifs_mount failed w/return code = -13
[   33.028512] CIFS VFS: Send error in SessSetup = -13
[   33.028649] CIFS VFS: cifs_mount failed w/return code = -13
```

Am I overlooking something?

---

### Post by sanderj on 2013-03-20
Progress: /etc/fstab now says:

//192.168.1.50/share/ /home/sander/share cifs  username=nmt,password=1234,sec=ntlmv2  0  0

(note the sec=ntlmv2), and the mount works. Cool.

But still not right:

```
sander@appelboor:~/share$ dir > dir
bash: dir: Permission denied
sander@appelboor:~/share$
```

so I can't write via the mount, whereas good old smblclient can write stuff:



```
sander@appelboor:~$ smbclient //192.168.1.50/share -U nmt 
Enter nmt's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.32]
smb: \> 
smb: \> put hallo.txt
putting file hallo.txt as \hallo.txt (0,7 kb/s) (average 0,7 kb/s)
smb: \> dir hallo.txt
  hallo.txt                           A       15  Wed Mar 20 23:42:30 2013

		43987 blocks of size 33553920. 246 blocks available
smb: \> sander@appelboor:~$ 
sander@appelboor:~$ 
```

It seems the mount action changes the ownership of the directory to root:root

```
sander@appelboor:~$ ll | grep share
drwxrwxr-x    6 sander sander      4096 feb  9 22:48 DLNA-share/
drwxrwxr-x    2 sander sander      4096 mrt 20 23:47 share/
sander@appelboor:~$ 
sander@appelboor:~$ sudo mount -a
sander@appelboor:~$ 
sander@appelboor:~$ ll | grep share
drwxrwxr-x    6 sander sander      4096 feb  9 22:48 DLNA-share/
drwxr-xr-x    2 root   root           0 mrt 20 23:42 share/
sander@appelboor:~$ 
```

I can only write as root:

```
sander@appelboor:~/share$ sudo su -
root@appelboor:~# pwd
/root
root@appelboor:~# cd /home/sander/share
root@appelboor:/home/sander/share# 
root@appelboor:/home/sander/share# dir > dir
root@appelboor:/home/sander/share# dir dir
dir
root@appelboor:/home/sander/share# exit
logout
sander@appelboor:~/share$
```

Weird.

---

### Post by sanderj on 2013-03-20
Changed /etc/fstab to:

//192.168.1.50/share/ /home/sander/share cifs  username=nmt,password=1234,sec=ntlmv2,uid=1000 

(so: added uid=1000, with 1000 my userid on my Ubuntu system), and now I can write:

```
sander@appelboor:~/share$ dir > dir4
sander@appelboor:~/share$ dir dir4
dir4
sander@appelboor:~/share$ 

```


mount now shows

```
//192.168.1.50/share/ on /home/sander/share type cifs (rw)
```

Solved! Thank you all for your assistance!

---

### Post by mbuell on 2014-03-06
This can still be a current problem. There is a slightly better solution linked below, in that it seems to both tell us WHY this happens, and it provides a better fix:

[http://www.linuxquestions.org/questions/showthread.php?p=5130057#post5130057](http://www.linuxquestions.org/questions/showthread.php?p=5130057#post5130057)

The fix is to install smbfs AND cifs-utils. 

The problem is, apparently, that mounting cifs does not properly access the password via the command line request. (If you include it in the mount command, you can get it to work, but if you don't, it doesn't have the ability to ask you for it on the command line.)

Installing smbfs automatically installs cifs-utils as a dependency.

Afaik, this thread could now be marked [SOLVED].

---

