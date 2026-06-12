---
title: "Ubuntu can't find partitions?"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Enk on 2011-04-08
Hi

I've just upgraded to 11.04. 

I've got 3 partitions on my hard drive /, /home and swap.

When I boot it all loads fine untill just after the "Ubuntu 11.04"-loading screen.

Then I get a message saying "Can't find /. Waiting for harddrive to be ready.". Or something like that (I am at work now so don't remember 100%).

I've got a choice between skipping and aborting (or waiting for the harddrive).

If I skip I get a new message about /home not being found, and if I skip that I get an error and end up in a terminal window.

I haven't toutched any hardware, and haven't configured anything. 

Any idea how to fix? I'm kinda noobish when it comes to this, but are the fstab-file not used anymore? Can remember reading something about that :P

Any replies are welcome.

---

### Post by Harry33 on 2011-04-08
> **Enk said:**
> Hi
I've just upgraded to 11.04. 
I've got 3 partitions on my hard drive /, /home and swap.
When I boot it all loads fine untill just after the "Ubuntu 11.04"-loading screen.
Then I get a message saying "Can't find /. Waiting for harddrive to be ready.". Or something like that (I am at work now so don't remember 100%).
I've got a choice between skipping and aborting (or waiting for the harddrive).
If I skip I get a new message about /home not being found, and if I skip that I get an error and end up in a terminal window.
I haven't toutched any hardware, and haven't configured anything. 
Any idea how to fix? I'm kinda noobish when it comes to this, but are the fstab-file not used anymore? Can remember reading something about that :P
Any replies are welcome.

The file fstab is an important file and is indeed used.
You could print here the contents of your /etc/fstab file.
Also print here the output of the command:
```
sudo blkid
```

---

### Post by coffeecat on 2011-04-08
+1 to Harry33's suggestion, but it would be a good idea to run the boot info script. The output of that includes blkid and fstab and a lot else useful besides. Here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please post the output between [noparse]```
 and 
```[/noparse] tags for legibility.

Obviously, you'll need to use a live CD or live USB for this, but please use Maverick or Lucid. The 055 version of the boot script gives odd results in the mbr when run with the Natty live CD and I don't have the link to the development Natty-compatible version.

---

### Post by Kevbert on 2011-04-08
Same problem here. I've tried installing the latest daily build of Natty and also tried an upgrade from Maverick to Natty and get the message that I need to manually mount the drive or continue.  The repair option does not work for me with the Ubuntu Natty kernel. Everything works fine with Natty Kubuntu 2.6.38-8 kernel. The partition in question is sdb7.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=64e274ea-b7ab-4ac0-b5d8-feaa208b5460 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6c104125-11d8-4775-9206-5dc82915e422 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0**** 
```

```
$ sudo blkid
/dev/sda1: UUID="F8D82972D8292FF4" TYPE="ntfs" 
/dev/sda5: LABEL="Music" UUID="C82C72412C722B18" TYPE="ntfs" 
/dev/sda6: LABEL="Data" UUID="9660546760544FDB" TYPE="ntfs" 
/dev/sda7: UUID="6c104125-11d8-4775-9206-5dc82915e422" TYPE="swap" 
/dev/sda8: UUID="8775544d-eccc-4020-a8c7-e811b7b14ed0" TYPE="ext4" 
/dev/sdb1: LABEL="ISO-FILES" UUID="4A47-915E" TYPE="vfat" 
/dev/sdb5: UUID="e9fa767d-2de9-4128-8233-bd7a79e2c0f6" TYPE="ext4" 
/dev/sdb6: UUID="1d4b97a5-5f1f-43e5-8eca-58d94f4481fc" TYPE="ext4" 
/dev/sdb7: UUID="64e274ea-b7ab-4ac0-b5d8-feaa208b5460" TYPE="ext4" 
$
```

---

### Post by ghostborg on 2011-04-08
This is what I did to add data drives to my system.
I am just a home user and no expert.

Here is an example of one of my drives in my fstab located at /etc/fstab .

# /dev/sdb1
UUID=495cdd8b-c9a6-4729-8309-d8bef4c3eb90	/media/MediaDiskB	ext4	defaults	0	0

The UUID is a better way of referencing the drive in case you move them around, change port connections, in your machine. It is ok to use the mount device /dev/sdb1 as in the comment above. Of course you will need to determine what your device is /etc/???? . Notice the one in sdb1 refers to the first partition on the drive.

Afterward I had to issue the command: You will need to change this to match your mount point that you entered in the fstab.
```
sudo chmod 777 /media/MediaDiskB
``` 

to give me permissions to use the drive as it was mounted
as root owned it.

Another usefull command is:
```
sudo mount -a
```

will mount all the drives in your fstab file, so you don't have to reboot.

---

### Post by ranch hand on 2011-04-08
There is a problem with grub and uuid that is effecting some folks.  Sounds like your problem.

The boot info script would be a real good idea.

While on the live CD you might want to try;
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Might help.

---

### Post by oldfred on 2011-04-08
Get last development version of Boot Info Script:
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

```

---

### Post by Enk on 2011-04-08
I'm just fooling around in the recovery console-thing on my machine. One thing I've noticed is that my partitions was not writeable. "mount -a" did nothing, but when I chmod'ed my partitions (sda1, sda5, sda6), and then ran "mount -a", I was able to see my home folder in /home. 

When I rebooted, the partitions was back to unwriteable tho.

I'm downloading 10.04 and going to do some more testing when I can boot up in live.

---

### Post by Enk on 2011-04-09
Finally gotten into live CD.


Here is my fstab-file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a628cfd0-268a-4d90-b22f-3ae7a6f3deb5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ba1d5b17-beb9-4334-bb31-6e94c4ecd1ab none            swap    sw              0       0
# home on own partition
/dev/sda1 /home ext4 nodev,nosuid 0 2
```

And the result of blkid
```
ubuntu@ubuntu:/$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6bb30b08-70fc-4c8b-a52e-1e0e06add5ce" TYPE="ext4" 
/dev/sda5: UUID="ba1d5b17-beb9-4334-bb31-6e94c4ecd1ab" TYPE="swap" 
/dev/sda6: UUID="a628cfd0-268a-4d90-b22f-3ae7a6f3deb5" TYPE="ext4"
```

I also ran the bootscript and pasted the RESULT.txt-file here:
[https://gist.github.com/911248](https://gist.github.com/911248)

I'm going to try to reinstall GRUB2. And again; all tips are welcome!

---

### Post by coffeecat on 2011-04-09
Which version of Ubuntu did you use to run the boot script and which version of boot script did you use? This..

```
=> Grub 2 is installed in the MBR of /dev/sda and looks for Be.
```... is the sort of thing you get when you run the current boot script from Natty, "looks for Be" making no sense. 

If you are running a Natty live CD, you need to run the development version of the boot script that oldfred gave you the wget command for. Or, if you use the current released version of the boot script that I linked to, you need to run this in Lucid or Maverick, as I pointed out before.

Or, if you did run compatible versions of Ubuntu and the boot script, please confirm this, because that part of the output is decidedly odd.

---

### Post by Enk on 2011-04-09
I'm not sure :P 

I just updated to 11.04 using update manager in my working Ubuntu 10.10-installation. The LiveCD is also Ubuntu 10.10.

---

### Post by coffeecat on 2011-04-09
> **Enk said:**
> I'm not sure :P 

:?

I presume you can't boot your upgraded Ubuntu so you must have been using a live CD. Am I correct? Or have I misunderstood? So which version of Ubuntu were you using and which version of the boot script? This is an important point because if that bizarre bit of output is not due to Ubuntu/boot script incompatibility it could indicate something more serious.

---

### Post by Enk on 2011-04-09
> **coffeecat said:**
> :?

I presume you can't boot your upgraded Ubuntu so you must have been using a live CD. Am I correct? Or have I misunderstood? So which version of Ubuntu were you using and which version of the boot script? This is an important point because if that bizarre bit of output is not due to Ubuntu/boot script incompatibility it could indicate something more serious.

Correct. I'm using a LiveCD. 

I just downloaded the boot script from Sourceforge. It's name is xxx055, so I guess it's version 0.55 or something? :P


Edit: downloading the development version (v0.56) and see if I get any more info.

Here are the result from boot_info_script056: [https://gist.github.com/911276](https://gist.github.com/911276)

---

### Post by coffeecat on 2011-04-09
You were using the **Maverick/10.10 **live CD.

And the 0.55 version of the boot script **or something**.

We need to be precise. Maverick and the 0.55 version of boot script are compatible, but the more serious problem that I hinted at is in this thread:

[http://ubuntuforums.org/showthread.php?t=1722064](http://ubuntuforums.org/showthread.php?t=1722064)

You'll see that the OP also saw "looks for Be" in their boot script output and was using the Maverick CD and the 0.55 boot script. Their problem was a failing hard drive. I'm not saying the two are linked but if that was my machine I would boot up with a live CD and run a SMART test from Disk Utility to be sure.

---

### Post by Enk on 2011-04-09
Yes.

LiveCD: Maverick 10.10
BootScript: Both ran 0.55 and 0.56

I ran a Check Filesystem from Disk Utility and got "Filesystem Clean" on the partitions. 

I could not find any SMART test option, but the SMART status said "Not Supported".

---

### Post by Enk on 2011-04-09
Anyone got any more tips? Still stuck :(

---

### Post by coffeecat on 2011-04-09
I can't see anything wrong with the latest boot script output, although I'd be interested in what others make of this:

```

=> Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.
```It looks OK, but I'm not familiar with the way 0.56 is reporting.

Looking back at your OP I wonder if it's an incomplete upgrade. I was doing an overdue upgrade to Kubuntu Natty yesterday and KDE's equivalent to update manager hung on me halfway through, so I rebooted. Except it wouldn't boot up. Like you I can't remember the exact error message but it was similar to yours. Eventually I chroot'ed in from another partition and coaxed it into finishing the upgrade with a mixture of 'aptitude safe-upgrade' and 'apt-get dist-upgrade'. It needed both. Now the system boots OK.

It wouldn't do any harm to chroot into your install from a live CD and see if any updates help.

---

### Post by oldfred on 2011-04-09
Suggestion for next time:
With a 1000GB drive it would be a good idea just to create another root partition (or two) for experimenting with beta installs. I actually have many roots, at least 3 for Ubuntu so I have old install, current install, and beta, plus another root or two for experimenting. I keep root partitions at 20-25GB so you have lots of room for system partitions.

---

