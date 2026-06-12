---
title: "issues with DLink DNS-323 NAS permissions"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by wa1d0rf on 2012-05-11
I have a DLink DNS-323 NAS external drive enclosure and I'm trying to get it to connect with my Ubuntu 12.04 system.  I've been trying various suggestions here and on the web without complete success.  Initially, I had the freshly installed system working or so I thought.  I then tried to transfer downloaded TV shows to this drive as a backup.  The Nautilus on my Ubuntu system reported a permissions issue when it was creating the folder for the files to be copied to.

My fstab file has the following entry:
```
//192.168.1.129/Volume_1    /NAS    cifs  guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```The DNS-323 is setup to allow all users read-write access.  I can see the contents of the drive including contents of subfolders.  I can create folders, but cannot copy files to it from any of my internal drives.  Nautilus reports that I don't have permissions.

Does anybody have any suggestions?

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> I have a DLink DNS-323 NAS external drive enclosure and I'm trying to get it to connect with my Ubuntu 12.04 system.  I've been trying various suggestions here and on the web without complete success.  Initially, I had the freshly installed system working or so I thought.  I then tried to transfer downloaded TV shows to this drive as a backup.  The Nautilus on my Ubuntu system reported a permissions issue when it was creating the folder for the files to be copied to.

My fstab file has the following entry:
```
//192.168.1.129/Volume_1    /NAS    cifs  guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```The DNS-323 is setup to allow all users read-write access.  I can see the contents of the drive including contents of subfolders.  I can create folders, but cannot copy files to it from any of my internal drives.  Nautilus reports that I don't have permissions.

Does anybody have any suggestions?

Many times Nautilus can't tell what the OS file permissions are.  This seems to be an configuration problems with the permissions setting the DLink.  How did you set the permissions?  What specifically are the settings?

Samba does not ultimately set the permissions.  The OS  settings are the final word on that.

Edit: What is the exact share name? Is it Volume_1 (not the dir)?

Edit2:  What do you get from this command```
mount
```

---

### Post by wa1d0rf on 2012-05-11
The following is what I get when I execute the "mount" command in terminal:
```
john@john-ubuntu:/$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /disk1 type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
/dev/sdb2 on /disk2 type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
/dev/sdc1 on /disk3 type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
/dev/sdd1 on /disk4 type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//192.168.1.129/Volume_1 on /NAS type cifs (rw)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
//192.168.1.129/Volume_1 on /media/DNS type cifs (rw)
```The settings on the DNS-323 are set to allow all users RW access, which is the default setting when you configure the thing.

Yes, the share is setup as "Volume_1".

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> The following is what I get when I execute the "mount" command in terminal:
```
john@john-ubuntu:/$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
...
/dev/sda2 on /disk1 type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
/dev/sdb2 on /disk2 type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
/dev/sdc1 on /disk3 type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
/dev/sdd1 on /disk4 type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//192.168.1.129/Volume_1 on /NAS type cifs (rw)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
//192.168.1.129/Volume_1 on /media/DNS type cifs (rw)
```The settings on the DNS-323 are set to allow all users RW access, which is the default setting when you configure the thing.

Yes, the share is setup as "Volume_1".

What is the output of ```
ls -al /NAS
```

---

### Post by wa1d0rf on 2012-05-11
This is what I get:
```
john@john-ubuntu:/$ ls -al /NAS
total 4
drwxrwxrwx  5 john john    0 May 11 10:09 .
drwxr-xr-x 28 root root 4096 May 11 07:29 ..
drwx------  2 john john    0 Apr  6 16:16 .systemfile
drwxrwxrwx  4 john john    0 May 11 10:09 .Trash-1000
drwxrwxrwx  4 john john    0 May 11 10:07 TVshows
```

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> This is what I get:
```
john@john-ubuntu:/$ ls -al /NAS
total 4
drwxrwxrwx  5 john john    0 May 11 10:09 .
drwxr-xr-x 28 root root 4096 May 11 07:29 ..
drwx------  2 john john    0 Apr  6 16:16 .systemfile
drwxrwxrwx  4 john john    0 May 11 10:09 .Trash-1000
drwxrwxrwx  4 john john    0 May 11 10:07 TVshows
```

Is this what you expected to see in this folder? Is this the contents of Volume_1?  You certainly have rw and x on this directory.  What is in the directory TVshows?

I'm sorry.  I'm a bit distracted here at the moment.  I just noticed you have this share also mounted at /media/DNS.  Is that what you wanted?  What is in /media/DNS?

---

