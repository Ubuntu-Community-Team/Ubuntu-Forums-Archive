---
title: "unable to copy paste videos from parttion to partition"
date: 2011-03-17
forum: Multimedia Software
---

### Post by zissshh on 2011-03-17
hi,,all,,,FIRst,,,A BIG THANK u,,,i have been a user of ubuntu 10.4 for the past year them the partiton crashed and then i recovered and got a new machine then got ubuntu 10.10,,,
Iam VERY HAPPY USING UBUNTU,,,AND BIG THANK U TO ALL WHO ARE CONNECTED

  NOW THE PROBLEM
         i have a copy paste problem of my video files from downloads folder to the other partiton and the error says INPUT/OUTPUT error,,,,
         now after googling an awful lot as per my searching skills,,,i havent received any any answer that solved my problem,,,i am helpless pls help me solve this :(

---

### Post by Elaztic on 2011-03-17
Hi,

First of all let's see if there are any of the trivial errors.

In the terminal check admission/rights of the two folders by:

ls -al <name of folder>

Your username or group should have write access to both folders.

Try to copy one of the files through the terminal:

cp <location/name of source file> <destination location>

You can use the tab-key to autocomplete.

Post your findings ;)

---

### Post by zissshh on 2011-03-22
sudhir@sudhir-desktop:~$ ls-al <donnie darko>
bash: syntax error near unexpected token `newline'
sudhir@sudhir-desktop:~$ ls-al donnie darko
No command 'ls-al' found, did you mean:
 Command 'lshal' from package 'hal' (main)
ls-al: command not found
sudhir@sudhir-desktop:~$

---

### Post by zissshh on 2011-03-22
while copying
this is the error
Error creating directory: Input/output error

---

### Post by oldfred on 2011-03-22
Two things.

The command has a space. Copy and paste.

ls -al

If your folder is donnie darko it has a space which Linux does not like.

cd 'donnie darko'
ls -al 'donnie darko'

Much better to use an underscore:
donnie_darko

or leave off the space
donniedarko

Or use CamelCase
DonnieDarko

But Linux is case sensitive where windows is not so donniedarko is not the same as DonnieDarko in Linux but would be the same in windows.

---

### Post by zissshh on 2011-03-23
sudhir@sudhir-desktop:~$ ls -al 'donniedarko'
ls: cannot access donniedarko: No such file or directory
sudhir@sudhir-desktop:~$

---

### Post by oldfred on 2011-03-23
sudhir@sudhir-desktop

That says your are in your desktop folder. Where is the folder you want. you have to do a cd to the folder that you want to list.

 cd /home/fred/shared/Photos/All2011/Winter2011

When I have folders like the above that I want to cd to in the command line, I cheat.  I cannot type a line that long without some typo.  I use Nautilus to drill down to the folder I want , then control l  (ctrl L) changes the location to a copyable format and paste it into the command line.

---

### Post by vanadium on 2011-03-23
Could it be that you are trying to copy a big file to a fat formatted disk?

Show us some properties of the disk by posting the output of

```

mount
sudo blkid

```

---

### Post by zissshh on 2011-03-24
sudhir@sudhir-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sudhir/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sudhir)
/dev/sda6 on /media/songs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0 on /media/disk type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
sudhir@sudhir-desktop:~$ sudo blkid
[sudo] password for sudhir: 
/dev/sda1: UUID="f846ae40-6468-49c9-b669-cb5a909e76bc" TYPE="ext3" 
/dev/sda5: LABEL="DATA" UUID="8C5C05E05C05C5C4" TYPE="ntfs" 
/dev/sda6: LABEL="songs" UUID="62FC0D8BFC0D5AA5" TYPE="ntfs" 
/dev/sda7: LABEL="VIDEO" UUID="121C1ED81C1EB6A7" TYPE="ntfs" 
/dev/sda8: UUID="d29ef4c8-972c-4b2b-8d60-e86758461e7e" TYPE="swap" 
sudhir@sudhir-desktop:~$

---

### Post by zissshh on 2011-03-24
sudhir@sudhir-desktop:~$ cd /home/sudhir/Downloads
sudhir@sudhir-desktop:~/Downloads$ ls -al 'donniedarko'
ls: cannot access donniedarko: No such file or directory
sudhir@sudhir-desktop:~/Downloads$ ls -al DonnieDarko
ls: cannot access DonnieDarko: No such file or directory
sudhir@sudhir-desktop:~/Downloads$ ls -al donnie_darko
ls: cannot access donnie_darko: No such file or directory
sudhir@sudhir-desktop:~/Downloads$ ls -aldonnie_darko
ls: invalid option -- 'e'
Try `ls --help' for more information.
sudhir@sudhir-desktop:~/Downloads$ ls -al donnie_darko
ls: cannot access donnie_darko: No such file or directory
sudhir@sudhir-desktop:~/Downloads$

