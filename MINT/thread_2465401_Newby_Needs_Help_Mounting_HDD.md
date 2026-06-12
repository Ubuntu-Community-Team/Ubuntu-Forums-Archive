---
title: "Newby Needs Help Mounting HDD"
date: 2021-07-31
forum: MINT
---

### Post by lenny54linux on 2021-07-31
New to Linux. Running Mint. Been trying to fix this issues for a many hours;
Laptop has two drives,

~ 500gb SSD - has linux OS
~ 1TB HDD -  formatted ex4

Initially the 1TB drive mounted, had it on the desktop, it will not mount now, it's listed in "Disks"
It's location is /dev/sda2

It's in timelapse, can access it there, not helpful. Many attempts with terminal return "Command not found"
I find code and command lines challenging, i really could use some help, I want this 1TB drive to be mounted in the root and auto mount at boot up.

Thank you.

---

### Post by Bashing-om on 2021-07-31
lenny54linux; Hello - Welcome to the Forum :D

> 
mounted in the root and auto mount at boot up.


That is the function of the /etc/fstab file. One edits this file for a desired result.

Please see:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen -Understanding fstab
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336) <-Manualy edit fstab - why(Morbius1)

If additional aid is needed, please provide us with your /etc/fstab file - between code tags
```

cat /etc/fstab

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


sda2 is a partition on the first device sda - I would expect the data drive to be identified as sdb -
Show us what the system sees:
```

sudo parted -l
sudo blkid

```

[INDENT][INDENT]help is what we do
[/INDENT][/INDENT]

---

### Post by lenny54linux on 2021-07-31
Thank you, I could not get anywhere with fstab, here's the sys info:

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vgmint-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/nvme0n1p2 during installation
UUID=0441cf0d-4a5d-45af-98df-9bc2639081ec /boot           ext4    defaults        0       2
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=A6FE-11DA  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vgmint-swap_1 none            swap    sw              0       0





Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start  End     Size    File system  Name                  Flags
 2      135MB  1000GB  1000GB  ext4         Basic data partition




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vgmint-swap_1: 1028MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  1028MB  1028MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vgmint-root: 510GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system  Flags
 1      0.00B  510GB  510GB  ext4




Error: /dev/mapper/nvme0n1p3_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/nvme0n1p3_crypt: 511GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Model: ADATA SX8200PNP (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1305MB  768MB  ext4
 3      1305MB  512GB   511GB

---

### Post by Bashing-om on 2021-07-31
lenny54linux - yukkie on me

I know nothing about the encryption level
> 
Error: /dev/mapper/nvme0n1p3_crypt


Will require those who have the knowledge to further aid and assist.

- A know-it-all I am not-

---

### Post by Dennis N on 2021-07-31
You need to get the UUID of the partition you want to mount on the HDD, and create a folder where you want it mounted (mount point) at startup. Once you have that, the fstab entry can be constructed:

If you mount at **/mnt/DataDisk**, substitute the actual partition's UUID for the one shown, add this line to /etc/fstab and it should work.

```
 UUID=f686a8ce-3094-4b46-b497-b8ee883ba951 /mnt/DataDisk ext4 defaults 0 2
```
 
 You must also change the owner of the mount point to your user name in order to use the disk.
 
 ```
sudo chown -R you:you /mnt/DataDisk
 