### Post by wa1d0rf on 2012-05-11
Yes, it shows the correct folders that are currently in that share.  That isn't my issue however.  As I stated at the beginning, I can see the existing folders, I can create folders, but I can't copy files from my ubuntu system into the NAS mount point using Nautilus.

I have been trying various "solutions" and one was to use a mount point in the "/media" folder.  I don't need this any longer and I have removed it from the fstab file.  My bad....I just haven't rebooted yet to totally remove it.

---

### Post by bab1 on 2012-05-11
```

```> **wa1d0rf said:**
> Yes, it shows the correct folders that are currently in that share.  That isn't my issue however.  As I stated at the beginning, I can see the existing folders, I can create folders, but I can't copy files from my ubuntu system into the NAS mount point using Nautilus.

I want to see the folders created by you in TVshows and inside one of those folders.

Edit:  Can you copy a file from your home directory to the /NAS directory from the command line?  Like this```
cp /home/john/*somefile /NAS*
```

---

### Post by wa1d0rf on 2012-05-11
> **bab1 said:**
> I want to see the folders created by you in TVshows and inside one of those folders.

Edit:  Can you copy a file from your home directory to the /NAS directory from the command line?  Like this```
cp *somefile /NAS*
```

I've only just begun to add files.  This is what I have in "TVshows":
```
john@john-ubuntu:/NAS/TVshows$ ls -al
total 0
drwxrwxrwx 4 john john 0 May 11 10:07 .
drwxrwxrwx 5 john john 0 May 11 10:09 ..
drwxrwxrwx 5 john john 0 May  5 19:34 30 Rock
drwxrwxrwx 4 john john 0 May  5 22:37 The West Wing
```My current issue arose when I was trying to add folders to "The West Wing" folder that hold each season's episodes.  Here is what is currently in "The West Wing":

```
john@john-ubuntu:/NAS/TVshows/The West Wing$ ls -al
total 0
drwxrwxrwx 4 john john 0 May  5 22:37 .
drwxrwxrwx 4 john john 0 May 11 10:07 ..
drwxrwxrwx 2 john john 0 May  5 22:37 The.West.Wing.S01.720p.WEB-DL.H.264-MERCK
drwxrwxrwx 2 john john 0 May 11 10:12 The.West.Wing.S02.720p.WEB-DL.AAC2.0.H.264-LP
```

---

### Post by bab1 on 2012-05-11
Can you copy *_files_* from your home folder to /NAS/TVshows via the command line?

It all looks okay to me so far.  But then again these are all folders with no files.

Where are the files that you want to put on the NAS right now?  Where are you storing them presently?

---

### Post by wa1d0rf on 2012-05-11
> **bab1 said:**
> Can you copy *_files_* from your home folder to /NAS/TVshows via the command line?

It all looks okay to me so far.  But then again these are all folders with no files.

Where are the files that you want to put on the NAS right now?  Where are you storing them presently?

I'm trying to copy the whole folder called "The.West.Wing.S07.720p.WEB-DL.AAC2.0.H.264-MC" in Nautilus by highlighting the folder name, right-click, choose cut, navigate to the /NAS/TVshows/The West Wing, then right-click, choose paste.  The folder permissions are as follows:
```
drwxr-xr-x  2 john john       4096 Jan  5 04:21 The.West.Wing.S07.720p.WEB-DL.AAC2.0.H.264-MC
```This is what the files look like on a local drive on my system.  The mount point is called "/disk4".