---

### Post by vanadium on 2011-03-24
I see all your drives are NTFS formatted. Therefore, the file size cannot be the issue.

Your /dev/sda7: LABEL="VIDEO" is NOT mounted. So probably you are not trying to copy there.

You must be trying to copy the files to either /dev/sda5: LABEL="DATA" or /dev/sda6: LABEL="songs" (see how I am guessing?).

First, check the free space remaining on the drive where you want to copy.

Secondly, hook the partitions /dev/sda5, /dev/sda6 and /dev/sda7 on a Windows system and have the file systems checked using the Windows tools.

If all this has been checked, and the problem remains, we can try to search further.

---

### Post by oldfred on 2011-03-24
My suggestion of alternative names for donnie darko was how you would name the folder. You have to use the actual name it is. what it that.

If the folder is in downloads 

cd Downloads
ls

if list is long highlight the list and click on the # (code tags in message edit panel above on right side) to put it into code tags.

---

### Post by zissshh on 2011-03-25
sudhir@sudhir-desktop:~/Downloads$ ls -al donnie_darko
total 718072
drwxr-xr-x  2 sudhir sudhir      4096 2011-03-08 05:13 .
drwxr-xr-x 30 sudhir sudhir     16384 2011-03-25 13:42 ..
-rw-r--r--  1 sudhir sudhir 734552064 2011-03-08 05:13 Donnie Darko[2001]DvDrip[Eng]-Bugz.avi
-rw-r--r--  1 sudhir sudhir       842 2011-03-07 20:59 Donnie Darko[2001]DvDrip[Eng]-Bugz.txt
-rw-r--r--  1 sudhir sudhir        47 2011-03-07 20:59 Torrent downloaded from Demonoid.com.txt

---

### Post by oldfred on 2011-03-25
You do not have permissions & have to use quotes because of the space in the name.

sudo chmod -R 777 /Downloads

Then you can copy & paste or using command line

cp -a old_directory new_directory

cp -a ~/Downloads/'Donnie Darko[2001]DvDrip[Eng]-Bugz.avi' /somenewplace

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by vanadium on 2011-03-25
This is not correct. The permissions of the source files do not determine whether you have permissions to write to a destination.

DO NOT USE THE chmod -R command UNLESS YOU KNOW WHAT YOU ARE DOING.

It could break your system.

The symptoms do not indicate a permission problem to me. 

It becomes time that zissshh specifies WHERE he wants to copy. Probably, it is a good idea to check the free space at the destination. None of the used file systems are a problem for a 700 MB file. As i already mentioned, one partition, VIDEO, is currently not mounted. So it is impossible at the moment to write to the VIDEO partition.

However, again, the fundamental issue is that we have not yet been told WHERE the file is being copied. So we do not know what destination to investigate.

---

### Post by oldfred on 2011-03-25
vanadium is correct if you run the chmod command on folders other than /download.

I did something similar once at root and ended up having to reinstall.

---

### Post by zissshh on 2011-03-27
sudhir@sudhir-desktop:~/Downloads$ sudo chmod -R 777 /Downloads
chmod: cannot access `/Downloads': No such file or directory
sudhir@sudhir-desktop:~/Downloads$

---

### Post by oldfred on 2011-03-27
You are in downloads so you cannot run it.

To move up one level, note space
```
cd ..
```Where is it you are trying to copy to. You have to have permissions there.

Besure not to go up more than one level. Or this will take you to home.

```
cd ~
```Then when you type this you should see your folders with your permissions note small letter L:
```

ls -l
```

---

### Post by vanadium on 2011-03-27
Post the output of
```

