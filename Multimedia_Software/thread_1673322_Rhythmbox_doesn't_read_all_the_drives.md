---
title: "Rhythmbox doesn't read all the drives"
date: 2011-01-22
forum: Multimedia Software
---

### Post by renoirbleu on 2011-01-22
hello,

I installed ubuntu while leaving windows vista aside.
I have most of music files in the drive on vista and I have a problem that the rhythmbox doesn't read files from that drive. 

Even though I tried so many times to add the songs in the drive on vista to the library of rhythm box, after I restart my computer it doesn't read these songs automatically. so I always have to import these files in rhythm box whenever I run it. 

I don't know why it happens actually. is it normal ? is there any way to make rhythm box to "memorize" or "save" these files like it does with other songs saved on ubuntu ? 

due to the limit of disk size on ubuntu, I cannot actually transfer all these files to ubuntu.

can somebody help me please ?
thank you !

---

### Post by ajgreeny on 2011-01-22
If the vista drive on which the music files are sitting is not mounted all the time, rhythmbox will not see those files.  If you don't want the vista partition permanently mounted you will have to copy all the music to your ubuntu home folder.

---

### Post by vanadium on 2011-01-22
In Ubuntu, ntfs drives are not available on startup. They are mounted "on demand" only, i.e., when you click the drive in the file manager.

Resolution: have your ntfs volume automounted on startup. This is done by editing the configuration file /etc/fstab in order to add a line for your Windows partition.

---

### Post by renoirbleu on 2011-01-22
@vanadium:
I looked around things in the system files and I found this "fstab"...

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a7e880e2-95b2-4f0f-995e-3db2f896286b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=eaa8df7a-b9e5-44ed-9141-850e55ec46b5 none            swap    sw              0       0I'm not sure if I found the right one. 
what should I do next ? how to have my ntfs volume amounted on startup there ? (I really know nothing about computer stuffs... :/)

---

### Post by vanadium on 2011-01-23
If you post the output of "sudo blkid" here, then I can provide you the line you need to add to /etc/fstab in order to also have your ntfs drive mounted on startup.

Currently, you see two partitions listed (indicated by their UUID): your root partition (mounted on root, /, type ext4), and your swap partition, that is not mounted ("none", type swap)

---

### Post by renoirbleu on 2011-01-23
thank you vanadium. 
sorry to bother you again but how can I get the output of "sudo blkid"? 

and will there be any other changes I can expect from adding my swap partition on the start up ? e.g. slowing down or whatsoever...

---

### Post by vanadium on 2011-01-24
Open a terminal (under Applications - Accessories) and give the command "sudo blkid". When asked, provide your login password then press enter.

---

### Post by renoirbleu on 2011-01-24
/dev/sda1: LABEL="RECOVERY" UUID="0868EAEB68EAD70A" TYPE="ntfs" 
/dev/sda2: UUID="BA24ED2724ECE77B" TYPE="ntfs" 
/dev/sda3: LABEL="bbJ-LOCAL" UUID="D48685F98685DC7C" TYPE="ntfs" 
/dev/sda5: UUID="a7e880e2-95b2-4f0f-995e-3db2f896286b" TYPE="ext4" 
/dev/sda6: UUID="eaa8df7a-b9e5-44ed-9141-850e55ec46b5" TYPE="swap" 

I guess this is it ?

---

### Post by vanadium on 2011-01-24
Very strange problem indeed, for which I don't have a solution. This password does not contain strange characters, I suppose? The key combination "Ctrl+D" will close the terminal. However, it does not look as if that is the issue.

---

### Post by renoirbleu on 2011-01-25
no, i don't have D letter in my password.
but I managed to work it out anyway.
could you take a look at it please?
many many thanks. :)

---

### Post by vanadium on 2011-01-25
Do not edit old posts: this confuses the thread.

You have three ntfs drives:
/dev/sda1: LABEL="RECOVERY" UUID="0868EAEB68EAD70A" TYPE="ntfs"
/dev/sda2: UUID="BA24ED2724ECE77B" TYPE="ntfs"
/dev/sda3: LABEL="bbJ-LOCAL" UUID="D48685F98685DC7C" TYPE="ntfs"

I cannot know which one it is you want to mount upon startup. You could indeed mount both (sda1 is a recovery partition which you do not need to mount).

You need a mount point: a directory within your file system, so make one:
```

sudo mkdir /mnt/sda2

```
This could also be done graphically using a nautilus window in root mode.

Now, we will edit /etc/fstab to mount sda2 in /mnt/sda2. Load /etc/fstab in your editor as root:
```

gksudo gedit /etc/fstab

```
Add a line for the drive:
```

UUID="BA24ED2724ECE77B" /mnt/sda2 ntfs dmask=000,fmask=111 0 0

```

The dmask option sets all permissions open, such that anyone can do anything on the partition. For files, however, the executable bit is not set. If you want this to be more restrictive, you need to change these umask values and use the uid or gid options to assign the partition to a specific user/group. By default, the partition is owned by root.

Save the file. Check if all is OK using
```

sudo mount -a

```
If no output is produced, all is well and your partition is accessible in /mnt/sda2.

To have convenient access from within your home directory, create a link:
```

ln -s /mnt/sda2 ~/mywindowsdrive

```
Now, you will find a directory "mywindowsdrive" (name it as you want) that contains the data on your ntfs partition.

---

### Post by renoirbleu on 2011-01-25
excuse me for the confusion (i didn't expect that you'll answer me back that soon).
I named my vista drive as bbJ-LOCAL before so I am sure that I need sda3 to be mounted. 
However, I don't understand where this sda2 came from...? 

anyway, how can I make a mount point in a directory within my file system..... typing this code with sda3 ? plus, I don't know how to open nautilus window thing... 

the rest seems fine... just typing them in fstab file, right ? :)

---