```
john@john-ubuntu:/disk4$ ls -al The.West.Wing.S07.720p.WEB-DL.AAC2.0.H.264-MC
total 29795420
drwxr-xr-x  2 john john       4096 Jan  5 04:21 .
drwxr-xr-x 82 john john      61440 May 10 23:37 ..
-rw-r--r--  1 john john 1435441613 Jan  5 04:20 The.West.Wing.S07E01.The.Ticket.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1367698579 Jan  5 04:19 The.West.Wing.S07E02.The.Mommy.Problem.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1355535179 Jan  5 04:21 The.West.Wing.S07E03.Message.of.the.Week.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1337309686 Jan  5 04:20 The.West.Wing.S07E04.Mr.Fros.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1405717172 Jan  5 04:21 The.West.Wing.S07E05.Here.Today.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1374293598 Jan  5 04:20 The.West.Wing.S07E06.The.Al.Smith.Dinner.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1374932623 Jan  5 04:21 The.West.Wing.S07E07.The.Debate.West.Coast.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1390564871 Jan  5 04:20 The.West.Wing.S07E08.Undecideds.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1350090412 Jan  5 04:21 The.West.Wing.S07E09.The.Wedding.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1408480811 Jan  5 04:20 The.West.Wing.S07E10.Running.Mates.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1433740417 Jan  5 04:19 The.West.Wing.S07E11.Internal.Displacement.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1397849790 Jan  5 04:21 The.West.Wing.S07E12.Duck.and.Cover.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1397729892 Jan  5 04:20 The.West.Wing.S07E13.The.Cold.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1388862133 Jan  5 04:19 The.West.Wing.S07E14.Two.Weeks.Out.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1365347862 Jan  5 04:21 The.West.Wing.S07E15.Welcome.to.Wherever.You.Are.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1427460557 Jan  5 04:21 The.West.Wing.S07E16.Election.Day.Pt.1.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1372841224 Jan  5 04:19 The.West.Wing.S07E17.Election.Day.Pt.2.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1400172245 Jan  5 04:21 The.West.Wing.S07E18.Requiem.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1393598010 Jan  5 04:21 The.West.Wing.S07E19.Transition.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1346202038 Jan  5 04:21 The.West.Wing.S07E20.The.Last.Hurra.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1384850402 Jan  5 04:20 The.West.Wing.S07E21.Institutional.Memory.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1371779902 Jan  5 04:19 The.West.Wing.S07E22.Tomorrow.720p.WEB-DL.AAC2.0.H.264-MC.mkv
```

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> I'm trying to copy the whole folder called "The.West.Wing.S07.720p.WEB-DL.AAC2.0.H.264-MC" in Nautilus by highlighting the folder name, right-click, choose cut, navigate to the /NAS/TVshows/The West Wing, then right-click, choose paste.  The folder permissions are as follows:
```
drwxr-xr-x  2 john john       4096 Jan  5 04:21 The.West.Wing.S07.720p.WEB-DL.AAC2.0.H.264-MC
```This is what the files look like on a local drive on my system.  The mount point is called "/disk4".

```
john@john-ubuntu:/disk4$ ls -al The.West.Wing.S07.720p.WEB-DL.AAC2.0.H.264-MC
total 29795420
drwxr-xr-x  2 john john       4096 Jan  5 04:21 .
drwxr-xr-x 82 john john      61440 May 10 23:37 ..
-rw-r--r--  1 john john 1435441613 Jan  5 04:20 The.West.Wing.S07E01.The.Ticket.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1367698579 Jan  5 04:19 The.West.Wing.S07E02.The.Mommy.Problem.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1355535179 Jan  5 04:21 The.West.Wing.S07E03.Message.of.the.Week.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1337309686 Jan  5 04:20 The.West.Wing.S07E04.Mr.Fros.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1405717172 Jan  5 04:21 The.West.Wing.S07E05.Here.Today.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1374293598 Jan  5 04:20 The.West.Wing.S07E06.The.Al.Smith.Dinner.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1374932623 Jan  5 04:21 The.West.Wing.S07E07.The.Debate.West.Coast.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1390564871 Jan  5 04:20 The.West.Wing.S07E08.Undecideds.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1350090412 Jan  5 04:21 The.West.Wing.S07E09.The.Wedding.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1408480811 Jan  5 04:20 The.West.Wing.S07E10.Running.Mates.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1433740417 Jan  5 04:19 The.West.Wing.S07E11.Internal.Displacement.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1397849790 Jan  5 04:21 The.West.Wing.S07E12.Duck.and.Cover.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1397729892 Jan  5 04:20 The.West.Wing.S07E13.The.Cold.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1388862133 Jan  5 04:19 The.West.Wing.S07E14.Two.Weeks.Out.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1365347862 Jan  5 04:21 The.West.Wing.S07E15.Welcome.to.Wherever.You.Are.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1427460557 Jan  5 04:21 The.West.Wing.S07E16.Election.Day.Pt.1.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1372841224 Jan  5 04:19 The.West.Wing.S07E17.Election.Day.Pt.2.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1400172245 Jan  5 04:21 The.West.Wing.S07E18.Requiem.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1393598010 Jan  5 04:21 The.West.Wing.S07E19.Transition.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1346202038 Jan  5 04:21 The.West.Wing.S07E20.The.Last.Hurra.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1384850402 Jan  5 04:20 The.West.Wing.S07E21.Institutional.Memory.720p.WEB-DL.AAC2.0.H.264-MC.mkv
-rw-r--r--  1 john john 1371779902 Jan  5 04:19 The.West.Wing.S07E22.Tomorrow.720p.WEB-DL.AAC2.0.H.264-MC.mkv
```for a test I would try and copy just one file from /disk4.  First I would g to the directory /disk4```
cd /disk4
```

