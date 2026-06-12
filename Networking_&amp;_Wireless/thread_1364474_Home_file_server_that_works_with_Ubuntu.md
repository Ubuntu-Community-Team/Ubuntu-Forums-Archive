---
title: "Home file server that works with Ubuntu"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by Mongao on 2009-12-25
Hi all,

I`m kind of a newbie;

I have three computers connected in a home network, 2 running Windows and 1 running Ubuntu. I am in need of a home file server, basically I need a software to run on EACH computer to back-up, accordingly to my chosen schedule, some folders from local drives to the server HD.


I have thought of ordering this :

[http://www.amazon.ca/D-Link-DNS-323-Network-Storage-Enclosure/dp/B000GK8LVE/ref=sr_1_1?ie=UTF8&s=electronics&qid=1261799797&sr=8-1](http://www.amazon.ca/D-Link-DNS-323-Network-Storage-Enclosure/dp/B000GK8LVE/ref=sr_1_1?ie=UTF8&s=electronics&qid=1261799797&sr=8-1)

My questions are:

1) Would Ubuntu recognize it on the network ?
2) Is there any kind of software that I can run in Ubuntu, to back-up some folders say every night at 2 am ? Most servers come bundled with this kind of software for Windows only, but I wonder if there are software written by Ubuntu enthusiasts that works the same way ?

May I install regular Ubuntu or the "server" edition ? I admitt I don`t know what it is exactly....

Thanks so much,

Mongao

---

### Post by memilanuk on 2009-12-25
The Ubuntu machine should 'see' the DNS-323 just fine if it (the Ubuntu box) has Windows networking (Samba) running okay.  Try a search on the model name here and you should get some good returns.

If you search either the forum here or the Community Docs for backup software you should get a lot of good ideas.  I don't know which ones specifically support backing up to SMB/CIFS (Windows filesystem) but I'm sure you'll find something.

Good luck,

Monte

---

### Post by zaphod777 on 2009-12-25
That would work fine but I would recommend something that has at least 2 disks and uses RAID that way when a disk fails your not up the creek.

Something like this
[http://www.lacie.com/us/products/product.htm?pid=11253](http://www.lacie.com/us/products/product.htm?pid=11253)

just remember that with raid 1 you can only use half of the space since it is mirrored. so if you have 2 x 1 TB drives you can only use about 1 TB of space.

Also read the directions I destroyed a raid 5 array before because I thought I had to turn off to replace the drive but I was supposed to hot swap it.

I like the one I linked because it supports bit-torrent and DLNA media server so you can stream media to your PS3 or X-Box.

as far as backup just setup the network share to mount automaticly in Linux and backup with rsync or something like that.

Windows has built in software.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

> Automagically mount SMB shares
In order to have a share mounted automatically every time you reboot, you need to do the following:

With any editor, create a file containing your Windows/Samba user account details:


gksu gedit /etc/samba/user
KDE users must use kdesu rather than gksu and instead of Gedit they can use Kwrite as editor.

... it should contain two lines as follows:


username=samba_user
password=samba_user_password
Note: "samba_user" = the user name on the samba server (may be different from your log-in name on the client). "samba_user_password" is the password you assigned to the samba_user on the samba server.

Save the file and exit gedit.

Change the permissions on the file for security:


sudo chmod 0400 /etc/samba/user # permissions of 0400 = read only
Now create a directory where you want to mount your share (e.g. /media/samba_share):


sudo mkdir /media/samba_share
Now, using any editor, and add a line to /etc/fstab for your SMB share as follows:


sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
Add a line for your SMB share:


//myserver_ip_address/myshare  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0
The share will mount automatically when you boot. The "noexec" option prevents executable scripts running from the SMB share.

To mount the share now, without rebooting,


sudo mount /media/samba_share
You can unmount the share with :


sudo umount /media/samba_share
If you wish to increase security at the expense of convenience, use this line in /etc/fstab


//myserver_ip_address/myshare  /media/samba_share  cifs  noauto,credentials=/etc/samba/user,noexec  0 0
The noexec" option prevents executable scripts running from the SMB share.

Edit /etc/samba/user, remove the password (leave just the samba user).

Now the share will NOT automatically mount when you boot and you will be asked for your samba password.

Mount the share with :


sudo mount /media/samba_share
CIFS may cause a shutdown error.

CIFS VFS: Server not responding.

---

### Post by MaxIBoy on 2009-12-26
The server edition of Ubuntu uses a low-tickrate kernel and no graphics/sound drivers, plus the default install is command-line only. Far as I know that's the only difference.

The backup software probably won't run server-side, it will likely run on the computers you back files up FROM. You can use sshfs + rsync in a cron job to accomplish this.

Hardware support isn't too big a deal for a fileserver. You need a working NIC and hard drive controller, both of which Linux has extensive drivers for-- doesn't matter if your video card won't work, or even if you have a video card at all. Use any cheap used computer you find. Slap a new hard drive in it, (don't trust used ones!) blow the dust out regularly, and it will serve you for years! 

