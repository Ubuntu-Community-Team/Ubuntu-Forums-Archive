---
title: "I Really Broke My Display Drivers"
date: 2013-11-21
forum: Multimedia Software
---

### Post by redbikemaster on 2013-11-21
So, this happened a while back, but I was fiddling with my display drivers, and I really fouled them up. I now cannot get to the login screen. As soon as I get past GRUB, the screen just flashes on and off showing no image. I can't get to a root console or anything.

---

### Post by electrohandyman501 on 2013-11-21
Can you boot from a LiveCD or USB?

---

### Post by redbikemaster on 2013-11-22
Yes. When booting, it'll flash the 'lubuntu' screen, then goes to the flashing.

---

### Post by Bashing-om on 2013-11-22
redbikemaster; Hi !

As a means of fault isolation, trying to preclude hardware issues; TRY;
Boot the liveDVD, at the purple splash screen -> depress and hold shift key -> language screen, escape key to accept the default -> boot options screen.
Here f6 key for preset boot options ->arrow down to the preset option(s)space or enter to accept and then the escape key to exit;
Choose "nomodeset" - for Nvidia and ATI graphics cards ->Enter key to continue the boot process to the GUI desk top.
Do you get a usable GUI desktop, or else what results from this procedure , did you try some of the other preset boot options ?