Then I would copy the file *The.West.Wing.S07E01.The.Ticket.720p.WEB-DL.AAC2.0.H.264-MC.mkv* to /NAS/TVshows/whatever.dir.you want like this```
cp The.West.Wing.S07E01.The.Ticket.720p.WEB-DL.AAC2.0.H.264-MC.mkv /NAS/TVshows/*[COLOR="Red"]whatever.dir.you.want.to.put.it.in[/COLOR]*
```

If it is **not** successful, what error codes do you get?  If you **are** successful, what permissions does the file have?

Essentially I'm trying to separate any file transfer problems from possible Nautilus specific problems.

---

### Post by wa1d0rf on 2012-05-11
> **bab1 said:**
> for a test I would try and copy just one file from /disk4.  First I would g to the directory /disk4```
cd /disk4
```Then I would copy the file *The.West.Wing.S07E01.The.Ticket.720p.WEB-DL.AAC2.0.H.264-MC.mkv* to /NAS/TVshows/whatever.dir.you want like this```
cp The.West.Wing.S07E01.The.Ticket.720p.WEB-DL.AAC2.0.H.264-MC.mkv /NAS/TVshows/*[COLOR=Red]whatever.dir.you.want.to.put.it.in[/COLOR]*
```If it is **not** successful, what error codes do you get?  If you **are** successful, what permissions does the file have?

Essentially I'm trying to separate any file transfer problems from possible Nautilus specific problems.