df -h

```
to show the available space on your partitions. Try to tell us what partition is the one with which you have the issue.

---

### Post by zissshh on 2011-03-28
sudhir@sudhir-desktop:~$ sudo chmod -R 777 /Downloads
[sudo] password for sudhir: 
chmod: cannot access `/Downloads': No such file or directory

---

### Post by zissshh on 2011-03-28
sudhir@sudhir-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              74G   37G   34G  52% /
none                  996M  248K  996M   1% /dev
none                 1002M  200K 1002M   1% /dev/shm
none                 1002M  116K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
/dev/sda6              79G   46G   33G  59% /media/songs
/dev/sda5              79G   29G   51G  36% /media/DATA
/dev/sda7              64G   56G  8.0G  88% /media/VIDEO

---

### Post by vanadium on 2011-03-28
Disk space is not the issue. Probably permissions are not the issue, because the error message would be specific. Your problem could indicate that your drive is breaking down.

You could try copying from the command line
```

cp "~/Downloads/Donnie Darko[2001]DvDrip[Eng]-Bugz.avi" /media/VIDEO

```
but I fear the same error message will pop up.

I am not sure how you could scan the drive to have bad blocks identified. You could take a look with Disk utility (System - Administration - Disk Utility). This among other things displays the disks "Smart status", which should be green, "Disk is healthy". Clicking "Smart data" allows to run a self test, i.e. scan the surface for errors.

While this could prolong your use of the drive a little, you should probably make sure the backup of your data is up to date, and expect that the drive will fail fully any time soon.

---

### Post by zissshh on 2011-03-28
sudhir@sudhir-desktop:~/Downloads$ cp "~/Downloads/Donnie Darko[2001]DvDrip[Eng]-Bugz.avi" /media/VIDEO
cp: cannot stat `~/Downloads/Donnie Darko[2001]DvDrip[Eng]-Bugz.avi': No such file or directory

the disk Status is healty and green: Running Self Test

Self Test Results:ok

---

### Post by vanadium on 2011-03-28
It then appears that the file that you listed here [http://ubuntuforums.org/showpost.php?p=10598572&postcount=13](http://ubuntuforums.org/showpost.php?p=10598572&postcount=13)
is gone.

Oops, I see: it is in the donnie_darko directory.

cp "~/Downloads/donnie_darko/Donnie Darko[2001]DvDrip[Eng]-Bugz.avi" /media/VIDEO

should work.

---

### Post by oldfred on 2011-03-28
I think the quotes should only be around the title.

cp ~/Downloads/donnie_darko/"Donnie Darko[2001]DvDrip[Eng]-Bugz.avi" /media/VIDEO

---

### Post by vanadium on 2011-03-28
Yes, indeed! The ~ does not get expanded when inside the quotes.

---

### Post by zissshh on 2011-03-29
sudhir@sudhir-desktop:~/Downloads$ cp ~/Downloads/donnie_darko/"Donnie Darko[2001]DvDrip[Eng]-Bugz.avi" /media/VIDEO
cp: cannot create regular file `/media/VIDEO': Permission denied

---

### Post by zissshh on 2011-03-29
I have also unable to delete any file that had been downloaded in a particular time when the problem arised, from  " songs " parttion especially
 Need some to the core solving solution

---

### Post by zissshh on 2011-03-29
I have also unable to delete any file that had been downloaded in a particular time when the problem arised, from  " songs " parttion especially
 Need some to the core solving solution
Also i they are stuck in trash,,which even Bleachbit is unable to remove

---

### Post by vanadium on 2011-03-29
> **zissshh said:**
> sudhir@sudhir-desktop:~/Downloads$ cp ~/Downloads/donnie_darko/"Donnie Darko[2001]DvDrip[Eng]-Bugz.avi" /media/VIDEO
cp: cannot create regular file `/media/VIDEO': Permission denied

This now appears as if /media/VIDEO is not available, this means, the partition VIDEO is not mounted. Therefore, the system tries to create a regular file named VIDEO under /media, but as a normal user, you do not have permission.

Lat us try to see why it does not mount

```

cd
mkdir video
sudo mount LABEL="VIDEO" video
mount

