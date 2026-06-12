---
title: "Mount Sony Ericsson W800i Gutsy Gibbon"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by moisessalum on 2007-10-24
I recently upgraded to Gutsy. ( I have many problems now!!:()

One problem, is that I can't mount my Sony Ericsson W800i to my computer.

When I used Feisty, it mounted instantly, but now, I get an error message.

It appears a little error message like this.

> Cannot mount volume.
Unable to mount volume.

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,   missing codepage or helper program, or other error    In some cases useful info is found in syslog - try    dmesg | tail or so.

I run dmesg | tail and this is what appears.

> 
moises@moises-desklap:~$ dmesg | tail
[ 1787.736000] SCSI device sdb: 1921024 512-byte hdwr sectors (984 MB)
[ 1787.772000] sdb: Write Protect is off
[ 1787.772000] sdb: Mode Sense: 00 6a 00 00
[ 1787.772000] sdb: assuming drive cache: write through
[ 1787.784000] SCSI device sdb: 1921024 512-byte hdwr sectors (984 MB)
[ 1787.792000] sdb: Write Protect is off
[ 1787.792000] sdb: Mode Sense: 00 6a 00 00
[ 1787.792000] sdb: assuming drive cache: write through
[ 1787.792000]  sdb: sdb1
[ 1788.920000] FAT: Unrecognized mount option "usefree" or missing value


I don't know what to do!!!

Help Please!!

---

### Post by Solenoid on 2007-11-22
I have the same problem, when I connect the USB cable the phone just flashes in Computer and then goes away, I can try to click on it before it disappears and it says "Unable to mount media - There is probably no media in the drive". I have tried some packages, but no luck. Can anybody point me to the right direction?

---

### Post by chronographer on 2007-11-25
Hello.  I don't know how long ago you posted this but I have just plugged my phone in and it mounted automagically!  Cool eh?

---

### Post by reza81 on 2007-11-26
I have a K800i with the same problem. In Feisty it worked just fine

---

### Post by Solenoid on 2007-11-26
I'm still trying to figure it out. When in Windows XP I used to go the My Computer -> Manage and there find it with its missing driver, then upon clicking *update driver* it found it and worked perfectly. In Ubuntu there's a similar thing called *Hardware Information* (under Preferences). I can see my Sony Ericsson W800 there. By scrolling down there's even a Memory Stick at /dev/sdb and its volume at /dev/sdb1. I tried to mount it, but it asked for the filesystem, what filesystem does a USB card/stick have? I was going to try FAT, but it seems there's no such thing.

Was this removed in Ubuntu Gutsy? Why? Why can some people connect their phone with no problems? Do I have to recompile my kernel and enable some options... or something like that.

---

### Post by reza81 on 2007-11-26
Oke to fix this you need to make a mount point.

You have to look wath the device name is. To do this:

```
sudo fdisk -l
```

than you see all of your connected devices


```

sudo mkdir /media/phone

sudo mount /dev/**sdh1** /media/phone

```

---

### Post by reza81 on 2007-11-26
sudo fdisk -l <<< gives you an output like this 

```

rza@space-ride:~$ sudo fdisk -l
[sudo] password for rza:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39fa39f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         304     2441848+  83  Linux
/dev/sda2   *         305        2432    17093160   83  Linux
/dev/sda3            2433        9729    58613152+  83  Linux

Disk /dev/sdb: 320.0 GB, 320046346240 bytes
255 heads, 63 sectors/track, 38910 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29aa5e05

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38910   312544543+  83  Linux

Disk /dev/sdg: 86 MB, 86016000 bytes
14 heads, 10 sectors/track, 1200 cylinders
Units = cylinders of 140 * 512 = 71680 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        1021       71400+   4  FAT16 <32M

Disk /dev/sdh: 956 MB, 956238336 bytes
64 heads, 32 sectors/track, 911 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1         912      933826+   6  FAT16
rza@space-ride:~$ 


```

---

### Post by Solenoid on 2007-11-26
Still asks for filesystem (I made the W800i directory all by myself trough the terminal :)).

```

solenoid@desktop:~$ sudo mount /dev/sdb1 /media/w800i
mount: you must specify the filesystem type

``` doesn't work, it asks for the filesystem.

Here's what it gave me,

```

solenoid@desktop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd35cd35c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        2885     7815622+  83  Linux
/dev/sda3           24076       24321     1975995   82  Linux swap / Solaris
/dev/sda4            2886       24075   170208675   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2045 MB, 2045771776 bytes
128 heads, 32 sectors/track, 975 cylinders
Units = cylinders of 4096 * 512 = 2097152 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     1997636+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(975, 127, 32) logical=(975, 63, 32)

```

