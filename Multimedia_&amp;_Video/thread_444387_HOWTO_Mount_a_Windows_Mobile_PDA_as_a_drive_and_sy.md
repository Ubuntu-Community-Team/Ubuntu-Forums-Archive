---
title: "HOWTO: Mount a Windows Mobile PDA as a drive and sync files and folders"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by eudemus on 2007-05-15
In order to do this, you ought already to have the PDA working using SynCE.
[http://synce.sourceforge.net](http://synce.sourceforge.net)
That's no trivial prerequisite - took me ages to get it working, and involved attention to udev stuff. The most helpful thread I found was this one, particularly post #14. But you need to follow the basic instructions about installing SynCE first - then when it doesn't work (!!) go to this thread!
[http://ubuntuforums.org/showthread.php?t=149183&page=2](http://ubuntuforums.org/showthread.php?t=149183&page=2)

MOUNTING YOUR PDA AS A DRIVE
Downloads and instructions are here:
[http://www.lvivier.info/SynceFS/](http://www.lvivier.info/SynceFS/)
[http://sourceforge.net/projects/syncefs/](http://sourceforge.net/projects/syncefs/)
The package that sorted it out nicely for me was syncefs_0.6_i386.deb, which was emailed to me directly by Laurent Vivier the developer - very kind chap. For some reason the earlier versions didn't work.
Then get coda going, and then mount ....

SYNCING FILES AND FOLDERS - something I do in Windows (at work - I have no choice!) very very easily using MS ActiveSync and (for the files on SD card) MightySync (great little app).

Use Unison. I just installed it via Synaptic - it's in the standard repositories.

HOpe that's some help.
Eudemus

---

### Post by eudemus on 2007-06-12
Correction: the version needed actually turns out to be syncefs_0.7_i386.deb, since under the previous version, files were written to the PDA in the wrong way, causing Unison to fail. Great work there by the syncefs guy, Laurent Viver.

This is fantastic, since now I can have my PDA (with 1GB card) as my repository of all my work files. It gets synced regularly in two places, so I have constant backups. Nice.

Eudemus

---

### Post by wersdaluv on 2007-06-23
I have SynceFS and Unison installed. What do I do now?

:KS

---

### Post by wersdaluv on 2007-06-23
When I double clicked the "synce" icon under "computer:///", it said
> Unable to mount the selected volume.

[mntent]: warning: no final newline at the end of /etc/fstab

/sbin/mount.cefs: cannot open /dev/cfs0

(you should load the module coda

---

### Post by eudemus on 2007-06-26
I'm a little lost in terms of how far you've got.
(and sorry about the delay in answering this, by the way, perhaps the problem is now resolved?)

First get SynceFS working, and make sure you've got everything ready for running SynceFS.
(It presuposes that you've got SynCE working - you can tell if you have by typing
synce-pstatus
on the command line. If you get a whole load of data back about your device, then it's working!)

As per the instructions for SynceFS, you need to have created the directory /mnt/synce, because this is where the device will be mounted.
sudo mkdir /mnt/synce
if you haven't already done that.

Second, you'll need to do the following:
sudo modprobe coda
mount /mnt/synce

If you get success with that, then you should be able to set up and use a profile in Unison, where Root 1 is the directory on the desktop and Root 2 is the directory on the PDA

Root 1: /home/eudemus/Files to go to SD Card
Root 2: /mnt/synce/SD Card/Current - SYNC TO SD CARD

All being well, this should then enable you to use Unison's graphical interface to sync the two directories together. I'm syncing about 600MB of data each time, and it's very slow the first time, but thereafter it's a bit quicker.

Let me know if you need more help. Sorry this is a bit of a splurge, but it's quite hard to tell how far you have got, where problems lie, etc.
Best
Eudemus

---

### Post by wersdaluv on 2007-06-27
> **eudemus said:**
> I'm a little lost in terms of how far you've got.
(and sorry about the delay in answering this, by the way, perhaps the problem is now resolved?)

First get SynceFS working, and make sure you've got everything ready for running SynceFS.
(It presuposes that you've got SynCE working - you can tell if you have by typing
synce-pstatus
on the command line. If you get a whole load of data back about your device, then it's working!)

As per the instructions for SynceFS, you need to have created the directory /mnt/synce, because this is where the device will be mounted.
sudo mkdir /mnt/synce
if you haven't already done that.

Second, you'll need to do the following:
sudo modprobe coda
mount /mnt/synce

If you get success with that, then you should be able to set up and use a profile in Unison, where Root 1 is the directory on the desktop and Root 2 is the directory on the PDA

Root 1: /home/eudemus/Files to go to SD Card
Root 2: /mnt/synce/SD Card/Current - SYNC TO SD CARD

All being well, this should then enable you to use Unison's graphical interface to sync the two directories together. I'm syncing about 600MB of data each time, and it's very slow the first time, but thereafter it's a bit quicker.

Let me know if you need more help. Sorry this is a bit of a splurge, but it's quite hard to tell how far you have got, where problems lie, etc.
Best
Eudemus

Thanks for the reply.

I already have synce working and am able to sync my Pocket PC with Evolution. Also, I already have the directory /mnt/synce. 

I found out that I really do not have SynceFS working. After running "synce-pstatus," what came out was, ```
The program 'synce-pstatus' is currently not installed.  You can install it by typing:
sudo apt-get install librapi2-tools
Make sure you have the 'universe' component enabled
bash: synce-pstatus: command not found

``` even if I already have librapi2-tools installed.

Also, the output of mount /mnt/synce is 
```
[mntent]: warning: no final newline at the end of /etc/fstab
/sbin/mount.cefs: /var/run/synce-1000.pid already exists
```

What could be the problem?

Thanks in advance.

:KS

---

### Post by eudemus on 2007-07-02
The error you have there is because you are trying to mount something that is already mounted.
Unmounting something mounted using SynceFS appears to be not totally simple.

sudo umount /mnt/synce
sudo rm /var/run/synce-*.pid

That should mean that you can then redo
mount /mnt/synce

(For example, if you disconnect the device (or switch it off, or whatever) while mounted, it doesn't like it, and when you reconnect it, some things work, some things don't - the desktop still considers that it has a device mounted, even if it can't actually access the device properly)

It looks as though you may not have synce itself installed properly. It's odd that you can't get synce-pstatus.

But that might not be the issue.

When you do mount /mnt/synce, do you EVER get a success message?
Or is it always the error you posted?

(Also, the error there seems to suggest there's something wrong with your fstab entry - maybe as simple as missing a carriage return at the end of the line. I've no idea if that makes a difference, but worth a try. What do you have in fstab for syncefs?)

Eudemus

---

### Post by wersdaluv on 2007-07-04
> **eudemus said:**
> The error you have there is because you are trying to mount something that is already mounted.
Unmounting something mounted using SynceFS appears to be not totally simple.

sudo umount /mnt/synce
sudo rm /var/run/synce-*.pid

That should mean that you can then redo
mount /mnt/synce

(For example, if you disconnect the device (or switch it off, or whatever) while mounted, it doesn't like it, and when you reconnect it, some things work, some things don't - the desktop still considers that it has a device mounted, even if it can't actually access the device properly)

It looks as though you may not have synce itself installed properly. It's odd that you can't get synce-pstatus.

But that might not be the issue.

When you do mount /mnt/synce, do you EVER get a success message?
Or is it always the error you posted?

(Also, the error there seems to suggest there's something wrong with your fstab entry - maybe as simple as missing a carriage return at the end of the line. I've no idea if that makes a difference, but worth a try. What do you have in fstab for syncefs?)

Eudemus
After entering,  sudo umount /mnt/sync while my Pocket PC is connected via synce
```
umount: /mnt/synce: not mounted

```

The output of sudo rm /var/run/synce-*.pid is
```
rm: cannot remove `/var/run/synce-*.pid': No such file or directory
```

Whenever I try to mount, I never got a success message.

This is what my /etc/fstab entry contains
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=379363af-3e2e-41f3-b0bb-d12b5c490bc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=7a8ef331-aaa4-4285-abf3-26aba5026db9 /home           ext3    defaults        0       2
# /dev/hda3
UUID=0e2b0cec-0387-48a8-af7c-26b6de2d7d0c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

none           /mnt/synce      cefs    rw,user,noauto,codadev=/dev/cfs0       0         0
```

---

### Post by eudemus on 2007-07-04
OK. It's not mounting (and hence you get the messages you do when trying to un-mount something that was never mounted in the first place!).

I'm tempted to think that the problem here is with SynCE.
The fact that you get no output from synce-pstatus certainly suggests this.

However, just in case that's incorrect, and SynCE is working fine after all, let me check.
You connect the device, you get SynCE working such that you can perform a Sync using SynCE (or something like Multisync using SynCE).
Then you do
sudo modprobe coda
mount /mnt/synce

If after all that, you don't get the messages you need, I'm inclined to think that either
(i) you didn't have SynCE working completely, and this is why SynceFS fails; or
(ii) there's something else wrong beyond my expertise to tackle.

I can recommend the following:
for Synce
[http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php)
for SynceFS
[http://www.lvivier.info/SynceFS/](http://www.lvivier.info/SynceFS/)
and if you hit difficulty, Laurent is very helpful and glad to investigate stuff related to SynceFS - just email him.

Probably also worth making sure you have the latest versions of Synce and SynceFS. Both should be available just via Synaptic in the Ubuntu repositories. Maybe even reinstalling them might help.

Sorry, this is probably not a huge amount of help. But I'd be interested to follow how you get on.
Best wishes, Eudemus.

---

### Post by wersdaluv on 2007-07-04
Thank you very much for your time and effort. I appreciate it.

---

### Post by eudemus on 2007-07-06
No worries. Did you get it working?
Hope so.
Eudemus

---

### Post by pepe5 on 2008-02-08
> **eudemus said:**
> In order to do this, you ought already to have the PDA working using SynCE.
[http://synce.sourceforge.net](http://synce.sourceforge.net)
That's no trivial prerequisite - took me ages to get it working, and involved attention to udev stuff. The most helpful thread I found was this one, particularly post #14. But you need to follow the basic instructions about installing SynCE first - then when it doesn't work (!!) go to this thread!
[http://ubuntuforums.org/showthread.php?t=149183&page=2](http://ubuntuforums.org/showthread.php?t=149183&page=2)

MOUNTING YOUR PDA AS A DRIVE
Downloads and instructions are here:
[http://www.lvivier.info/SynceFS/](http://www.lvivier.info/SynceFS/)
[http://sourceforge.net/projects/syncefs/](http://sourceforge.net/projects/syncefs/)
The package that sorted it out nicely for me was syncefs_0.6_i386.deb, which was emailed to me directly by Laurent Vivier the developer - very kind chap. For some reason the earlier versions didn't work.
Then get coda going, and then mount ....

SYNCING FILES AND FOLDERS - something I do in Windows (at work - I have no choice!) very very easily using MS ActiveSync and (for the files on SD card) MightySync (great little app).

Use Unison. I just installed it via Synaptic - it's in the standard repositories.

HOpe that's some help.
Eudemus

I also wanna to join followed discussion. I have problem with mounting SynceFS: on default Ubuntu server it appears like this:

[INDENT]```
$ **ls -alF /mnt/synce/**
ls: /mnt/synce/: No such device

```[/INDENT]

The only message added to kernel log after this command is this:

[INDENT]```
$ **tail -1 /var/log/messages**
Feb  8 05:37:36 ubuntu-server-vm kernel: [70645.941045] coda_upcall: Venus dead on (op,un) (3.4) flags 10

```[/INDENT]

I googled for "Venus dead" +/- and i only found [coda.wikidev.net/Quick_Client_Action]("http://coda.wikidev.net/Quick_Client_Action").. Not much related?! :-( Ok, i tried to install [coda-client]("http://www.coda.cs.cmu.edu/debian"), but after that the coda module stoped working or what:

[INDENT]```
$ **lsmod | fgrep -i coda**
coda                   36932  3 

$ **sudo mount /mnt/synce/**
/sbin/mount.cefs: Cannot open /dev/cfs0
(you should load the module coda)

~ $ **sudo rmmod coda**
ERROR: Module coda is in use

```[/INDENT]

Before few days the SynceFS worked, but after some update or what, it stopped. I dont know what to try further :-S. Maybe it is because of some incompatibility of latest kernel lib patches and SynceFS? Is still CodaV2 supported by cernel?

I have 
[LIST]
[*]UbuntuServer-7.10
[*]Coda Kernel/Venus communications, v6.0.0
[*]synce-serial   0.9.1-3.1
[*]synce-dccm     0.9.1-3
[*]and i am trying again syncefs 0.7
[/LIST]

Any working versions combination or workaround will be great. Please.. i'd like to bring my cooperation to get great Vivier's SynceFS working again. Thanks in advance. JK

---

### Post by eudemus on 2008-02-13
Hi, JK,
In terms of working combinations, I'm running Kubuntu Gutsy, vdccm, and I'm not sure what version of synce-serial, but whatever the most recent one is in the repositories. I also have syncefs 0.7.

One thing you wrote surprised me: you need to run the mount command as user not as root.

But I suppose it's worth checking the basics:
Do you definitely have SynCE working with the device?
Do you definitely have syncefs installed? (I had some difficulty doing this from the deb file - it needed to be run from the terminal, as I recall, despite *appearing* to run successfully in the GUI)

It sounds as though you don't have SynCE running successfully. In which case it's not an issue for Vivier and SynceFS.

I realise this probably isn't much use. But do post again if you're any further on and I can be of any further help.
Cheers, Eudemus

---

### Post by foxy123 on 2008-02-18
I've got MyGuide car sat nav which runs on WM5. I tied this howto and I am stuck.

I have installed all the stuff (though synce-pstatus does not work for me:

```
~$ synce-pstatus
The program 'synce-pstatus' is currently not installed.  You can install it by typing:
sudo apt-get install librapi2-tools
bash: synce-pstatus: command not found

``` 

OK, when I run sudo synce-serial-start, I've got:

```
~$sudo synce-serial-start
kill: 15: No such process


synce-serial-start is now waiting for your device to connect


```



So I assume that it's connected (I may be wrong though).

Then I mount:

```
$ sudo mount /media/synce/
[mntent]: warning: no final newline at the end of /etc/fstab
SynCE FS using "/dev/cfs0" (CODA v3)
```

But if I do find, I've got I/O error:

```
$ find /media/synce/
/media/synce/
find: /media/synce/: Input/output error

```
Any help?

---

### Post by foxy123 on 2008-03-02
I have managed to get connected to my WM5 device, but still cannot mount it. I can see all the dirs/files on it using pls command, the device appears on my desktop as mounted but alas I cannot access it with nautilus or thunar:

```
~$ pls -a /

** (process:10517): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
--D------T              1998-01-01 12:00:00  Storage Card/
--D------T              1998-01-01 12:00:00  Network/
--D------T              1998-01-01 12:00:00  Flash Disk/
AC--------          23  2007-01-01 12:00:01  Control Panel.lnk
Directory               2007-01-01 12:00:01  My Documents/
Directory               2007-01-01 12:00:01  Program Files/
Directory               2007-01-01 12:00:00  Temp/
Directory               2007-01-01 12:00:00  Windows/

```
```
$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda6 on /home type ext3 (rw)
/dev/sda3 on /media/diskd type vfat (rw,utf8,umask=007,gid=46)
/dev/hda5 on /media/ideext3 type ext3 (rw)
/dev/sda1 on /media/winsys type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
[COLOR="Red"]**none on /media/synce type cefs (rw,noexec,nosuid,nodev,noauto,user,codadev=/dev/cfs0)**[/COLOR]

```
```
~$ ls -a /media/synce
.  ..  Storage Card

```

I asked Laurent but he does not know why I cannot access files.

---

### Post by eudemus on 2008-03-03
If Laurent doesn't know, then I don't stand a chance of knowing!

So, as I'm understanding you, the device is mounted, you can browse directories and files from the command line, but not using nautilus and similar file management programs.
Right?

And you definitely mounted it as user, not as root?

It shouldn't make any difference therefore if you open nautilus as root. But still, that might be an interesting thing to try.

I'm really in the dark, I'm afraid. I'd see if you could give Laurent anything more to go on - he's normally good on this kind of thing.

Do post anything you find out in trying to resolve this, it's all much appreciated.
Eudemus

---