```

---

### Post by zissshh on 2011-03-30
The Video Partition was mounted when i tried copying,,,,

  Now also have another problem while copying anything to Songs partition
  I get this Error

/media/songs/StudentsInfoGraphics/144.jpg could not be saved, because an unknown error occurred.

Try saving to a different location.

After Trying to save the same file again to the same location,it says if i want to replace the already existing file,,and it get replaced when i replace it,,,

Can this be also related to this problem.
CAn there be any solution

---

### Post by vanadium on 2011-03-30
The error message you reported suggests the partition was not mounted.

---

### Post by zissshh on 2011-03-31
There was no chance that the partition was unmounted,,,

---

### Post by zissshh on 2011-03-31
Is there a shoutbox on Forum,,so that i can appeal to every member for an answer

---

### Post by vanadium on 2011-03-31
Provide more and detailed information. Chances are more people will look at it and see what the problem is.

I say it was not mounted. You say it was mounted. I can only guess from what you tell, you can know.

To proove that the partition is mounted, see whether it is listed in the output of "mount". You once posted the output of "mount", and at that time, it was *not* mounted, wasn't it? So why would I assume it is mounted if an error message clearly suggests me that the OS was trying to create a file /media/VIDEO. The OS would not try that if there were already a directory /media/VIDEO. At the time you tried my command, the directory VIDEO was not there, hence the drive was not mounted.

This leads me to return to my earlier answer of 30 march 04:22 PM, which you did not further investigate.

---

### Post by zissshh on 2011-04-02
My issue is with Song Partition ,,,also that i am unable to rename partitions,,,
  But iam unable to delete anything from Songs Partiton,,,,OR cOPY TO IT
The donnie darko got copied to Video but unable to copy to songs partition,,,,,,
When i try to delete anything from the songs partition: 
Unable to trash : Input -Output eRROR

---

### Post by zissshh on 2011-04-02
i AM ABLE TO COPY ONLY WHEN I PASTE IT TWICE,WHEN I COPY IT FIRST TIME THE SYAYTEM RESPONDS SAYING THE FILE COULD NOT BE COPIED INPUT-OUTPUT EEROR,NOW AGAIN I COPY PASTE THE SAME FILE TO THE SAME LOCATION,IT SAYS (REPLACE THE FILE WITH),SO I SAY OK AND IT IS DONE,,BUT IAM UNABLE TO DELETE SOME FILE ON THE SONGS PARTITON,,,

---

### Post by oldfred on 2011-04-02
Please review these links.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

From a liveCD use Disk Utility or gparted and rename your partitions. Remove all spaces to avoid that issue.

See attached from DiskUtility. You click on drive, then click on partition and choose edit.

---

### Post by zissshh on 2011-04-05
There is no problem mounting the partition ,,but there is problem in copying files giving input-output error

---

### Post by vanadium on 2011-04-05
The output here [http://ubuntuforums.org/showpost.php?p=10595094&postcount=9](http://ubuntuforums.org/showpost.php?p=10595094&postcount=9) showed your VIDEO partition was not mounted. The output here [http://ubuntuforums.org/showpost.php?p=10614322&postcount=27](http://ubuntuforums.org/showpost.php?p=10614322&postcount=27) suggests the cp command is trying to create a file /media/VIDEO. this means that the directory VIDEO did not exist at that time. This indicated that either your VIDEO partition was not mounted, or it was mounted on another location.

This is the evidence I have got. Obviously, I can only base my opinion based on the information you provide. You, in contrast, are in front of your computer.

Try the same cp command again, but this time, do also include the output of
```

sudo blkid
mount
ls -l /media
ls /media/VIDEO

