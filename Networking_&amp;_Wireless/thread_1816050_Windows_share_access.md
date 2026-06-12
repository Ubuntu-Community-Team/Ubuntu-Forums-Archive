---
title: "Windows share access"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by Stephen Shellard on 2011-08-01
I am using a QNAP NAS Windows share to hold all the music for my SONOS music system.   

I also wish to backup files from my 11.04 Desktop and have installed smbfs for this purpose.  This has enabled me to copy files via the command line using root permissions, but I cannot perform similar operations via GUI.  By contrast, when I access the NAS via my wifes Windows 7 computer, copying files can be done directly via GUI.

In Ubuntu I generally access the NAS via /places/Network  [Access Path: smb://sonosmusic/etc]   but have also mounted it as follows: 
sudo smbmount  //192.168.0.8/qmultimedia  /mnt/sonosmusic -o username=stephen, password=xxxxxxxxx  and have attempted to change folder ownership [currently root] and permissions using chmod and chown respectively.  The chown appears to go through without difficulties, but on inspection, ownership remains with root.  The permissions remain with root regardless. 

I have attempted and failed to mount it using similar formulations based around mount.cifs,  mount smbfs,  mount cifs, though would confess to being confused as to the significance and distinction between all of these.   

When logging in to the QNAP NAS via  web interface, I can see that the user name established for my access has all read and write permissions.

I do not have SAMBA installed as I only wish to access the share from my Ubuntu desktop and do not require to access my Ubuntu files from a Windows machine.  I have some past experience with SAMBA but have not found it easy to work with.

Advice and suggestions would be greatly appreciated.  I would hope at least to be able to get the access from my Ubuntu 11.04 as can be had from Windows 7.

---

### Post by capscrew on 2011-08-01
> **Stephen Shellard said:**
> I am using a QNAP NAS Windows share to hold all the music for my SONOS music system.   

I also wish to backup files from my 11.04 Desktop and have installed smbfs for this purpose.  This has enabled me to copy files via the command line using root permissions, but I cannot perform similar operations via GUI.  By contrast, when I access the NAS via my wifes Windows 7 computer, copying files can be done directly via GUI.

In Ubuntu I generally access the NAS via /places/Network  [Access Path: smb://sonosmusic/etc]   but have also mounted it as follows: 
sudo smbmount  //192.168.0.8/qmultimedia  /mnt/sonosmusic -o username=stephen, password=xxxxxxxxx  and have attempted to change folder ownership [currently root] and permissions using chmod and chown respectively.  The chown appears to go through without difficulties, but on inspection, ownership remains with root.  The permissions remain with root regardless. 

I have attempted and failed to mount it using similar formulations based around mount.cifs,  mount smbfs,  mount cifs, though would confess to being confused as to the significance and distinction between all of these.   

When logging in to the QNAP NAS via  web interface, I can see that the user name established for my access has all read and write permissions.

I do not have SAMBA installed as I only wish to access the share from my Ubuntu desktop and do not require to access my Ubuntu files from a Windows machine.  I have some past experience with SAMBA but have not found it easy to work with.

Advice and suggestions would be greatly appreciated.  I would hope at least to be able to get the access from my Ubuntu 11.04 as can be had from Windows 7.

By your description it appears that the Qnap NAS drives are formatted NTFS.  NTFS formatted drives have no uid/gid and therefore are  always mounted as read only and owned by root.  You should mount these with the mount command declaring your UID and GID.  If you want multiple users to have access declare a GID that all the users are members of.  More information is available in the man pages```
man mount.cifs

man mount
```

---

### Post by Stephen Shellard on 2011-08-02
Thank you for this response which has been helpful though I continue to struggle with a number of issues. 

Despite using options and referring to manuals as suggested I have been unable to mount the share from the command line.  For example:

sudo mount.cifs  //192.168.0.8/qmultimedia  /mnt/sonosmusic -o user=stephen, password=xxxxxxx, uid=1000, gid=1000

I have also tried using forceuid and forcegid options, but without success:  however;  I have succeeded in mounting the drive with the desired permissions by adding a line to my fstab file:

 //192.168.0.8/qmultimedia /mnt/sonosmusic cifs rw,auto,_netdev,user=stephen,password=xxxxxx,uid=1000,gid=1000 0 0

There are a number of problems which continue to trouble me however:

1]I have tried using the noauto option as I would prefer the drive not to automatically mount on boot up as it is not always switched on.  As expected it does not mount on boot up, but when I have then tried to mount it explicitly, it does not do so with the required permissions - or does not mount at all - I have tried a variety of approaches to this. Perhaps I have not got the syntax correct or have misunderstood what is meant by "explicitly mount" in this context.

2] I have attempted to copy some photographs to the drive - a total of about 440mbs.   Though this appears to start working, the projected time for the task is unacceptable - varying from 21 to 36 hours. 