I tried to copy one file from /disk4 directly into /NAS/TVshows and this is what I get:
```
john@john-ubuntu:/disk4$ cp Wicked.Tuna.S01E03.Weekend.Warriors.HDTV.XviD-CRiMSON.avi /NAS/TVshows
cp: cannot create regular file `/NAS/TVshows/Wicked.Tuna.S01E03.Weekend.Warriors.HDTV.XviD-CRiMSON.avi': Permission denied
```Doesn't seem to be necessarily Nautilus related.

---

### Post by bab1 on 2012-05-11
At this point all I can give you is my mount in fstab and you try that (with whatever mods you think best).

I mount my Samba shares with this```
//server/share/ /media/mount cifs  user,username=user,credentials=/home/*[COLOR="Blue"]user[/COLOR]*/.smbcred,uid=1000,gid=1000,nobrl,noauto,iocharset=utf8  0  0
```

I noticed you used the *guest* option.  This does not define the share as available for guests.  What is does is suppresses the request for login.  From the man pages *"guest - don´t prompt for a password"* and elsewhere *"mount.cifs will prompt for a password, unless the guest option is specified."*.

My best guest is that the NAS doesn't know john is logged in and therefore you don't have permissions.  Make sure you are user 1000 and that you group ID is also 1000.  If not then you need to use the appropriate uid and gid.

If you don't want to login make a .creds file as I did.  Also the first user in the line is so a mortal user can mount the share form the terminal.  If you are auto mounting from the fstab then drop the *user* and the *noauto* from the line.  i set the permissions in a different way so that is why no mention in this either.

I move 75GB at a time with 4 different users (my backups) so I know it works.  I control user access by the group.  I don't really care who is the "user", I care what the group is.

---

### Post by wa1d0rf on 2012-05-11
thanks for trying, but I've tried a 1000 variations with fstab and no joy.  I'm not 100% sure what credentials I'm suppose to use.  The only account I have on the NAS is my admin account.  I've tried that in the fstab entry and I've tried my ubuntu account info too.  why is it so difficult to do?

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> thanks for trying, but I've tried a 1000 variations with fstab and no joy.  I'm not 100% sure what credentials I'm suppose to use.  The only account I have on the NAS is my admin account.  I've tried that in the fstab entry and I've tried my ubuntu account info too.  why is it so difficult to do?

What fun would easy be.  I would not give up so fast.  With Samba (and in this case we don't even know which version) you need to have a OS user and a Samba user (same name would be nice).  If your admin account is not the same as your Ubuntu user account then we have permissions problems.  The credentials file is used so you don't have to login each time if the share only allows (valid) samba users.

Are you able to get to the command line on the DLink?  Can we see what the Samba config file looks like (smb.conf)?

Its up to you, I'll help if you want.  if not I'll let it go.  I can annotate the entire fstab entry if you like.  Or...

---

### Post by wa1d0rf on 2012-05-11
> **bab1 said:**
> What fun would easy be.  I would not give up so fast.  With Samba (and in this case we don't even know which version) you need to have a OS user and a Samba user (same name would be nice).  If your admin account is not the same as your Ubuntu user account then we have permissions problems.  The credentials file is used so you don't have to login each time if the share only allows (valid) samba users.

Are you able to get to the command line on the DLink?  Can we see what the Samba config file looks like (smb.conf)?

Its up to you, I'll help if you want.  if not I'll let it go.  I can annotate the entire fstab entry if you like.  Or...

Your last post sounded (to me) like you were giving up.  Ok, my ubuntu account is "john" and the Dlink account that I use to log into the admin website is "admin".  I don't know if I can get to a command line on the Dlink, all I know how to use is the website that allows for configuration of the device.

It has options to allow me to create accounts and groups.  I wonder if I need to create an account there with the same credentials as I use in ubuntu.  Do I need to do anything to the smb.conf file on ubuntu?

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> Your last post sounded (to me) like you were giving up.  Ok, my ubuntu account is "john" and the Dlink account that I use to log into the admin website is "admin".  I don't know if I can get to a command line on the Dlink, all I know how to use is the website that allows for configuration of the device.

It has options to allow me to create accounts and groups.  I wonder if I need to create an account there with the same credentials as I use in ubuntu.  Do I need to do anything to the smb.conf file on ubuntu?

I am assuming you are using the Ubuntu host as a client only.  No Samba **Server**.  The default smb.conf file should be okay

Of course you need a user=john on the NAS and that user should be able to access the share we are using.

Then you can see what happens.  We may need to make other adjustments.

---

### Post by wa1d0rf on 2012-05-11
> **bab1 said:**
> I am assuming you are using the Ubuntu host as a client only.  No Samba **Server**.  The default smb.conf file should be okay

Of course you need a user=john on the NAS and that user should be able to access the share we are using.

Then you can see what happens.  We may need to make other adjustments.

OK, that makes sense.  I created a user on the Dlink the same as my ubuntu account.  Then I restarted the Dlink.  I edited my fstab as follows:

```
//192.168.1.129/Volume_1 /NAS cifs  users,credentials=/.smbcredentials,uid=1000,gid=1000,rw,auto,nobrl,iocharset=utf8  0  0
```

then I did a mount -a.  I'm hoping this command does a remount of all shares in the fstab.  Am I correct?

Then I attempted to create a document in the /NAS/TVshows folder and now I was able to create a document.  No more "permission denied" error.  That looked promising, so I attempted to transfer one file from /disk4 to the Dlink and it started to copy!  It errored out when it was finished copying however.  I tried another file and it gave me the "permission denied" error immediately!

Maybe we are closer now?

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> OK, that makes sense.  I created a user on the Dlink the same as my ubuntu account.  Then I restarted the Dlink.  I edited my fstab as follows:

```
//192.168.1.129/Volume_1 /NAS cifs  users,credentials=/.smbcredentials,uid=1000,gid=1000,rw,auto,nobrl,iocharset=utf8  0  0
```

then I did a mount -a.  I'm hoping this command does a remount of all shares in the fstab.  Am I correct?

Then I attempted to create a document in the /NAS/TVshows folder and now I was able to create a document.  No more "permission denied" error.  That looked promising, so I attempted to transfer one file from /disk4 to the Dlink and it started to copy!  It errored out when it was finished copying however.  I tried another file and it gave me the "permission denied" error immediately!

Maybe we are closer now?

We are closer, but not home yet.  Did you really mean to put the creds at /.smbcredentials not /home/john/.smbcredentials?  are you the only user on Ubuntu?  Are you uid=1000?  Why no username=john t go with the creds file.  BTW what is in your cred file?

Can you post what is in the directory that partially transferred?

---

### Post by wa1d0rf on 2012-05-11
> **bab1 said:**
> We are closer, but not home yet.  Did you really mean to put the creds at /.smbcredentials not /home/john/.smbcredentials?  are you the only user on Ubuntu?  Are you uid=1000?  Why no username=john t go with the creds file.  BTW what is in your cred file?

Can you post what is in the directory that partially transferred?

One of the posts (on another forum) suggested making a credentials file and that's where they suggested it should go.  Would it be better in the /home/john/ folder?  Yes, I am the only user that logs into this ubuntu computer.  I ran the "id" command and it states that "john" is uid 1000 and gid 1000.  The smbcredentials file has the following (password has been masked for my protection LOL):

```
username=john
password=********
```

So you think I should add "username=john to the fstab entry instead of "users"?

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> One of the posts (on another forum) suggested making a credentials file and that's where they suggested it should go.  Would it be better in the /home/john/ folder?  Yes, I am the only user that logs into this ubuntu computer.  I ran the "id" command and it states that "john" is uid 1000 and gid 1000.  The smbcredentials file has the following (password has been masked for my protection LOL):

```
username=john
password=********
```

So you think I should add "username=john to the fstab entry instead of "users"?

I think that it works where ever you want to put it.  Putting it in the root of the entire file system (/) is a little messy.  In non-threatening systems, placing it in the users home dir is just neater.  In systems where security is important most folks put the cred file in the user root's home dir (/root) which means the attacker has to know the root password or in the case of Ubuntu the password of a sudoer (e.g John's password).

You have the right info in the cred file.

I wonder...  You have always used the IP address rather than a hostname (actually a NETBIOS NAME), could that be a problem.  It sure stops you from browsing for the share with the GUI.

---

### Post by wa1d0rf on 2012-05-12
> **bab1 said:**
> I think that it works where ever you want to put it.  Putting it in the root of the entire file system (/) is a little messy.  In non-threatening systems, placing it in the users home dir is just neater.  In systems where security is important most folks put the cred file in the user root's home dir (/root) which means the attacker has to know the root password or in the case of Ubuntu the password of a sudoer (e.g John's password).

You have the right info in the cred file.

I wonder...  You have always used the IP address rather than a hostname (actually a NETBIOS NAME), could that be a problem.  It sure stops you from browsing for the share with the GUI.

Yes, always the IP address.  I can browse the share fine with both terminal and Nautilus and I was able to create folders and documents there for a while yesterday (still couldn't copy files) but not now.  It's back to "permission denied" whenever I try to create folders/files and copy folders/files.  

I have no idea what the hostname would be.  The devicename on my network (as per router device list) is "dlink-2B23C7".  Can I use that name interchangeably with the IP address?  What would this get me anyway?  The manual that came with it is written in "Engrish" and only the bare minimum of information.  It has software, but only for Windoze.  I only use Ubuntu however, so I have to use the web interface for configuration.  The Dlink uses a linux distribution as the OS, so there is nothing to do with Windoze here.

Added info:  I tried "//dlink-2B23C7/Volume_1" instead of the IP addess and sharename and had no effect.  I can still browse the share but cannot create folders/files. :(

---

### Post by bab1 on 2012-05-12
> **wa1d0rf said:**
> Yes, always the IP address.  I can browse the share fine with both terminal and Nautilus and I was able to create folders and documents there for a while yesterday (still couldn't copy files) but not now.  It's back to "permission denied" whenever I try to create folders/files and copy folders/files.  

I have no idea what the hostname would be.  The devicename on my network (as per router device list) is "dlink-2B23C7".  Can I use that name interchangeably with the IP address?  What would this get me anyway?  The manual that came with it is written in "Engrish" and only the bare minimum of information.  It has software, but only for Windoze.  I only use Ubuntu however, so I have to use the web interface for configuration.  The Dlink uses a linux distribution as the OS, so there is nothing to do with Windoze here.

Added info:  I tried "//dlink-2B23C7/Volume_1" instead of the IP addess and sharename and had no effect.  I can still browse the share but cannot create folders/files. :(

Is there a Places>>Network menu you can follow to see the share? if you follow that you will eble able to mount via Nautilus.  I'm talking about *browsing **to** the share* not just viewing the data in the share.  Their is a difference.  Try it and see what happens.

I would like you to use the fstab entry as I did.  Don't leave out parts and add others.  You can just cut and paste the entry from below.  I used your name etc. so it should work.  If it does I will explain what the difference is.```
//192.168.1.129/Volume_1/ /NAS cifs  user,username=john,credentials=/.smbcredentials,uid=1000,gid=1000,nobrl,iocharset=utf8  0  0
```

---

### Post by wa1d0rf on 2012-05-12
> **bab1 said:**
> Is there a Places>>Network menu you can follow to see the share? if you follow that you will eble able to mount via Nautilus.  I'm talking about *browsing **to** the share* not just viewing the data in the share.  Their is a difference.  Try it and see what happens.

I would like you to use the fstab entry as I did.  Don't leave out parts and add others.  You can just cut and paste the entry from below.  I used your name etc. so it should work.  If it does I will explain what the difference is.```
//192.168.1.129/Volume_1/ /NAS cifs  user,username=john,credentials=/.smbcredentials,uid=1000,gid=1000,nobrl,iocharset=utf8  0  0
```

Well, the former "Places" is now part of Nautilus in Ubuntu 12.04.  There is a link on the left column called "Browse Network".  I went there and it shows the Dlink and another icon for "Windows Network".  The windows network shows two groups:  MSHOME and WORKGROUP.  Within the WORKGROUP is the dlin icon again.  Within the MSHOME group it only shows my ubuntu server (another ubuntu machine I have, this is not the one I'm having issues copying files from).  I'm not sure what group my ubuntu machine is in, but maybe this is a clue as to why the permissions are failing?

I changed my fstab with the entry you provided (you did say make changes as you wish, last time!) and I rebooted the system (not just the umount and mount commands) and there is no difference.

---

### Post by bab1 on 2012-05-13
> **wa1d0rf said:**
> Well, the former "Places" is now part of Nautilus in Ubuntu 12.04.  There is a link on the left column called "Browse Network".  I went there and it shows the Dlink and another icon for "Windows Network".  The windows network shows two groups:  MSHOME and WORKGROUP.  Within the WORKGROUP is the dlin icon again.  Within the MSHOME group it only shows my ubuntu server (another ubuntu machine I have, this is not the one I'm having issues copying files from).  I'm not sure what group my ubuntu machine is in, but maybe this is a clue as to why the permissions are failing?
The workgroup is used only to associate various hosts (computers) visually.  You could have all the hosts in one workgroup or the other if you wanted.  Having them in multiple workgroups will not deny you access.> 

I changed my fstab with the entry you provided (you did say make changes as you wish, last time!) and I rebooted the system (not just the umount and mount commands) and there is no difference.
I think we will have to go back to the basics here.  If only to diagnose the problem.  This is going to take a few steps and negative answers are just as important as positive ones.

Start by commenting out the mount line for the share in fstab.  In other words there will be no shares mounted via fstab.  Then browse for the share.  It should be the "dlin icon" you mentioned.  See if you  can access the share.  If you can see if you can create a file (right click>>create a document).

What do you get from this command```
smbtree
```
Let's see if you can view the mounted share via the terminal.  Make sure you are in your home directory and post what you get from this command ```
ls -lt .gvfs
```

---

### Post by wa1d0rf on 2012-05-13
> **bab1 said:**
> The workgroup is used only to associate various hosts (computers) visually.  You could have all the hosts in one workgroup or the other if you wanted.  Having them in multiple workgroups will not deny you access.
I think we will have to go back to the basics here.  If only to diagnose the problem.  This is going to take a few steps and negative answers are just as important as positive ones.

Start by commenting out the mount line for the share in fstab.  In other words there will be no shares mounted via fstab.  Then browse for the share.  It should be the "dlin icon" you mentioned.  See if you  can access the share.  If you can see if you can create a file (right click>>create a document).

What do you get from this command```
smbtree
```Let's see if you can view the mounted share via the terminal.  Make sure you are in your home directory and post what you get from this command ```
ls -lt .gvfs
```

The smbtree command returns this:
```
john@john-ubuntu:~$ smbtree
Enter john's password: 
MSHOME
    \\UBUNTU-SERVER          ubuntu-server server (Samba, Ubuntu)
        \\UBUNTU-SERVER\print$             Printer Drivers
        \\UBUNTU-SERVER\IPC$               IPC Service (ubuntu-server server (Samba, Ubuntu))
    \\DLINK-2B23C7           DNS-323