```
in your reply.

Or just post the output of these commands. They may indeed well prove that your VIDO partition is not mounted or mounted elsewhere.

Else, the search for a cause of the problem still will take very, very long ...

---

### Post by zissshh on 2011-04-06
sudhir@sudhir-desktop:~$ sudo blkid
[sudo] password for sudhir: 
/dev/sda1: UUID="f846ae40-6468-49c9-b669-cb5a909e76bc" TYPE="ext3" 
/dev/sda5: LABEL="DATA" UUID="8C5C05E05C05C5C4" TYPE="ntfs" 
/dev/sda6: LABEL="songs" UUID="62FC0D8BFC0D5AA5" TYPE="ntfs" 
/dev/sda7: LABEL="VIDEO" UUID="121C1ED81C1EB6A7" TYPE="ntfs" 
/dev/sda8: UUID="d29ef4c8-972c-4b2b-8d60-e86758461e7e" TYPE="swap" 
/dev/sdb1: LABEL="New Volume" UUID="1F9B-B1F6" TYPE="vfat" 
sudhir@sudhir-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sudhir/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sudhir)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/New Volume type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda6 on /media/songs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7 on /media/VIDEO type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
sudhir@sudhir-desktop:~$ ls -l /media
total 28
drwxr-x--- 2 root   root    4096 2010-12-11 01:32 apt
drwx------ 4 sudhir sudhir  4096 2011-04-06 12:02 New Volume
drwx------ 1 sudhir sudhir  8192 2011-02-19 19:41 songs
drwx------ 1 sudhir sudhir 12288 2011-04-02 19:51 VIDEO
sudhir@sudhir-desktop:~$ ls /media/VIDEO
4413987999_f33402d6e5_o.jpg
backupNamroka
bigB
books
Donnie Darko[2001]DvDrip[Eng]-Bugz.avi
gry.jpg
Paintings
photos
recent
REsearchREpeat
schooltool
ShopDEsigns
snakeoil_supplements_956.png
sudhir
The War You Don't See - John Pilger .mp4

---

### Post by vanadium on 2011-04-06
Hooray, hooray, now indeed your VIDEO partition is correctly mounted under /media/VIDEO. It is an ntfs file system and previous output showds that there are still had some 8 GB free. There should not be a problem to copy a 700 MB video file.

However, you did not retry copying the file now. In these circumstances, if there will be any error messages, it will be a different one than the one you posted before.

---

### Post by zissshh on 2011-04-07
the problem lies with the songs partition

---

### Post by vanadium on 2011-04-07
Nice to learn that 14 days and five thread pages later :D

---

### Post by zissshh on 2011-04-07
I think Vanadium ,,You are not providing me the correct answer for the problem i have mentioned earlier:)
  I have mounted the songs partition
  now if i want to create a folder,it replies saying directory issues and input output error
 If i try to copy ,i get the reply of input output error and if i try to copy again,the file is copied when i  say ok to replace the exixting 0 byte file.
 ............ If u read properly i have already mentioned the problem over and over again.....
 I have been using ubuntu for a year and i ahve installed it myself and been clearing all the issues by discussing online and the seniors,
now after a year of communicating online i am not that bad at to put my problem across in such a bad manner......that i wont ever get an answer

---

### Post by oldfred on 2011-04-07
Did we not start with Donnie Darko not being copied to a video partition?

Now that the Video & songs partitions are both mounted and both have same permissions what is different in your not being able to copy to songs?

Copy & paste terminal commands.

Are you just using default permissions of a mount from Nautilus? If doing this a lot and the partitions are part of an internal drive it is best to add the mount to fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by zissshh on 2011-08-26
iam just using the default permissions of nautilus,,,
  is there any code result output from terminal


this problem is not limited to my donniedarko file,,that was just an example,,,the problem sometimes crops up on usb and sd card,,,

also in the SOngs Partition,i have to create a folder to paste a file or the file is not allowed to be pasted and I/O Error crops up

Now ,, i also have a problem creating a folder in the above said partition,,,i cant create a new folder,,,,if its created it cant be seen,,,

only if i restart the system that i can see it,,,

also iam unable to rename the partitons,,,

i want only two partitons,,,can it be possible

---

### Post by zissshh on 2011-09-02
Pls reply to this,,,

As I repeat My problem,,,

I have issues copying,pasting,deleting stuff from the SONGS Drive,,,

Nowadays when i delete a file or folder,,,it always shows I/O Error

And its becoming more complicated as once i click on the window showing the error,,on cancel or Skip...

the folder which contained the file shows zero items and even if i try to go back or try to check the folder,,,still it shows zero items,,,

It only shows the contents after restarting the system minus the file i was deleting,,,

i hope this does not get more complicated,,

need some clarification on my worrisome doubt

---

### Post by zissshh on 2011-09-04
Please help :)

---