3] The fstab file now includes my password, which is not good practice. 

Direction with any of these points would be appreciated.

---

### Post by capscrew on 2011-08-02
> **Stephen Shellard said:**
> Thank you for this response which has been helpful though I continue to struggle with a number of issues. 

Despite using options and referring to manuals as suggested I have been unable to mount the share from the command line.  For example:

sudo mount.cifs  //192.168.0.8/qmultimedia  /mnt/sonosmusic -o user=stephen, password=xxxxxxx, uid=1000, gid=1000

I have also tried using forceuid and forcegid options, but without success:  however;  I have succeeded in mounting the drive with the desired permissions by adding a line to my fstab file:

 //192.168.0.8/qmultimedia /mnt/sonosmusic cifs rw,auto,_netdev,user=stephen,password=xxxxxx,uid=1000,gid=1000 0 0

There are a number of problems which continue to trouble me however:

1]I have tried using the noauto option as I would prefer the drive not to automatically mount on boot up as it is not always switched on.  As expected it does not mount on boot up, but when I have then tried to mount it explicitly, it does not do so with the required permissions - or does not mount at all - I have tried a variety of approaches to this. Perhaps I have not got the syntax correct or have misunderstood what is meant by "explicitly mount" in this context.

2] I have attempted to copy some photographs to the drive - a total of about 440mbs.   Though this appears to start working, the projected time for the task is unacceptable - varying from 21 to 36 hours. 

3] The fstab file now includes my password, which is not good practice. 

Direction with any of these points would be appreciated.

With an entry in fstab you should be able to mount the drive without using sudo.  I have always used the mount command like this ```
mount -t cifs
```

See if this works for you```
mount -t cifs //192.168.0.8/qmultimedia  /mnt/sonosmusic -o user=stephen, password=xxxxxxx, uid=1000, gid=1000
```

If this doesn't work, what errors do you get?

How are you connected to the share; Wireless or Ethernet cable?

You could put the user/pass information in a credential file with your user read only permissions if you don't want that information in the incantation.

Sorry for the brevity.  I am on the road at the moment and wanted to respond with some basic ideas.

Edit:  I would check to see if the *smbfs package *is installed.  You can do that with this command```
sudo apt-get **[COLOR="Red"]-s [/COLOR]**install smbfs 
```  If it is installed you will get this```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 57 not upgraded.

```

---

### Post by Stephen Shellard on 2011-08-02
Thanks again.

I have put noauto back into fstab, rebooted and attempted to mount using the command as suggested.  The message "only root can do this"  is returned.

The QNAP NAB is connected by Ethernet cable.

Here is the result of a check for smbfs: 

stephen@Zoostorm:~$ sudo apt-get -s install smbfs
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I also tried to mount with the line of code suggested in the previous post, but using sudo.  In this case, the mount manual is returned, and the share does not mount [despite being registered in fstab, noauto.]

---

### Post by capscrew on 2011-08-02
> **Stephen Shellard said:**
> Thanks again.

I have put noauto back into fstab, rebooted and attempted to mount using the command as suggested.  The message "only root can do this"  is returned.

The QNAP NAB is connected by Ethernet cable.

I'm about to board a flight just now.  I will respond  later today.

-Capscrew

---