```

I'm not sure what this command is suppose to do or mean, but his is what it returns:
```
john@john-ubuntu:~$ ls -lt .gvfs
total 0
```

I tried to copy the files I already have on the Dlink back to one of my local drives and I got an error part way through the copy.  I think maybe there is a physical issue with the hard drive in the Dlink.  I had two drives in a RAID 0 configuration before and removed one and reformatted, that's when this issue began.

---

### Post by bab1 on 2012-05-13
> **wa1d0rf said:**
> The smbtree command returns this:
```
john@john-ubuntu:~$ smbtree
Enter john's password: 
MSHOME
    \\UBUNTU-SERVER          ubuntu-server server (Samba, Ubuntu)
        \\UBUNTU-SERVER\print$             Printer Drivers
        \\UBUNTU-SERVER\IPC$               IPC Service (ubuntu-server server (Samba, Ubuntu))
    \\DLINK-2B23C7           DNS-323
```

I assume you  commented out the Samba share mount line in the fstab file.  Is that correct?  

Notice that the \\DLINK-2B23C7 shows no Samba share.  If there is no share legitimately created then you can't mount the share via fstab.  This sounds consistent with what you have said.  (see below). > 

I'm not sure what this command is suppose to do or mean, but his is what it returns:
```
john@john-ubuntu:~$ ls -lt .gvfs
total 0
```
The **ls -lt** command lists contents of the directory your in (the current working directory.  The .**gvfs** is a hidden directory in your home directory that serves as the mount point for Nautilus mounted Samba shares.  If there were shares mounted, they would have shown up in *.gvfs*.  What is returned is consistent with the *smbtree* command which shows no samba shares to mount.> 
I tried to copy the files I already have on the Dlink back to one of my local drives and I got an error part way through the copy.  I think maybe there is a physical issue with the hard drive in the Dlink.  I had two drives in a RAID 0 configuration before and removed one and reformatted, that's when this issue began.
So now after all of this back and forth we get to the root of the problem.  The drive has been reformatted and **no new share has been created**.  I would say you need to recreate the share as well as formatting the disk.

Below is a chart of the 3 states of a (your) system```

