---
title: "Samba Server help"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by love2learn on 2011-04-03
**The Need:**
The main need I have is, I want my Win7 media box running XBMC to network with my Fresh Server 64 install of Ubuntu 10.04. Not even network. I just want to be able to see my shared hard drives in the Ubuntu Server from the win7 media center.

**The facts:**
I have a SOHO with 3 (main) computers and a Server.They are all Behind a wireless router. All the computers are communicating via wireless signal. Server is on hardwire cat5 cable to router. 

The media center (win7) was working fine on my 8.10 install but i wanted to upgrade to 10.04 for the LTS until 12.04 comes out. I have 4 shared sdd's and 1 OS sdd. Yes, I am an idiot and did not backup my smb.conf.

The Server is a server64 install with --no-install-recommends ubuntu-desktop as a gui. So it does not have your normal menu within ubuntu so please try to stick to CLI if at all possible.

**My admissions to stupidity:**
I followed many guides on samba and I followed them very blindly. I dont understand how samba works nor do I claim to know anything about linux in general. I am very ignorant compared to most (if not all) the people on this website when it comes to *nix flavors so I dont mind being treated as such.

**A few things you might/might not need:**

```
[ATTACH]188032[/ATTACH] 
```l2l@Server:~$ ls -la Desktop
total 8
drwxr-xr-x  2 l2l l2l 4096 2011-04-03 01:21 .
drwxr-xr-x 28 l2l l2l 4096 2011-04-03 21:06 ..

l2l@Server:~$ smbtree
Enter l2l's password: 
CHOPPERS
    \\SERVER                 Server server (Samba, Ubuntu)
        \\SERVER\IPC$               IPC Service (Server server (Samba, Ubuntu))
        \\SERVER\Music              
        \\SERVER\Movies2            
        \\SERVER\Pictures           
        \\SERVER\Movies1            
        \\SERVER\print$             Printer Drivers

I've worked on this for two days and now I am simply stumped.**](*,)** Please help.:oops:

---

### Post by love2learn on 2011-04-04
[Movies1]
    path = /media/Movies/Movies1
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755
[Pictures]
    path = /media/Pictures/Pictures
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755

[Movies2]
    path = /media/Movies2/Movies2
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755

[Music]
    path = /media/Music/Music
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755

This is how my smb.conf looks

---

### Post by dmizer on 2011-04-04
Your shared directory paths seem very unusual. Just to be sure:

Do you have a folder in /media/movies called "movies1"?

In a samba share, "path =" is the exact location of all of your shared files. So, if you can list all of your pictures with this command:
```
ls /media/Pictures
```
Then your share should look like this:
```
[Pictures]
path = /media/Pictures
writeable = yes
browseable = yes
guest ok = yes
create mask = 0755
```

---

### Post by love2learn on 2011-04-04
i switched to ubuntu 10.04 on my laptop (dual boot) and I can see the server  as Server in the windows share. I can also see it as smb://192.168.1.100 but when i try the /Movies1 switch it wont mount.  Does that mean my FSTAB is messed up? 

They automount but I used pysdm to mount and it looks a bit messed up. Maybe that is where I should start today...

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                     0  0  
# / was on /dev/sda1 during installation
UUID=125a714d-7b96-4943-a2f5-a3fb7d4fcf8c  /            ext4  errors=remount-ro                       0  1  
# swap was on /dev/sda5 during installation
UUID=bb43f34f-ec72-4eef-8cf2-a45fbb729f24  none         swap  sw                                      0  0  
/dev/sdb1                                  /media/sdb1  vfat  uid=1000,umask=777,dmask=777,fmask=777  0  0  
/dev/sdc1                                  /media/sdc1  vfat  defaults                                0  0  
/dev/sdd1                                  /media/sdd1  vfat  defaults                                0  0  
/dev/sde1                                  /media/sde1  vfat  defaults                                0  0

---

### Post by love2learn on 2011-04-04
oh thank heaven, I have the "god" of samba here. I have read many of your posts and you have helped me years ago.  I have /media/Pictures/Pictures as there are some pictures my wife and I have that we dont want the media center to have a chance to broadcast. so I put the media center past the /media/Pictures folder. I know its flaky. If that is the main problem I will change the file structure if needs be.

currently this is the output of:

l2l@Server:~$ ls /media/Pictures
Pictures

I now switched it to:
```
l2l@Server:~$ ls /media/Pictures/
alyse's pictures  pics

```and my smb.conf is NOW:

```
[Movies1]
    path = /media/Movies
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755

[Pictures]
    path = /media/Pictures
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755

[Movies2]
    path = /media/Movies2
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755

[Music]
    path = /media/Music
    writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0755

```Fstab looks like this Now:

```
/dev/sdb1                                  /media/sdb1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0  
/dev/sdc1                                  /media/sdc1  vfat  uid=1000,umask=777,dmask=777,fmask=777,0,0,  0  0  
/dev/sdd1                                  /media/sdd1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0  
/dev/sde1                                  /media/sde1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0
```

---

### Post by love2learn on 2011-04-04
I thought maybe a firewall was the problem...

ip tables on server:

```
l2l@Server:~$ sudo iptables -L
[sudo] password for l2l: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

all win7 computers are firewall-less

---

### Post by Morbius1 on 2011-04-04
Sorry for the interruption but if pysdm is responsible for that fstab please stop using it. And don't use Mountmanager either it will be worse. Please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
mount
```

---

### Post by love2learn on 2011-04-04
its no interuption, any input is welcomed.

```
l2l@Server:~$ sudo blkid -c /dev/null
[sudo] password for l2l: 
/dev/sda1: LABEL="Pictures" UUID="49C6-E94D" TYPE="vfat" 
/dev/sdb1: LABEL="Music" UUID="49BC-30E3" TYPE="vfat" 
/dev/sdc1: LABEL="Movies" UUID="49BB-EB9E" TYPE="vfat" 
/dev/sdd1: LABEL="Movies2" UUID="49BB-EE2A" TYPE="vfat" 
/dev/sde1: UUID="125a714d-7b96-4943-a2f5-a3fb7d4fcf8c" TYPE="ext4" 
/dev/sde5: UUID="bb43f34f-ec72-4eef-8cf2-a45fbb729f24" TYPE="swap" 
```
```
l2l@Server:~$ mount
/dev/sde1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/sdb1 type vfat (rw)
/dev/sdc1 on /media/sdc1 type vfat (rw)
/dev/sdd1 on /media/sdd1 type vfat (rw)
/dev/sda1 on /media/Pictures type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

Going to un-install pysdm now.

---

### Post by Morbius1 on 2011-04-04
Are sda1, sdb1, sdc1, and sdd1 internal or external partitions?

---

### Post by love2learn on 2011-04-04
internal partitions. each is a seperate sata drive mounted inside the server. They are on a raid card if that makes a difference.

---

### Post by Morbius1 on 2011-04-04
**[1] Unmount all of them:**
```
sudo umount /media/sdb1
sudo umount /media/sdc1
sudo umount /media/sdd1
sudo umount /media/Pictures
```[**2] Comment out the following fstab entries by placing a # sign in front of the lines so that they look like this:**
> [COLOR=Blue]**#**[/COLOR]/dev/sdb1                                  /media/sdb1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0  
**[COLOR=Blue]#[/COLOR]**/dev/sdc1                                  /media/sdc1  vfat  uid=1000,umask=777,dmask=777,fmask=777,0,0,  0  0  
**[COLOR=Blue]#[/COLOR]**/dev/sdd1                                  /media/sdd1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0  
**[COLOR=Blue]#[/COLOR]**/dev/sde1                                  /media/sde1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0**[3] Create permanent homes for these partitions:**
```
sudo mkdir /media/Pictures
sudo mkdir /media/Music
sudo mkdir /media/Movies
sudo mkdir /media/Movies2
```**[4] Add the following lines to fstab:**
```
UUID=49C6-E94D /media/Pictures vfat defaults,uid=1000,utf8,umask=000 0 2
UUID=49BC-30E3 /media/Music vfat defaults,uid=1000,utf8,umask=000 0 2
UUID=49BB-EB9E /media/Movies vfat defaults,uid=1000,utf8,umask=000 0 2
UUID=49BB-EE2A /media/Movies2 vfat defaults,uid=1000,utf8,umask=000 0 2
```**[5] Save fstab and in a terminal run the following command to test for errors and mount the new partitions:**
```
sudo mount -a
```[COLOR=Blue]Note: It would be a miracle if I didn't make a typo in all this so if there is an error post it.[/COLOR]

If there are no errors, then your smb.conf should now be pointing to the right partitions with permissions set to accommodate guest write access.

[COLOR=Blue]EDIT:[/COLOR] your might want to post your fstab one more time after all of this is done since you had your Ubuntu partition mounted twice. The steps above should have fixed that but .....

---

### Post by love2learn on 2011-04-04
wow, i had a bunch of stuff fubared huh... okay this is how it went:

new fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                          0  0  
# / was on /dev/sda1 during installation
UUID=125a714d-7b96-4943-a2f5-a3fb7d4fcf8c  /            ext4  errors=remount-ro                            0  1  
# swap was on /dev/sda5 during installation
UUID=bb43f34f-ec72-4eef-8cf2-a45fbb729f24  none         swap  sw                                           0  0  
#/dev/sdb1                                  /media/sdb1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0  
#/dev/sdc1                                  /media/sdc1  vfat  uid=1000,umask=777,dmask=777,fmask=777,0,0,  0  0  
#/dev/sdd1                                  /media/sdd1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0  
#/dev/sde1                                  /media/sde1  vfat  uid=1000,umask=777,dmask=777,fmask=777       0  0  

UUID=49C6-E94D /media/Pictures vfat defaults,uid=1000,utf8,umask=000 0 2
UUID=49BC-30E3 /media/Music vfat defaults,uid=1000,utf8,umask=000 0 2
UUID=49BB-EB9E /media/Movies vfat defaults,uid=1000,utf8,umask=000 0 2
UUID=49BB-EE2A /media/Movies2 vfat defaults,uid=1000,utf8,umask=000 0 2
```