You can sometimes find Windows users willing to give up ancient computers for free in exchange for recovering files from them (won't even boot up properly due to infections and whatnot, nothing a PuppyLinux CD won't handle...) That's how I got my hands on [this beauty]("http://ubuntuforums.org/showpost.php?p=7205109&postcount=265").

You wouln't believe how much a computer like that is good for. I run it as a torrent slave, game server, and I even host my website on it now. I recently upgraded the RAM from 128 Mb to 192-- no performance boost at all, guess I didn't need the extra memory!

---

### Post by zaphod777 on 2009-12-26
> **MaxIBoy said:**
> The server edition of Ubuntu uses a low-tickrate kernel and no graphics/sound drivers, plus the default install is command-line only. Far as I know that's the only difference.

The backup software probably won't run server-side, it will likely run on the computers you back files up FROM. You can use sshfs + rsync in a cron job to accomplish this.

Hardware support isn't too big a deal for a fileserver. You need a working NIC and hard drive controller, both of which Linux has extensive drivers for-- doesn't matter if your video card won't work, or even if you have a video card at all. Use any cheap used computer you find. Slap a new hard drive in it, (don't trust used ones!) blow the dust out regularly, and it will serve you for years! 

You can sometimes find Windows users willing to give up ancient computers for free in exchange for recovering files from them (won't even boot up properly due to infections and whatnot, nothing a PuppyLinux CD won't handle...) That's how I got my hands on [this beauty](http://ubuntuforums.org/showpost.php?p=7205109&postcount=265).

and a beauty she is!

---

### Post by zaphod777 on 2009-12-26
You might also be able to get an old pc from work that is about to make it in the recycle bin.

---

### Post by Mongao on 2009-12-26
Thanks to everybody that replied;

I am REALLY an amateur Ubuntu user, but I would like to go deep on it.

I prefer to buy a NAS rather than using old PC`s, I`ll use a RAID configuration.

Well, I assume the D-LINK would work well with Ubuntu if I have Samba installed, OK ? I`ll mount everything next week and will try editing the TXT files as mentioned.

Thanks,
Mongao

---

### Post by zaphod777 on 2009-12-26
> **Mongao said:**
> Thanks to everybody that replied;

I am REALLY an amateur Ubuntu user, but I would like to go deep on it.

I prefer to buy a NAS rather than using old PC`s, I`ll use a RAID configuration.

Well, I assume the D-LINK would work well with Ubuntu if I have Samba installed, OK ? I`ll mount everything next week and will try editing the TXT files as mentioned.

Thanks,
Mongao

D-Link should work fine but I didn't see any mention of it having a raid configuration on it. 

Ubuntu already has Samba installed the directions are just so you can have it mount automaticly as a network drive. You can use a bookmark but for backing up a network drive will work better.

---

### Post by memilanuk on 2009-12-26
[http://www.smallnetbuilder.com/nas/nas-reviews/29671-dlinkdns323review?showall=&start=2](http://www.smallnetbuilder.com/nas/nas-reviews/29671-dlinkdns323review?showall=&start=2)

Individual, JBOD, Raid 0, & Raid 1

---

### Post by Mongao on 2009-12-26
Thanks for the replies, although I may use the D-Link DNS using computers running Windows and Ubuntu, I assume I can use ONLY Ubuntu in all computers if I want, right ?

As far as I understood, I can neglect the Windows utility that comes bundled with the D-Link DNS and use the Web-based feature under Ubuntu to configure it, right ? Can anyone confirm please ?

I am in Canada and I have just found out that the DNS-343 model, that features 4 HDDs instead of two hasn`t been released here, only in the USA. I may wait some extra weeks to check if it will be available here.

Thanks,

Mongao

---

### Post by memilanuk on 2009-12-26
Might try that site I linked to (smallnetbuilder.com); they have reviews on most any of the NASes you may consider, including the 343.

---

### Post by zaphod777 on 2009-12-26
You can have ubuntu and windows it shouldn't matter. 

Yes you don't need the utility it seams to be just for assigning the IP address the first time which you can do through the web interface.

Just check the router dhcp tables for new devices when connected to find it's ip or use an ip scanner.

---

### Post by paxmark1 on 2009-12-27
google dns-323 wiki and you will find the funplug site.

The 323 does have raid,  bittorrent, inotify_upnp inotify_itune from the beginning and with the fun plug script (if you feel up to it) you can get ssh and mediatomb to work.  

Dlink also has a wiki over the 323

---

### Post by Mongao on 2009-12-28
Thanks for the replies !

Mongao

---

### Post by Mongao on 2009-12-28
Please, can anyone give me very basic instructions on how to use RSYNC ?

I am looking for a software that would allow me to choose the folders I want to have backed-up say every night.

Thanks,

Mongao

---