```
 replace 'you' by your user name.

---

### Post by lenny54linux on 2021-07-31
Thank you, 

when I run: [COLOR=#000000][FONT=&quot] UUID=f686a8ce-3094-4b46-b497-b8ee883ba951 /mnt/DataDisk ext4 defaults 0 2

I get this: [/FONT][/COLOR]bash: /mnt/DataDisk: No such file or directory


For this one: [COLOR=#000000][FONT=&quot]sudo chown -R you:you /mnt/DataDisk

I can't get it to work, not sure on the user name, I installed from USB as OEM, but I tried:

[/FONT][/COLOR]oem@M4:~$  UUID=f686a8ce-3094-4b46-b497-b8ee883ba951 /mnt/DataDisk ext4 defaults 0 2
bash: /mnt/DataDisk: No such file or directory
oem@M4:~$ sudo chown -R M4:M4 you /mnt/DataDisk
[sudo] password for oem:            
chown: invalid user: &#8216;M4:M4&#8217;
oem@M4:~$ sudo chown -R OEM@M4:OEM@M4 /mnt/DataDisk
chown: invalid user: &#8216;OEM@M4:OEM@M4oem@M4:~$ sudo chown -R M4:M4 /mnt/DataDisk
chown: invalid user: &#8216;M4:M4&#8217;

---

### Post by lenny54linux on 2021-07-31
Devise: /dev/sda2

UUID: 15e2d829-2450-4d9a-a4a4-2193dbe97a83

Partition file: Linux Filesystem

Contents: Ext4 (version 1.0) &#8212; Mounted at /run/timeshift/backup

Thanks.

---

### Post by lenny54linux on 2021-07-31
I did create a folder: /media/FILES

UUID=15e2d829-2450-4d9a-a4a4-2193dbe97a83 /mnt/FILES ext4 defaults 0 2bash: /mnt/FILES: No such file or directory

---

### Post by wildmanne39 on 2021-07-31
Moved to mint sub-forum.

---

### Post by Bashing-om on 2021-07-31
lenny54linux; Well -

1) Got to have a valid directory for the mountpoint:
what shows:
```

ls -al /mnt/
#or added
ls -al /media/

```
where we are looking to see if "/mnt/DataDisk" does exist - else one will need to create it.

2) ownership
Who are "you" on this system:
```

who
id

```
so we can assign the correct owner to the file system in question. Be aware that this user must have the ability to elevate privileges to administration of the system (sudo rights).
 
for example for ME on MY system -would be
```

sudo chown sysop:sysop /mnt/DataDisk/