[INDENT][INDENT]further advise is pending
[/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-01-10
Sorry for being gone so long! Had to replace the PSU for an unrelated thing.

I can get to a root-level prompt now through recovery mode, so I now just need help with the commands on how to install the default drivers from there.

---

### Post by QIII on 2014-01-10
Hello!

Did you install the proprietary driver earlier?

You need only remove the proprietary driver and remove or rename /etc/X11/xorg.conf.

But the method for removing the driver depends on how you installed it.

Did you install it from the repo; by downloading from ATI and creating a .deb; or by running the .run file from ATI directly?

---

### Post by redbikemaster on 2014-01-10
Oh, tough one. I honestly can't remember, as it was over a year ago. Is there a way to check?

---

### Post by QIII on 2014-01-10
But you do remember installing a driver?

---

### Post by redbikemaster on 2014-01-10
Yep. I definitely installed proprietary drivers. I may have done it via the 'Additional Drivers' GUI.

---

### Post by QIII on 2014-01-10
That's the easiest thing, then.

From the command prompt in recovery mode:

(Edit:  from long familiarity, I forgot to tell you something obvious to me -- you have to mount the drive ...)
```
mount -o remount,rw /
```

to mount the drive in read/write mode

then

```
apt-get purge fglrx* fglrx-amdcccle*
```

then

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

The first command removes the driver, the second renames the xorg.conf file.  You can remove it later, but I generally recommend renaming things initially just in case you decide you want them back.

Then reboot.

---

### Post by redbikemaster on 2014-01-10
Going to try that now. Will report in a second.

---

### Post by Bashing-om on 2014-01-10
redbikemasterl;  Hello once more.

Let's try a quicker way than through the "recovery" console.

Boot to the grub menu in your install;
Top entry should be the latest kernel - highlighted -> "e" key for edit mode;
Boot parameters screen .. arrow down and across to the term "quiet splash" and add the term "nomodeset" - with out the quotes ;
key-combo ctl+x to continue the boot process, hopefully to the GUI login;
Login here -> desktop (degraded graphics is ok);
Locate the utility "Additional Drivers" (location varies with version of ubuntu installed) and install the recommeded driver.

[INDENT][INDENT]hope that is all there is too it
[/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-01-10
Neither method worked. First method resulted in the error 'fglrx is not installed' or something like that.

other method had no effect.

---

### Post by QIII on 2014-01-10
OK.  Are you absolutely sure you installed the proprietary driver?

If so, let's see if you installed it a different way.  If you installed it directly from the .run file, apt wouldn't know about it, so it would tell you it's not installed.

Mount the drive rw again.

Then

```
amdconfig --uninstall
```

---

### Post by redbikemaster on 2014-01-10
It said ```
fglrx uninstall completed
``` so I rebooted, but no change. Do I still need to rename xorg.conf?

---

### Post by QIII on 2014-01-10
Ya.  I should have said that.  If it's there, your OS is trying to follow its instructions, which it can't.

---

### Post by redbikemaster on 2014-01-10
Doing so now. Sorry about my lack of knowledge. I've been forced to use Win 7 due to school, and have had no time to use Linux, so I'm uber rusty.

---

### Post by QIII on 2014-01-10
No need to apologize.  That's why we're here!  ;)

---

### Post by redbikemaster on 2014-01-10
Returned 
```

mv: cannot stat '/etc/X11/xorg.conf': No such file or directory

```

---

### Post by QIII on 2014-01-10
OK.  That means it wasn't generated to begin with, or amdconfig removed it for you.

Now that you got it uninstalled, try bashing-om's "nomodeset" method and see if you can get to your desktop.

---

### Post by QIII on 2014-01-10
Oh, hold on a second!

that should be 

/etc/X11/xorg.conf

notice the slash at the start

Edit:  Ha!  You put the slash in.  Nevermind!

---

### Post by zemega on 2014-01-10
Why don't you try uninstalling ubuntu-desktop and reinstall it back?

---

### Post by redbikemaster on 2014-01-10
I must be doing the 'nomodeset' wrong, as it yet again has no effect.

---

### Post by QIII on 2014-01-10
C&P the exact text you are issuing and let's have a look at it.

---

### Post by redbikemaster on 2014-01-10
Good idea.

```

nomodeset

```

i'm putting it one space after
```

quiet splash

```

and one space before

```

$vt_han\doff

```

making the line read
```

linux      /boot/vmlinuz-3.5.0-23-generic root=UUID=9f8eaa86-025f-4b93-b231-cc17d8fb1e49 ro   quiet splash nomodeset $vt_han\duff

```

instead of
```

linux      /boot/vmlinuz-3.5.0-23-generic root=UUID=9f8eaa86-025f-4b93-b231-cc17d8fb1e49 ro   quiet splash $vt_han\duff

```

---

### Post by Bashing-om on 2014-01-10
redbikemasterl

Does not look right to me at all .. the "$vt_han\duff" I think should be " $vt_handoff".

Would have to reboot into another install to check.. but I think that is correct.

[INDENT][INDENT]my bit to help
[/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-01-10
I'm a blind idiot. It is an 'o', not a 'u'. Handoff. Doesn't the backslash merely function as an escape character? On my screen, it looks like
```

han\
doff

```

so is it escaping a new line character by that?

i should specify it goes to a new line due to it being the edge of the screen.

---

### Post by Bashing-om on 2014-01-10
redbikemaster;

I am not real sure what the escape character would do in this context,, It should read:
"ro quiet splash nomodeset $vt_handoff"

Try it from grub's menu once more and advise of results...

past my beddy bye time here.. will catch up on this thread in my AM.

edit: else we are going to go to a Command Line Interface, and look at what is !
It is not luck
[INDENT][INDENT]but attention to detail
[INDENT][INDENT][INDENT]that makes things work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-01-10
No change.

---

### Post by Bashing-om on 2014-01-10
redbikemaster; Yuk !

OK, Let's see if we can determine what is not going on .. CLI time.
Edit grub's boot parameter :
Remove "quiet splash nomodeset" and insert the term "text" -> ctl+x to continue the boot process to a text login (TTY1) ;
Login in with user name and password.
Now, let's look ;
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

``` It can be a real pain to figure out copy and paste from terminal, so presently do not bother, our interest here is from my reference marked in red:
> 
[sudo] password for sysop: 
  *-display:0             
      [color=red] description: VGA compatible controller
       product: RV515 [Radeon X1300/X1550][/color]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
      [color=red] configuration: driver=radeon latency=0[/color]
       resources: irq:16 memory:e0000000-efffffff memory:fd4f0000-fd4fffff ioport:5c00(size=256) memory:fd400000-fd41ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV515 [Radeon X1300/X1550 Series] (Secondary)
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0.1
       bus info: pci@0000:06:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress cap_list
       configuration: latency=0
       resources: memory:fd4e0000-fd4effff
sysop@1310mini:~$

-----------------------------
The output from "lspci -nnk | grep -iA3 vga" we are only concerned that there is but one graphics card listed and it is the same same as from the prior output.
In essence, we want to know what graphics card(s) you have onboard and what - if any - driver is loaded.
From this we can determine what driver should be installed.

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-05-30
Hey, I'm finally back! Sorry again.

So, I replaced
```

quiet splash

```
with
```

text

```
and hit Ctrl + X, and it rebooted and did the exact same thing. Hit 'e' again, and sure enough, it said
```

quiet splash

```
again!

---

### Post by Bashing-om on 2014-05-30
redbikemaster; Hey,

Still here 6 months later -

OK, with the boot parameter 'text" you should boot to a textual terminal interface (TTY1).

So you do get to the grub boot menu;
Then:
'e' key for edit mode;
edit in the boot parameter text by replacing " quiet splash nomodeset $vt_handoff ";
key combo ctl+x to continue the boot process.

Now, you do not get to the textual terminal interface ????

Keep in mind this edit will not persist a re-boot. Any edit to the boot parameters from the grub menu is a one-time-boot method only.

Trying to get our ducks all in a row, and we are reading from the same book and on the same page.
Working to get you a graphics driver installed.

If you can not boot to the terminal, we need to find out why and correct that condition.

[INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-05-30
Oh, I didn't know to replace the $vt_handoff also. Will try that now.

---

### Post by redbikemaster on 2014-05-30
So far, all I get is a blank screen. Nothing ever comes up after hitting Ctrl + X.

---

### Post by Bashing-om on 2014-05-30
redbikemaster; UnGood !

OK, can you boot the liveDVD in "try ubuntu" mode to the GUI desk top ?

From there I suggest we take a look and make sure the boot files are in-place on the installed system.

[INDENT][INDENT]we be look'n for that cause
[/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-05-30
I'm in the GUI desktop now.

---

### Post by Bashing-om on 2014-05-30
redbikemaster; Great .

That do mean it ain't the hardware at fault.

OK let's look, by mounting the installed root partition from the liveDVD and see what is:
From that liveDVD: -> key combo ctl+alt+t yields a terminal.
In preparation to Mount that installed partition: 
Post back the outputs - between code tags to maintain readability - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
Once we know the where we can do the how.

[INDENT][INDENT]as we roll up sleeves to
[INDENT][INDENT][INDENT]get to work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-05-30
```
sudo fdisk -lu
```
Result:
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005f4e


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1936752639   968375296   83  Linux
/dev/sda2      1936754686  1953523711     8384513    5  Extended
/dev/sda5      1936754688  1953523711     8384512   82  Linux swap / Solaris


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x83060f04


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848  3907026943  1953410048    7  HPFS/NTFS/exFAT
Note: sector size is 4096 (not 512)


Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xda8b4c4b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   536870655  2147474432    7  HPFS/NTFS/exFAT

```

sudo parted -l
```

Model: ATA ST1000DM005 HD10 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  992GB   992GB   primary   ext4            boot
 2      992GB   1000GB  8586MB  extended
 5      992GB   1000GB  8586MB  logical   linux-swap(v1)




Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   2000GB  2000GB  primary  ntfs




Model: Seagate Backup+ Desk (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      8389kB  2199GB  2199GB  primary               boot




Model: SanDisk Cruzer (scsi)
Disk /dev/sdd: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

```

---

### Post by Bashing-om on 2014-05-30
redbikemaster; OK,

EDIT: getting scattered brained -- Do this from the liveUSB.

Now that we know where to look, let's see what is there before replacing files.
set up to look:
```

sudo mkdir /mnt/look
sudo mount /dev/sda1 /mnt/look

```
and now to look at look:
What returns from terminal commands:
```

ls -la /mnt/look/
ls -la /mnt/look/boot
ls -la /mnt/look/boot/grub

```

When all done with look'n in look we MUST UNmount that partition.
```

sudo umount /mnt/look

```
now you may shut the system down or reboot or whatever.

Now if all is in place as I expect, will (re-)install the boot code to the MBR of that 1st hard drive ( now that 1st hard drive must be set as the 1st hard drive boot priority in bios !!).

And then we see what the situation is.

[INDENT][INDENT]it is all in the process.
[/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-05-30
Here's the results:
```

lubuntu@lubuntu:~$ sudo mkdir /mnt/look
lubuntu@lubuntu:~$ sudo mount /dev/sda1 /mnt/look
lubuntu@lubuntu:~$ ls -la /mnt/look/
total 116
drwxr-xr-x  23 root root  4096 Mar  1  2013 .
drwxr-xr-x   1 root root    60 May 30 17:51 ..
drwxr-xr-x   2 root root  4096 Dec 17  2012 bin
drwxr-xr-x   3 root root  4096 Jan  9 22:51 boot
drwxr-xr-x   2 root root  4096 Jul  8  2012 cdrom
drwxr-xr-x   5 root root  4096 Apr 23  2012 dev
drwxr-xr-x 165 root root 12288 May 30 14:05 etc
drwxr-xr-x   3 root root  4096 Feb 10  2013 home
lrwxrwxrwx   1 root root    32 Feb 10  2013 initrd.img -> boot/initrd.img-3.5.0-23-generic
lrwxrwxrwx   1 root root    33 Feb 10  2013 initrd.img.old -> /boot/initrd.img-3.5.0-23-generic
drwxr-xr-x  21 root root  4096 Mar  1  2013 lib
lrwxrwxrwx   1 root root    34 Nov  8  2012 libnss3.so -> /usr/lib/i386-linux-gnu/libnss3.so
drwx------   2 root root 16384 Jul  8  2012 lost+found
drwxr-xr-x   3 root root  4096 Nov  9  2012 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   6 root root  4096 Dec 17  2012 opt
drwxr-xr-x   2 root root  4096 Apr 19  2012 proc
drwx------  20 root root  4096 May 30 01:27 root
drwxr-xr-x   5 root root  4096 Jul  8  2012 run
drwxr-xr-x   2 root root 12288 Feb 10  2013 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Apr 23  2012 srv
drwxr-xr-x   2 root root  4096 Apr 14  2012 sys
drwxrwxrwt   6 root root  4096 May 30 14:04 tmp
drwxr-xr-x  11 root root  4096 Mar  1  2013 usr
drwxr-xr-x  13 root root  4096 May 30 14:05 var
lrwxrwxrwx   1 root root    29 Feb 10  2013 vmlinuz -> boot/vmlinuz-lubuntu@lubuntu:~$ ls -la /mnt/look/boot
total 90736
drwxr-xr-x  3 root root     4096 Jan  9 22:51 .
drwxr-xr-x 23 root root     4096 Mar  1  2013 ..
-rw-r--r--  1 root root   801704 Sep 26  2012 abi-3.2.0-32-generic-pae
-rw-r--r--  1 root root   853793 Oct 19  2012 abi-3.5.0-18-generic
-rw-r--r--  1 root root   853737 Nov 13  2012 abi-3.5.0-19-generic
-rw-r--r--  1 root root   856743 Jan 24  2013 abi-3.5.0-23-generic
-rw-r--r--  1 root root   147435 Sep 26  2012 config-3.2.0-32-generic-pae
-rw-r--r--  1 root root   154429 Oct 19  2012 config-3.5.0-18-generic
-rw-r--r--  1 root root   154403 Nov 13  2012 config-3.5.0-19-generic
-rw-r--r--  1 root root   154427 Jan 24  2013 config-3.5.0-23-generic
drwxr-xr-x  5 root root    12288 May 30 12:43 grub
-rw-r--r--  1 root root 13487764 Nov  9  2012 initrd.img-3.2.0-32-generic-pae
-rw-r--r--  1 root root 15070519 Nov  9  2012 initrd.img-3.5.0-18-generic
-rw-r--r--  1 root root 15069877 Dec 17  2012 initrd.img-3.5.0-19-generic
-rw-r--r--  1 root root 15072501 Jan  9 22:51 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root   176764 Jan  3  2013 memtest86+.bin
-rw-r--r--  1 root root   178944 Jan  3  2013 memtest86+_multiboot.bin
-rw-------  1 root root  2313078 Sep 26  2012 System.map-3.2.0-32-generic-pae
-rw-------  1 root root  2321612 Oct 19  2012 System.map-3.5.0-18-generic
-rw-------  1 root root  2321402 Nov 13  2012 System.map-3.5.0-19-generic
-rw-------  1 root root  2322953 Jan 24  2013 System.map-3.5.0-23-generic
-rw-------  1 root root  5014912 Sep 26  2012 vmlinuz-3.2.0-32-generic-pae
-rw-------  1 root root  5176048 Oct 19  2012 vmlinuz-3.5.0-18-generic
-rw-------  1 root root  5175696 Nov 13  2012 vmlinuz-3.5.0-19-generic
-rw-------  1 root root  5176144 Jan 24  2013 vmlinuz-3.5.0-23-generic
3.5.0-23-generic
lrwxrwxrwx   1 root root    29 Feb 10  2013 vmlinuz.old -> boot/vmlinuz-3.5.0-23-generic
lubuntu@lubuntu:~$ ls -la /mnt/look/boot
total 90736
drwxr-xr-x  3 root root     4096 Jan  9 22:51 .
drwxr-xr-x 23 root root     4096 Mar  1  2013 ..
-rw-r--r--  1 root root   801704 Sep 26  2012 abi-3.2.0-32-generic-pae
-rw-r--r--  1 root root   853793 Oct 19  2012 abi-3.5.0-18-generic
-rw-r--r--  1 root root   853737 Nov 13  2012 abi-3.5.0-19-generic
-rw-r--r--  1 root root   856743 Jan 24  2013 abi-3.5.0-23-generic
-rw-r--r--  1 root root   147435 Sep 26  2012 config-3.2.0-32-generic-pae
-rw-r--r--  1 root root   154429 Oct 19  2012 config-3.5.0-18-generic
-rw-r--r--  1 root root   154403 Nov 13  2012 config-3.5.0-19-generic
-rw-r--r--  1 root root   154427 Jan 24  2013 config-3.5.0-23-generic
drwxr-xr-x  5 root root    12288 May 30 12:43 grub
-rw-r--r--  1 root root 13487764 Nov  9  2012 initrd.img-3.2.0-32-generic-pae
-rw-r--r--  1 root root 15070519 Nov  9  2012 initrd.img-3.5.0-18-generic
-rw-r--r--  1 root root 15069877 Dec 17  2012 initrd.img-3.5.0-19-generic
-rw-r--r--  1 root root 15072501 Jan  9 22:51 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root   176764 Jan  3  2013 memtest86+.bin
-rw-r--r--  1 root root   178944 Jan  3  2013 memtest86+_multiboot.bin
-rw-------  1 root root  2313078 Sep 26  2012 System.map-3.2.0-32-generic-pae
-rw-------  1 root root  2321612 Oct 19  2012 System.map-3.5.0-18-generic
-rw-------  1 root root  2321402 Nov 13  2012 System.map-3.5.0-19-generic
-rw-------  1 root root  2322953 Jan 24  2013 System.map-3.5.0-23-generic
-rw-------  1 root root  5014912 Sep 26  2012 vmlinuz-3.2.0-32-generic-pae
-rw-------  1 root root  5176048 Oct 19  2012 vmlinuz-3.5.0-18-generic
-rw-------  1 root root  5175696 Nov 13  2012 vmlinuz-3.5.0-19-generic
-rw-------  1 root root  5176144 Jan 24  2013 vmlinuz-3.5.0-23-generic
lubuntu@lubuntu:~$ ls -la /mnt/look/boot/grub
total 2564
drwxr-xr-x 5 root root   12288 May 30 12:43 .
drwxr-xr-x 3 root root    4096 Jan  9 22:51 ..
drwxr-xr-x 2 root root    4096 Nov  9  2012 fonts
-rw-r--r-- 1 root root     699 Mar  1  2013 gfxblacklist.txt
-r--r--r-- 1 root root   12453 May 30 01:27 grub.cfg
-rw-r--r-- 1 root root    1024 May 30 13:54 grubenv
drwxr-xr-x 2 root root   12288 Nov  9  2012 i386-pc
drwxr-xr-x 2 root root    4096 Jul  8  2012 locale
-rw-r--r-- 1 root root 2560080 Nov  9  2012 unicode.pf2

```

---

### Post by Bashing-om on 2014-05-30
redbikemaster; Well well,

Everything looks to be there and in the right places....should boot, so we lookin' at  see'n as how it is not booting to replace the boot code in the master boot record of the hard drive.

NOW< consider -> looks like you are running release 12.10 (quantal) .. That version is  End-Of-Life and no longer enjoys support. The software repository has (or will be) been turned down. That fact may make it real tough to fix this system.

Are you in a position where the data and personal files on this system are backed up and you can clean install a current release ( 14.04 ! )  ?

In this situation - EOL - a clean install is highly recommended. But, it is your system, your time and your call.

[INDENT][INDENT][INDENT]whatcha wanna do 

[/INDENT][/INDENT][/INDENT]

---

### Post by redbikemaster on 2014-05-30
Well, I can get stuff off the drive using the LiveCD and my 16 GB flash drive. I might as well do that.

---

### Post by Bashing-om on 2014-05-30
redbikemaster; Hey,

I truly think that is the better thing to do to get ya up and happy with ubuntu.
Clean install 14.04 ( full support until 2019 !).

If that is what you are going to do ->
Please mark this thread solved; 
aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.

If there is any problem we will deal with it in a new thread.

[INDENT]it can only get better
[/INDENT]

---

