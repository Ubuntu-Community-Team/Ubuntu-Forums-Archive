---
title: "Successful Windows Networking with cifs"
date: 2005-01-23
forum: Networking &amp; Wireless
---

### Post by bobalien on 2005-01-23
I had made several posts to this thread: [http://www.ubuntuforums.org/showthread.php?t=7686](http://www.ubuntuforums.org/showthread.php?t=7686) recently in my attempt to solve some Windows (win2k server) and Ubuntu (client) networking issues. I've seen several threads started on this topic, and most die fairly early.

In the newest edition of Maximum PC there's a guide ("The Linux Diaries") that deals with switching to Linux from Windows, touching also on using Linux in a Windows network environment.  The section "Connecting to fileshares" offered the following advice, which proved to be successful and painless to set up:

- edit /etc/fstab
- add the line *//server[or domain]/share /local/dir cifsexec,credentials=/etc/cifspw,uid=yourLinuxusername*  (make sure to leave a carriage return at the end of the fstab file)
- create /etc/cifspw and enter 2 lines: *username=yournetworkuser* and *password=yournetworkpassword*

after you reboot, you'll have a permanently mounted share

- this was done using *Ubuntu [Warty]* as a client PC joining a *win2k server* domain

----
Edit 1/24/05 9:46 am

Some quick notes: 
- *samba* and *smbfs* must be installed and up to date (both can be done through Package Manager)
- in the lines added to the fstab file, *,uid=yourLinuxusername* is unnecessary, and seemed to cause a couple of problems for me actually

---

### Post by kdavison007 on 2005-01-24
thanks for the tip!  I'll bring my Ubuntu Warty laptop into work tomorrow and see if I can connect to our fileserver.  The only problem is that if it works then I'll be getting an fstab error everytime I boot and I'm not connected to the network, right?

---

### Post by bobalien on 2005-01-24
i guess so - my situation involved a permanently connected computer

i never got regular old "windows networking" to work on a domain, so this was just a work-around for me... there's several flaws, as in the password is exposed in an unsecure file (which i could always secure), and the fstab errors you mention... maybe everything will be easier in hoary... anyway, my set-up worked great all day today, so it works for me

---

### Post by kdavison007 on 2005-01-25
When you say //servername[domain]/... what do you mean?

For instance say I have a share on a workgroup named "msworkgroup"  - would I put //msworkgroup/servernameorip/sharename  ?

---

### Post by nocturn on 2005-01-25
[QUOTE=kdavison007]When you say //servername[domain]/... what do you mean?

For instance say I have a share on a workgroup named "msworkgroup"  - would I put //msworkgroup/servernameorip/sharename  ?[/QUOTE]

normally not, this is UNC naming, so either \\server or \\server.mydomain should work.  It should be a DNS domain, not a workgroup one.

---

### Post by kdavison007 on 2005-01-25
Okay.  Thanks for quick response.  I got it to work!

---

### Post by bobalien on 2005-01-25
[QUOTE=kdavison007]When you say //servername[domain]/... what do you mean?

For instance say I have a share on a workgroup named "msworkgroup"  - would I put //msworkgroup/servernameorip/sharename  ?[/QUOTE]

I haven't tried this with a workgroup, but I was able to join to a win2k domain...

our windows domain is ourgrp.com, with the actual file server named g_server1, and shares on the server "Client", "Users" and "Exchange"

my fstab read something like:
*//ourgrp.com/Clients /home/user/Desktop/Clients cifsexec,credentials=/home/user/cifspw*

I don't remember if I tried this but I believe I could have alson just put:
*//g_server1/Clients /home/user...* 

- and in your case I believe you could just use *//servername/sharename* and not worry about the workgroup

-- oops, just saw someone beat me to it..

---

### Post by khantozavri on 2005-10-10
Hi:

I've followed all your recommendations (except reboot, whill I'll do after finishing this post;) ) but when I 'sudo mount -a' received:
-
mamuka@mamuka:~$ sudo mount -a
mount: unknown filesystem type 'credentials=/etc/cifspw'
-