```
where I am "sysop" on my system.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by lenny54linux on 2021-07-31
Thank you for your help:

oem@M4:~$ ls -al /mnt/
total 8
drwxr-xr-x  2 root root 4096 Jul  3 08:24 .
drwxr-xr-x 19 root root 4096 Jul 28 14:01 ..
oem@M4:~$ #or added
oem@M4:~$ ls -al /media/
total 16
drwxr-xr-x   4 root root 4096 Jul 31 19:15 .
drwxr-xr-x  19 root root 4096 Jul 28 14:01 ..
drwxr-xr-x   2 root root 4096 Jul 31 19:15 FILES
drwxr-x---+  2 root root 4096 Jul 31 17:54 oem


oem@M4:~$ who
oem      tty7         2021-07-31 17:54 (:0)
oem@M4:~$ id
uid=29999(oem) gid=29999(oem) groups=29999(oem),4(adm),27(sudo),30(dip),46(plugdev),114(lpadmin),134(sambashare)

sudo chown OEM:OEM /mnt/DataDisk/
[sudo] password for oem:            
chown: invalid user: &#8216;OEM:OEM&#8217;

---

### Post by Dennis N on 2021-07-31
```
sudo chown OEM:OEM /mnt/DataDisk/
[sudo] password for oem:
chown: invalid user: ‘OEM:OEM’ 
```
What's wrong here is that Linux is case sensitive. You can't switch capital with lower case letters. So the command should be:
```
sudo chown -R oem:oem /mnt/DataDisk
```
I added the -R here just in case you rebooted before doing this command. It's ok to add the -R in any case.
I hope it all works now. 

(The user number 29999 shown by id command for the current user is a bit strange to me. Usually, this is 1000 for the current human user and lower numbers for system uses.)

---

### Post by TheFu on 2021-08-01
```
UUID=f686a8ce-3094-4b46-b497-b8ee883ba951 /mnt/DataDisk ext4 defaults 0 2
```
isn't a command. It is a line to add to the fstab file. Use the **sudoedit** command to modify system config files like the fstab.  I didn't check that the UUID was correct.

If you need a temporary mount and don't want to modify the fstab, then you could use this command: 
```
sudo mount  UUID=f686a8ce-3094-4b46-b497-b8ee883ba951 /mnt/DataDisk
```
/mnt is perfect for temporary mount locations according to the standards. For permanent mounts, it isn't a good place - again - according to the standards.  But it is your system and you can mount storage anywhere you like.

The mount assumes that a file system has been laid down on the partition/UUID and that it can be figured out by the mount command.

Also, if there are 5 steps in a process, you should stop when the first step fails. DO NOT CONTINUE!!!  That's a good way to trash a system.

There is some basic knowledge lacking.  We all started out that way. Take a look at : [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) which builds knowledge and skills in the most efficient order, so you waste the least amount of time overall.  Unix/Linux administration isn't like Windows.  Skills build on prior skills.  It is best NOT to skip over the early skills or mistakes will happen later, sometimes those mistakes will be tragic.

OEM@M4:OEM@M4  is supposed to be the USER:GROUP.
OEM is the user @M4 is the hostname, so that shouldn't be used in any chown/chmod command, ever.  Also, both of those (hostname and username) really should be lowercase to avoid future problems.  In theory, it shouldn't matter, but sometimes it does.

BTW, your OS drive is using something called LVM.  This is a nice volume manager, but it doesn't work the same way that direct partition flie systems work.  LVM is much more flexible, at the cost of some complexity.  If you ever need help with LVM stuff, be certain you mention that so someone with the right knowledge can answer.  

LVM + encryption is another skillset. Mention both, if those are being used.  Also, make 100% certain you have excellent backups. Should anything go wrong, restoring from backups is usually the only answer for encrypted storage.  You've been warned.  BTW, I use LVM+LUKS encrypted storage on my laptops. It's a security consideration for me.

---

### Post by lenny54linux on 2021-08-01
oem@M4:~$ sudo chown -R oem:oem /mnt/DataDisk
[sudo] password for oem:            
chown: cannot access '/mnt/DataDisk': No such file or directory
oem@M4:~$ 


 No such file or directory, command line not valid, see this too many times.
Thanks for your input.

Like i mentioned in the first post, I want the drive to be mounted in the proper place, load on boot up. Temp mount does me no good.
When i did the initial install somehow it was a OEM install meant to be handed over to a end user, i had no idea.
I tried adding a new user, but then rebooting lost all my settings, so i gave that up.

Can i get a step by step for editing the fstap to make this system correct?

---

### Post by lenny54linux on 2021-08-01
The temp mount command did not work, i tried your UUID and the actual one:

em@M4:~$ sudo mount  UUID=f686a8ce-3094-4b46-b497-b8ee883ba951 /mnt/DataDisk
mount: /mnt/DataDisk: can't find UUID=f686a8ce-3094-4b46-b497-b8ee883ba951.
oem@M4:~$ sudo mount  UUID=15e2d829-2450-4d9a-a4a4-2193dbe97a83 /mnt/DataDisk
mount: /mnt/DataDisk: mount point does not exist.

Terminal and code is not my thing, obviously, but i've been pasting code for a day and half and it gets me nowhere...
so frustrating

Does the terminal need to be in "root" for any of this to work?

---

### Post by TheFu on 2021-08-01
emmy54linux - I wrote this for a reason:
> There is some basic knowledge lacking. We all started out that way. Take a look at : [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) which builds knowledge and skills in the most efficient order, so you waste the least amount of time overall. 

There problems you are having are due to a lack of basic knowledge. I provided a link to gain that knowledge.  Pasting code will never work without the understanding, since your system is a little different, you'll need to understand what needs to be modified for it.

This error is a little obtuse, if you've never seen it before:
>  mount: /mnt/DataDisk: mount point does not exist.
The fix is to create the mount point.  A mount point is just an empty directory.  Then try the mount command using the correct UUID.  That will get it mounted, then use a chown command already provided to give your userid ownership of the newly mounted storage. Bob's your uncle.

In ubuntu, you never need to be in "root" ... whatever that means .... to do anything.  You only need basic Unix/Linux knowledge.  Heck, much of the knowledge applies to MS-Windows too. For example, the idea of relative and absolute directories is the same on Windows, Unix, Linux, OSX, Android, and every other popular OS in the world today.  But somehow people using Windows never gain that skill.  Windows programmers know it.

You're probably getting even more frustrated now.  Why can't someone just tell you what to type?  It is because there are tiny little issues that will happen because we are human and those tiny little issues take us 2 seconds to see and fix.   Because we've gained that basic knowledge ourselves.

I have to ask, what's the difference between the _em_ and _oem_ userids above?  Linux is multi-user from the ground up, so the userid used for every command runs in a slightly different way with a slightly different result.

The more you learn, the less frustrating it will all be.  You should see how frustrated I get on Windows and OSX computers.  Back when I owned a Mac, I wanted to throw it against the wall many times, it was that frustrating to me. Ended up giving it away to a coworker after just a few weeks.

---

### Post by lenny54linux on 2021-08-01
I'm working my way thru the PDF, it is helpful, thank you.
Let me ask you, going to Accessories~ Disks, I selected the gear icon and chose "Edit mount options"

It says for mount point: /mnt/15e2d829-2450-4d9a-a4a4-2193dbe97a83

would changing this to:

/boot/15e2d829-2450-4d9a-a4a4-2193dbe97a83

work?

---

### Post by TheFu on 2021-08-01
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) has some tips about mounting storage along with "why" and "what" and "where".  It pushes the "LABEL" method, since that skips all the UUID junk, which can be confusing.  UUIDs are just meant to be unique identifiers. Nothing more. There's nothing special about them.  A UUID can be generated for almost anything.  Computers like unique, but random alphanumeric strings aren't exactly human friendly.

I'd written a few other things, but the forum software validation is still broken. It has been since the upgrade a few weeks ago. Sorry.

Don't mount random data under /boot/, ok?  Bad idea, even if it is possible.  There are standards for where storage belongs.  "Linux File System Hierarchy Standards" - google that. There is a table and that contains all you need to know.

---

### Post by lenny54linux on 2021-08-01
Thank you.
The "Media" dir seems to be for "removable" media,
I've been looking at so much shell code my eyes are going blurry. How do I move this drive to a mount point where it shows up all the time as a permanent drive?

Thanks.

---

### Post by lenny54linux on 2021-08-01
I think I got it now:


make dir:
sudo mkdir /mnt/files


in root do : touch /etc/fstab
And then in Disk utility change mount point to add and then reboot and now it start mounting &#8230;

---

### Post by Bashing-om on 2021-08-01
lenny54linux; Hey hey :D

Progress is being made :D

We are all at some point on the learning curve - none knows all there is to know.
Now I will expose some of my ignorance.
As you have executed:
> 
in root do : touch /etc/fstab

I am unsure what that results in, as "touch" creates a new file - did that command overwrite the /etc/fstab file that "was" ?
The tool here to modify a file is a text editor - of which there are many many. Which one depends on your desktop environment (nano is universal but maybe above your skills present;y to employ). You can edit stuff from gedit, mousepad - for the GUI - or whatever text editor you use and paste it into the file with "sudo" privileges.

I think next we need to see what is current for the /etc/fstab file.
show us
```

cat /etc/fstab 

```

[INDENT]this ain't nothing but a thing
[/INDENT]

---

### Post by TheFu on 2021-08-01
Manpage says: 
 touch - change file timestamps

To "touch" a file tries to update the mtime for that file to the current time.  Directories are just files too, BTW.  For external "watching" programs that look for updates to a file, this could launch some action.  **inotify** works in this way - that's off topic, but slightly interesting.

Since systemd took over the fstab,  there are 2 ways to have updates to the fstab noticed by the OS.
* **sudo mount -a**  # forces a re-read of the the file and mounts everything it would just like reboot.
* **sudo systemctl daemon-reload**   # not exactly certain what the really does, but I think it relooks at all the boot system files for changes and recreates any systemd "unit" files. Unit files are how different parts of systemd are configured.  Every mount line in the /etc/fstab is turned into a mount unit file, for example.

I was fairly certain that the link in post #18 above had step-by-step instructions for mounting.

---