---

### Post by Solenoid on 2007-11-27
Solved. For those with seek the answer to the same question:

1) make a mount point, I made mine in */media/w800i*, to do this open the terminal and enter
```
sudo mkdir /media/w800i
```
this will be the folder where you access the memory stick - feel free to change w800i to anything you want.

2) enter this in the terminal
```
sudo mount -t vfat /dev/sdb1 /media/w800i
```
where sdb1 is your memory stick (I found this in Hardware Information under preferences).

Now you can access your memory stick from /media/w800i.

Also when removing your device you should unmount it, probably to avoid file corruption.

So before removing the phone enter this in the terminal:
```
sudo umount /media/w800i
```

Correct me if I'm wrong.

---

### Post by Solenoid on 2007-11-27
There's still an issue :(, I can't add stuff to the memory stick and some characters arent displayed (extended ASCII I think: é, è, ü, ö...). I tried to add -w (read/write), but since it's already by default it didn't change anything. I'm able to read files though.

---

### Post by chronographer on 2007-11-28
If that was ntfs filesystem, you may need to use "mount -t ntfs-3g <source> <target>" I don't know if this helps though, but I think Ubuntu earlier than Gutsy would mount ntfs and you could read, but not write, so with ntfs-3g you can read and write...  If you don't have the package "ntfs-3g" then enable the universe repository and search for it in synaptic. the package is called ntfs-3g surprisingly!

---

### Post by Solenoid on 2007-11-28
That's what it told me when I tried with ntfs-3g:
```

solenoid@desktop:~$  sudo mount -t ntfs-3g /dev/sdb1 /media/w800i
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

When I *sudo fdisk -l* it tells me that the *sdb1* system is *W95 FAT32*. Right after that I tried *vfat* again and it worked like before.

---

### Post by co0lingFir3 on 2008-01-17
I still dont understand why gutsy wont mount the w800i automatically. however it works for me if i mount it manually. one problem remains: i've only write access as root. i tried to change the rights but it didnt work. anyone got a solution on that?!

---

### Post by Dafty on 2008-02-25
Same problem for me with the latest Gutsy 7.10 and a W800.

The drive appears for a while in Computer, but can't be mounted.

However I can't see it in fdisk at any point either:

[FONT="Courier New"]richard@acer-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9cb6c7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14266   114591613+  83  Linux
/dev/sda2           14267       14593     2626627+   5  Extended
/dev/sda5           14267       14593     2626596   82  Linux swap / Solaris
richard@acer-laptop:~$ [/FONT]

Errors from dmesg if anyone can work them out ;-)

[FONT="Courier New"][ 1123.783160] : Add. Sense: Medium not present
[ 1123.783164] end_request: I/O error, dev sdb, sector 15908856
[ 1123.794348] sd 5:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1123.794354] : Add. Sense: Medium not present
[ 1123.794358] end_request: I/O error, dev sdb, sector 0
[ 1123.805543] sd 5:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] [/FONT]

Also sometimes when using fdisk the command freezes after sda5 above for some time (presumably trying to read the device. Error messages from dmesg after doing the fdisk where it froze:

[FONT="Courier New"][ 1350.800509] usb 1-1: reset full speed USB device using ohci_hcd and address 5
[ 1350.903910] sd 5:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1350.903917] : Add. Sense: Medium not present
[ 1350.903922] end_request: I/O error, dev sdb, sector 15908856
[ 1350.903925] printk: 32 messages suppressed.
[ 1350.903928] Buffer I/O error on device sdb, logical block 1988607
[ 1350.913679] sd 5:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1350.913685] : Add. Sense: Medium not present
[ 1350.913690] end_request: I/O error, dev sdb, sector 15908856
[ 1350.913695] Buffer I/O error on device sdb, logical block 1988607[/FONT]

Any suggestions appreciated.


Richard

---

### Post by jastonas on 2008-05-07
Very helpful thread! worked perfectly fine for me. Not to ask a lot, but is there a way for this to be done automatically from now on?

---

### Post by co0lingFir3 on 2008-05-16
wanted to ask the same thing, jastonas ^^
there must be some way to mount my w800i automatically when plugged in. i tried to modify /etc/fstab by adding:
```
# added by me: Sony Ericsson W800i
Label=Sony Eri Memory Stick 	/media/w800i/		vfat
```
somehow it didnt work... so how can i mount it automatically?

greez,
cF

---