This is my fstab:

---
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs notail          0       1
/dev/hda8       /home           reiserfs defaults        0       2
/dev/hda5       /media/hda5  vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1	/media/windoza	ntfs	nls=utf8,umask=0222	0	0
//adns/extra /media/extra cifsexec,credentials=/etc/cifspw

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
--

BTW, what are all those /tem/app...in my fstab? never seen them before. Running Breezy Badger...

Thanks,

Mamuka

---

### Post by bobalien on 2005-10-10
you know, I really only accidentally stumbled onto this solution, and it worked temporarily, but ended up giving me some minor stability problems down the road... I eventually just ended up putting Windows on the system anyway :/  I'm definitely no linux expert, so sorry I can't help you any further, maybe someone else in the forum has found something that works better?

---

### Post by rsgranne on 2005-11-16
> **khantozavri]Hi:

I've followed all your recommendations (except reboot, whill I'll do after finishing this post said:**
> 
//adns/extra /media/extra cifsexec,credentials=/etc/cifspw


The example at the top of this thread contains a typo, which you copied. This is the line that should be in your fstab:

//adns/extra /media/extra cifs exec,credentials=/etc/cifspw 0 0

Notice the space between cifs and exec; notice also the 0 0 at the end.

Try that & let us know if that works.

Scott

---

### Post by Rikostan on 2006-03-30
I just found this in another thread and it solved all of my MP3 playing woes... I can now get to all of my music on our (Windows) media server, which was the last thing I needed to accomplish.

Thanks!

---

### Post by lysis on 2006-04-03
you found what in who's other thread?  =/

---

### Post by sovin on 2006-09-05
hi, i'm running ubuntu on a laptop and need to access the shared folder on my windows xp workgroup

would the line in my fstab be as follows?

```
//LOREY_LAN/Clients /home/user/Desktop/Clients cifs exec,credentials=etc/cifspw
```

---

### Post by holyUb on 2007-08-02
Hello, I'm a newbie but i proceed this way and had no pb:


apt-get install samba smbfs smbclient
cd /etc
nano cisfpw

wrote 2 lines as follow :

username=remote_user_login
password=your_password

saved this file, then :

mkdir /local
cd /local
mkdir your_mounted_dir
nano /etc/fstab



added this line at EOF [with carriage return], don't forget fs type !

//XXX.XXX.XXX.XXX/your_mounted_dir /local/your_mounted_dir  smbfs cifsexec,credentials=/etc/cifspw,uid=root

saved the file then :

mount -a
mount

The result is :

/dev/sda1 on / type ext3 (rw,errors=remount-ro,usrquota,grpquota)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
[B]//XXX.XXX.XXX.XXX/your_mounted_dir on /local/your_mounted_dir type smbfs (rw)
[/B]


Thanks a lot for your subject,
best regards,

A french ubuntu newbie

---

### Post by ChrisAshton84 on 2007-12-06
Thanks!  The first format with ... cifs exec,... didn't work but with ... smbfs cifsexec,... it did!

---

### Post by jwl007 on 2007-12-14
I too got the mounted share working with the following command in /etc/fstab:

//XXX.XXX.XXX.XXX/your_mounted_dir /local/your_mounted_dir smbfs cifsexec,credentials=/etc/cifspw,uid=yourlocaluser,gid=yourlocaluser

So on startup, my user is able to read and write to the mounted share.

My question is.. is this actually CIFS, or is it a hybrid samba,cifs workaround where samba tries and then if it fails, cifs is attempted?

---

### Post by Qazzian on 2008-03-28
if you are on Kubuntu try typing this into your URL bar in Konqueror

smb://computername

It worked for me with Kubuntu Gutsy.

It asks for passwords etc as you need them

---