new mount:

```
l2l@Server:~$ sudo mount -a
mount: mount point /media/Pictures does not exist
mount: mount point /media/Music does not exist
mount: mount point /media/Movies does not exist
mount: mount point /media/Movies2 does not exist
```

---

### Post by Morbius1 on 2011-04-04
Did you do this step:
> **[3] Create permanent homes for these partitions:**
```
sudo mkdir /media/Pictures
sudo mkdir /media/Music
sudo mkdir /media/Movies
sudo mkdir /media/Movies2 
```

---

### Post by love2learn on 2011-04-04
:oops: did now lol

```
l2l@Server:~$ sudo mkdir /media/Pictures
l2l@Server:~$ sudo mkdir /media/Music
l2l@Server:~$ sudo mkdir /media/Movies
l2l@Server:~$ sudo mkdir /media/Movies2
l2l@Server:~$ sudo mount -a
```

Thank you for all your help! I can not see the Server yet but that was a big kink in the system.

---

### Post by love2learn on 2011-04-04
this guide is a ridiculously over-simplified POS....  [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

---

### Post by dmizer on 2011-04-04
> **love2learn said:**
> this guide is a ridiculously over-simplified POS....  [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

It depends on what you want to do. For most things, using the default smb.conf file with that howto will work just fine.

It looks like you have things better sorted on the server side of things. Let's take a look at the client side now. Do you have Windows or Linux clients, or both?

You said you have a Win7 client. Do you have Windows Live installed? Double check even if you are pretty sure you do not. Windows Live seems to interfere a lot with Samba. Is there an active firewall on the Windows machine? If so, try disabling it.

---

### Post by love2learn on 2011-04-04
> **dmizer said:**
> It depends on what you want to do. For most things, using the default smb.conf file with that howto will work just fine. 

Yeah. I was taking some frustration out. Sorry.

> **dmizer said:**
> It looks like you have things better sorted on the server side of things. Let's take a look at the client side now. Do you have Windows or Linux clients, or both?

You said you have a Win7 client. Do you have Windows Live installed? Double check even if you are pretty sure you do not. Windows Live seems to interfere a lot with Samba. Is there an active firewall on the Windows machine? If so, try disabling it.

Yes, I haven't updated my progress in a bit:

With a restart to samba my linux side works. So I know now that the Server is good.

I started with this thread on the windows side about 30 minutes ago:

[http://www.tomshardware.com/forum/75-63-windows-samba-issue](http://www.tomshardware.com/forum/75-63-windows-samba-issue)

> [nikonz wrote :]("http://www.tomshardware.com/forum/75-63-windows-samba-issue#t1444")

Control Panel - Administrative Tools - Local Security Policy 

Local Policies - Security Options 



Network security: LAN Manager authentication level 
     Send LM & NTLM responses 

Minimum session security for NTLM SSP 
   Disable Require 128-bit encryption 



my SMB server worked after changing those two options

I did this to my laptop with no avail. I will look into your suggestion and update in a bit.

sry didnt answer your questions:

I have win7 clients on the rest of my network or ubuntu 10.04 all ubuntu's work great. The win7 clients do not.  There are no firewalls active anywhere inside the network.

---

### Post by love2learn on 2011-04-04
I do not have windows live anything on my laptop. I can't see the server but I can ping it with the ip address. I am using AVG for an anti-virus if that matters.

-removed the stored credentials as per this guys post 
   
                                                                        [> **[URL="http://www.tomshardware.com/forum/profile-384012.htm"]CompTechPC]("http://www.tomshardware.com/forum/profile-384012.htm")                                                            **                                                                             [/URL][02-15-2009 at 07:50:47 PM]("http://www.tomshardware.com/forum/75-63-windows-samba-issue#t1475")                         
                                                                                                                                                           
                         Hooray! I am able to once again  connect to my Samba share via Windows 7 after removing the stored  credentials for the Samba share.  Control Panel -> Credential  manager.


That didnt work for me either.

---

### Post by love2learn on 2011-04-04
There is this itch in the back of my head I cant get rid of. Before I did a fresh install of ubuntu on my server ( from 8.10 to 10.04) my win7 media center computer was working ( with xbmc loaded and playing movies) So even though my nix boxes can see the server, it bugs me that the rest cant and the media center could before the change...

---

