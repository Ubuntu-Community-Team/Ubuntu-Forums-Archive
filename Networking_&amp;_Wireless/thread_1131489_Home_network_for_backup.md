---
title: "Home network for backup"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by NJC on 2009-04-20
Attempting to connect 2 computers via router and both connected to cable modem. I'll call them PCA and PCB: PCA is main PC; PCB **ONLY** for backup. 

PCA = tri-boot WinXP/Ubuntu 8.04/9.04
PCB = Ubuntu 9.04 (has a FAT32 partition /windows for backup)

I want to backup files from PCA to PCB. Samba is installed but I can't share (permissions)  /windows partition on PCB.  I've scoured the forums and tried to understand NFS, Samba and SSH but I think I'm making this too complex. Is there any easy way to achieve this?

I have NFS/SSH/Samba installed and both PC's can ping each other.

---

### Post by inobe on 2009-04-20
follow steps from 1 to 11 under **"Share files and folders with other computers"**

then for access from a windows platform to linux' follow steps 1 to 6 under **"Accessing shared folders via Windows"**

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

if that doesn't work be sure that file and printer sharing is setup on the windows platform.

---

### Post by NJC on 2009-04-20
Thanks! That was very straightforward ... although now "Unable to mount partition" from PCA.

---

### Post by inobe on 2009-04-20
have you rebooted all systems since.

please include what you can and cannot do after the restart.

note: i am not familiar with fstab !

---

### Post by NJC on 2009-04-21
I restarted the machines and I was able to get to login screen but it still wouldn't mount - on either machine! Also ran smbpasswd and gave blank passwords for testing but no dice.

---

### Post by zman58 on 2009-04-21
Both PCs should be plugged into the LAN side of the router. The WAN side of the router should be plugged into the cable modem. That is how you would normally share internet connection AND allow both computers to talk with each other. Hopefully that is your configuration.

---

### Post by lisati on 2009-04-21
Sounds like the OP's setup is similar to mine, if not theoretically easier (mine is 4 x PCs with assorted OSes connected to LAN side of one router (which can also do wireless), WAN side of same router hooked up to another router which takes care of ADSL internet connection and wireless as well)

On the Ubuntu installations, I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=202605") to enable file sharing with Samba.

On the XP installations, I ran the network setup wizard, enabling file sharing in the process.

Setting up networking on the one and only Win98 machine in my home network took a little work, fairly straightforward, I'll provide some details if asked. I can't remember what I did with Vista, but it too was fairly straightforward.

---

### Post by NJC on 2009-04-21
I chmod 777  /windows on PCB and it's mounted, but PCA says it's not mounted and won't access it. :confused:

Any further ideas?

---

### Post by NJC on 2009-04-27
Although I wanted a separate /windows partition on Server (PCB), I deleted it, ran shares-admin on a backup folder under Home, and all is well.

---

### Post by Roasted on 2009-04-28
Can you give me a little bit of information in regards to your current situation?

Is PCA your Linux machine?

What hard drives do you have in your computer?

Are you backing up your Windows machine TO your Ubuntu machine?

Do you have a specific hard drive to run this task? Or are you hoping to dump the Windows data onto the same drive you run Ubuntu on as a means of a backup?

Ultimately is your Ubuntu machine intended to be a "Backup Server?"

Note - I have Ubuntu running on my main rig and I have 4 XP desktops in the house that automatically synchronize to it at 3:00 AM every morning, so maybe I can help a bit more if I know your setup a little bit better.

---

### Post by NJC on 2009-04-28
> Is PCA your Linux machine?Sorry for the neophyte terminology. PCA is a XP/Ubuntu Client

> What hard drives do you have in your computer?2 separate XP/Ubuntu drives Client; one drive Server (PCB). 

> Are you backing up your Windows machine TO your Ubuntu machine?Although I'd like that as an eventual option, my files in need of backup are stored on Client's fat32 Ubuntu partition.

> Or are you hoping to dump the Windows data onto the same drive you run Ubuntu on as a means of a backup? Hoping to dump the shared XP/Ubuntu fat32 files to Server.

> Ultimately is your Ubuntu machine intended to be a "Backup Server?"Exactly - I want to make it into a backup file Server. I would like to make an automated backup process also but don't have anything setup currently. Thanks for your help.

---

### Post by Roasted on 2009-04-28
I'll tell you how my setup is, and perhaps you can decide if it's a route you want to take.

I have a 250gb SATA hard drive in my computer that I call my "network drive." It mounts automatically via /etc/fstab to the /media/storage share. Media/storage ultimately the 250gb shared drive.

Within Samba I have 4 users set up. Within Samba I added the users respectively. Then I password protected their shares and set up the users according to their share. Meaning Fred cannot get into Jason's stuff. That way my parents don't go snooping my brother's backup files, etc. :guitar:

Now, on the XP machines, I downloaded SyncBack SE - the free version. I set up a scheduler on each XP computer which synchronizes the users "My Documents" folder to their folder share, which Samba has linked to /media/storage. So when Fred would go to start - run - \\SambaServer\Fred it automatically links to /media/storage on my Ubuntu machine, which is Fred's specific password protected share. The one trick is within SyncBack SE you have to configure the Samba login credentials with it, that way SyncBack SE can authenticate to Samba and run the backup process with ease.

So ultimately, every morning at 3:00 AM, SyncBack SE on the XP computers pushes everybody's "My Documents" down to my server. 

The curve ball here is, I like backups of backups. So you know how I said I have a 250gb network drive? Yeah, well, I have two 250gb drives. The one is a copy of the other. So I have an rsync script which synchronizes my "Network Drive" with the other 250gb drive. This script runs at 4:00 AM with the help of a crontab scheduled task within Ubuntu.

Life is good in the world of Linux. :guitar:

If you need additional help I'll do the best I can to help ya out.

---