### Post by capscrew on 2011-08-05
Sorry for the huge delay.  Sometimes short trips turn out to be more arduous than anticipated.  In fact I am still not home.  :-(

> **Stephen Shellard said:**
> ...
I have put noauto back into fstab, rebooted and attempted to mount using the command as suggested.  The message "only root can do this"  is returned.

It turns out that you need to use a different incantation when mounting a share when it is listed in in fstab.  Reading from the ***mount ***man pages shows this clearly```
The non-superuser mounts.
              Normally, only the superuser can  mount  filesystems.   However,
              when fstab contains the user option on a line, anybody can mount
              the corresponding system.

```
Unfortunately, the example is a little unclear.  You should be able to mount the share with an abbreviated mount command like this```

mount //192.168.0.8/qmultimedia 

or

mount /mnt/sonosmusic 

```
These correspond to the man page description of```
Thus, given a line

                     /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

              any user can mount the iso9660 filesystem  found  on  his  CDROM
              using the command

                     mount /dev/cdrom

              or

                     mount /cd

```


I do not have a Linux machine to test this but I trust the man pages to give me correct information.

---

### Post by Stephen Shellard on 2011-08-06
Hopefully you have made it home by now and have recovered from the stresses of your journey.  Thank you for your continuing engagement with these issues.

Firstly, I have succeeded in mounting the drive with the correct permissions, in the way you suggest.  I did have to make a few changes to fstab before success, as errors with the relevant fstab line were being indicated, despite the fact that the same line with the substitution of auto for noauto, seemed to mount the drive on start up without a hitch.  Anyway, removing the gid from the line seems to have made a difference; also adding "users" as an option.  

However the problem of copying files remains:  I am currently being told that it should take 90 hours to copy 440MBs!  The figure does fluctuate, presumably depending on the computer activity. This problem may of course have more to do with the set up of the QNAP NAS, though copying from Windows 7 has been unproblematic.

I am sure I can create a credentials file as suggested to sort out the issue with the password by the way, but suggestions as regards this remaining matter would of course be welcome.  Thanks again for your help.

Post Script.  With regard to the speed of file transfer:  I attempted to copy some data across my Ethernet to a usb drive linked to my Netgear Router [which can be accessed by other computers on the network].  This also proved very slow with a projected 9 hours to copy 116 MBs.  The same files copied to a USB plugged directly into the computer in a matter of seconds.  I guess there is some more profound network problem, linked not only to the QNAP NAS.

---

### Post by capscrew on 2011-08-06
> **Stephen Shellard said:**
> Hopefully you have made it home by now and have recovered from the stresses of your journey.  Thank you for your continuing engagement with these issues.

No, I'm about halfway through my journey.  Unfortunately I still have no Linux machines at my disposal.  I can't test anything before I give you advice.  :-(  > 

Firstly, I have succeeded in mounting the drive with the correct permissions, in the way you suggest.  I did have to make a few changes to fstab before success, as errors with the relevant fstab line were being indicated, despite the fact that the same line with the substitution of auto for noauto, seemed to mount the drive on start up without a hitch.  Anyway, removing the gid from the line seems to have made a difference; also adding "users" as an option.
I believe that is due to how the function mount() reads the fstab file verses the mount system call.  Note the two different mounts in the man pages [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://manpages.ubuntu.com/cgi-bin/search.py?q=mount+&op=&cx=003883529982892832976%3A5zl6o8w6f0s&cof=FORID%3A9&ie=UTF-8&siteurl=manpages.ubuntu.com%2F").  Note that there is mount(2) and mount(8 ).  The numbers in the parenthesis refer to the section of the man pages. >  

However the problem of copying files remains:  I am currently being told that it should take 90 hours to copy 440MBs!  The figure does fluctuate, presumably depending on the computer activity. This problem may of course have more to do with the set up of the QNAP NAS, though copying from Windows 7 has been unproblematic.
My belief is that the Qnap device is running an earlier version of Samba.  It might even be Samba 2.  Ubuntu is using Samba 3.5 and Windows of course implements its own version of the SMB protocol.

There are a few *tuning *parameters that you can try.  I have to say that I haven't found the need to use these, but then again I am using Samba 3.5 and Windows Vista and Win7.  The parameters I'm referring to are used with the mount.cifs (mount -t cifs).  These are *rsize *and *wsize*.  See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html")for info.  For discussion [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1213688")is a past Ubuntu forum thread.    > 

I am sure I can create a credentials file as suggested to sort out the issue with the password by the way, but suggestions as regards this remaining matter would of course be welcome.  Thanks again for your help.

I'm sure you can.  No problem with the help.  Wish I had my own Linux machine though.  ;-)> 

Post Script.  With regard to the speed of file transfer:  I attempted to copy some data across my Ethernet to a usb drive linked to my Netgear Router [which can be accessed by other computers on the network].  This also proved very slow with a projected 9 hours to copy 116 MBs.  The same files copied to a USB plugged directly into the computer in a matter of seconds.  I guess there is some more profound network problem, linked not only to the QNAP NAS.

See my thoughts above.  Read the thread I linked to.  If you wish to search on Google START with [**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://www.google.com/search?q=throughput+samba+rsze+wsize+mount.cifs+site%3Aubuntuforums.org&btnG=Go!#pq=qnap%20slow%20transfer%20speeds&hl=en&gs_id=5n&xhr=t&q=samba+slow+transfer+speeds+rsize&qe=c2FtYmEgc2xvdyB0cmFuc2ZlciBzcGVlZHMgcnNpemU&qesig=vtfCqieuiGmve0uHk8qlRw&pkc=AFgZ2tnMQBlPwG3TtJ7WfDoKbrblvcpDDvhiRecohTIHJXomU6piy6fqoDVY263t2wQ6xlLlu8Z_wzODAjufwPv6e1cnLUY86g&pf=p&sclient=psy&source=hp&pbx=1&oq=samba+slow+transfer+speeds+rsize&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=5d738012b56afd96&biw=1058&bih=542").

---

### Post by Stephen Shellard on 2011-08-07
Thank you again for your attention.  

Your speculation on the version of Samba installed on the NAS sounds probable.  I do have the latest firmware version on the NAS, but otherwise can't find information on the version of SAMBA.  

I have now added the following options to my fstab: rsize=4096,wsize=4096  and this caused no errors, but there is no noticeable change either for better or worse.  I won't pretend to have fuly understood this yet however. In the meantime, I have been trying a completely different tack which may perhaps throw light on my slow network problems.  I noticed that one of the services available on my NAS was for NFS.  I also noticed that the format of the disk would appear to be EXT 3.  Presumably then the NAS can offer access both on the basis of NFS and SAMBA.  I deinstalled smbfs and smbclient and have now mounted the share as NFS. HOWEVER,  whilst I appear to have read and write access to the drive, file transfers are still very slow, comparable to the problems I was experiencing previously.


Perhaps this read out from ifconfig will mean more to someone else than it does to me.

```
stephen@Zoostorm:~$ ifconfig -v
eth0      Link encap:Ethernet  HWaddr 00:24:21:17:01:47  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8996529 (8.9 MB)  TX bytes:4651806 (4.6 MB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9604 (9.6 KB)  TX bytes:9604 (9.6 KB)

```

---

### Post by capscrew on 2011-08-07
> **Stephen Shellard said:**
> Thank you again for your attention.  

Your speculation on the version of Samba installed on the NAS sounds probable.  I do have the latest firmware version on the NAS, but otherwise can't find information on the version of SAMBA.  

I have now added the following options to my fstab: rsize=4096,wsize=4096  and this caused no errors, but there is no noticeable change either for better or worse.  I won't pretend to have fuly understood this yet however. In the meantime, I have been trying a completely different tack which may perhaps throw light on my slow network problems.  I noticed that one of the services available on my NAS was for NFS.  I also noticed that the format of the disk would appear to be EXT 3.  Presumably then the NAS can offer access both on the basis of NFS and SAMBA.  I deinstalled smbfs and smbclient and have now mounted the share as NFS. HOWEVER,  whilst I appear to have read and write access to the drive, file transfers are still very slow, comparable to the problems I was experiencing previously.

I'm sure you understand that when you un-installed smbfs, you removed the Samba client software such as mount.cifs.  You can now longer use that host as  Samba client to mount Samba shares.  But, you can always reinstall it.  ;-)

You can use NFS if you like.  It is only used for Linux (*nix) to Linux hosts though.  You must use Samba for Linux to Windows sharing.  Also you can't browse to NFS shares like most can with Samba shares.  NFS shares (exports is what NFS calls them) must be mounted via fstab or a script.

There are tunables for NFS that are similar to Samba tunables.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.techrepublic.com/blog/opensource/tuning-nfs-for-better-performance/64") for insight.  A NFS search on Google reveals [**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://www.google.com/search?q=nfs+tuning+parameters&btnG=Go!").

---

### Post by Stephen Shellard on 2011-08-08
I discovered a poorly connected wire in my Ethernet wall socket and having sorted this, file transfer is going fine.  Many thanks to capscrew for assistance with mounting my NAS. I note the points about the limitations of using NFS, but I am not seeing this as an issue for me. So, all problems are now now resolved.  Now I need to take a rest [speak to my wife, engage with dog, etc. etc.]:popcorn:

---

### Post by capscrew on 2011-08-08
> **Stephen Shellard said:**
> I discovered a poorly connected wire in my Ethernet wall socket and having sorted this, file transfer is going fine.  Many thanks to capscrew for assistance with mounting my NAS. I note the points about the limitations of using NFS, but I am not seeing this as an issue for me. So, all problems are now now resolved.  Now I need to take a rest [speak to my wife, engage with dog, etc. etc.]:popcorn:

Glad I could help.

---