Physical = The bare hardware
Real =  The Operating system running on the hardware
Virtual = A virtual machine running in your system (i.e. Java or a VM )
```
I'm pretty sure the hard drive is physically okay, but I would reformat the disk anyway as you rebuild this system.  I think the DLINK OS is running okay.  

Delete the share, format the drive and create a new share using the DLink menu.

---

### Post by wa1d0rf on 2012-05-14
> **bab1 said:**
> I'm pretty sure the hard drive is physically okay, but I would reformat the disk anyway as you rebuild this system.  I think the DLINK OS is running okay.  

Delete the share, format the drive and create a new share using the DLink menu.

I reset the Dlink to factory settings.  I made sure the workgroup matched my ubuntu machine (just for fun)  and reformatted the one and only drive I have in the enclosure to EXT3.  I left the default network share settings alone (RW access for all users, no password required).  

Next I tried to create the "TVshows" folder from Nautilus and it worked fine.  I then tried to create an empty document file and that worked fine too!  So I then tried to copy a folder full of TV show episodes and it was also successful.

It seems to work as it should now, but I'm worried that it will again degrade and deny me access again.  I'm not fully trusting that the physical drive is good.  There is only one drive now because the other one (an exact match) also degraded killing my RAID 0 setup.  Luckily, I can get these TV shows back again if I really want them.  I thought that this RAID 0 setup would allow me to insert a new (matched) drive and it would rebuild, but it didn't.  Therefore, I don't trust vital information storage to that drive, instead I make copies and store them on different drives on multiple computers.

---

### Post by bab1 on 2012-05-15
> **wa1d0rf said:**
> I reset the Dlink to factory settings.  I made sure the workgroup matched my ubuntu machine (just for fun)  and reformatted the one and only drive I have in the enclosure to EXT3.  I left the default network share settings alone (RW access for all users, no password required).  

Next I tried to create the "TVshows" folder from Nautilus and it worked fine.  I then tried to create an empty document file and that worked fine too!  So I then tried to copy a folder full of TV show episodes and it was also successful.

It seems to work as it should now, but I'm worried that it will again degrade and deny me access again.  I'm not fully trusting that the physical drive is good.  There is only one drive now because the other one (an exact match) also degraded killing my RAID 0 setup.  Luckily, I can get these TV shows back again if I really want them.  I thought that this RAID 0 setup would allow me to insert a new (matched) drive and it would rebuild, but it didn't.  Therefore, I don't trust vital information storage to that drive, instead I make copies and store them on different drives on multiple computers.

Well well now...  You *_should_* be leery of the remaining drive.  When drives start to fail Ubuntu will mount the partition as **read only**.  Sound familiar?  The disk(s) should be checked with SMART tools for your disks.   

Are you saying this was to be the only place this date was supposed to exist?  You should always have a separate backup destination.  Data is data.  Backups are something else. 

I have a single 1TB disk set that I mount and use as the backup destination for my data.  This disk is spun down when not being used.  It has nothing to do with online data use.

Coincidently I just had one of my backup drives fail on me.  I noticed it when it would only mount read only.  I quick look at the drive and I decided to replace that drive.  Total time with data off line zero.  I replaced the disk and rebuilt the file system and the new backup drive was operational in less than a hour.

Read up on RAID so you understand al of the options.  I'm not a believer in RAID mirrors.  For the very reason you experienced (they don't work for what you want to do). RAID 5 et all are are mostly at the practical limits for SOHO (small network) installations.  Imagine a 3 X 3TB RAID5 installation.  The rebuild time is days and the chance of data corruption is always just around the corner.

A couple of suggestions going forward.  Always explain you situation fully (bad disks/history of set up).  This could have saved you days of playing around.  In the end the badness is going to come out anyway.  :-(

Create a proper backup protocol.  Use and external disk that can be mounted only when needed for backups.  Treat it like tape if you wish but it should **not** be always mounted and available.  It is meant to  duplicate data and stored off line.

---

