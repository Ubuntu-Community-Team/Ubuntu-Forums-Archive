---
title: "HOWTO: Make a permanent USB key that runs Natty so you can test"
date: 2010-12-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by castrojo on 2010-12-03
Hi everyone,

I've started this wiki page on how to create your own persistent Natty USB key so you can test and file bugs on Natty without having to break your existing computer:

[https://wiki.ubuntu.com/Unity/InstallUSBKey](https://wiki.ubuntu.com/Unity/InstallUSBKey)

Feel free to update the instructions if you find they are missing bits or if something is too complicated.

---

### Post by jfernyhough on 2010-12-03
OK - first the how-to looks good... here it comes - but isn't this just a LiveUSB with persistent storage? It's great for testing Ubiquity (the installer) but as far as testing the other aspects of the system will it work as well as using a full USB installation (e.g. on a UBS HDD) or in a virtual machine?

Isn't there already a script/program specifically for making a VM using the latest daily ISO?

---

### Post by castrojo on 2010-12-03
> **jfernyhough said:**
> OK - first the how-to looks good... here it comes - but isn't this just a LiveUSB with persistent storage?

Yep!

> 
Isn't there already a script/program specifically for making a VM using the latest daily ISO?

You're thinking about testdrive, but unfortunately you can't test Unity in a VM, it needs the bare metal in order to get the full experience, which is why we want to point a USB key as an option for people test and file/fix bugs and have an updating USB that they can test on multiple computers without risking the existing OS.

EDIT: Cool, the testdrive-gtk also has a button to just make a USB key right after you sync the ISO.

---

### Post by plun on 2010-12-03
Well. I haven't checked it against this....

[http://www.jonobacon.org/2010/11/30/testing-natty-and-unity-safely-with-a-usb-stick/](http://www.jonobacon.org/2010/11/30/testing-natty-and-unity-safely-with-a-usb-stick/)

Seems to be the same....

---

### Post by castrojo on 2010-12-03
Yeah I'm just basically moving it to the wiki so people can update it as we go along and add other stuff.

---

### Post by arpanaut on 2010-12-03
@whiprush

Seems the link in your signature is broken?

---

### Post by cariboo on 2010-12-03
The correct url is:

[https://wiki.ubuntu.com/Unity/Bitesize](https://wiki.ubuntu.com/Unity/Bitesize)

---

### Post by VMC on 2010-12-03
> **whiprush said:**
> 
You're thinking about testdrive, but unfortunately you **can't test Unity in a VM**, it needs the bare metal in order to get the full experience.
This is the most important part. Some folks test only using a VM, then when time for the release their left high and dry. A VM would never test your video hardware, which is usually the first thing to go.

---

### Post by jbrew on 2010-12-03
I have it loaded on the USB per the instructions, but it won't let me test Unity without 3d enabled.  Installing the NVIDIA drivers fails to the USB.  Is there something I'm missing or a workaround?

---

### Post by cariboo on 2010-12-03
You may have to setup some persistent space on your usb key in order to setup the drivers. It may be easier to use the nouveau drivers and just install libgl1-mesa-dri-experimental, then logout, then log back in again.

---

### Post by Arrowstar on 2010-12-03
I just used the Windows USB creator that is available on today's Natty daily build CD and attempted to boot with the resultant USB drive per the instructions.  However, the system appears to halt after displaying a BIOS version message.  It's not an error message, and nothing else is displayed.  The system simply stops booting.  Anyone notice this?  Should I try creating the USB drive with an Ubuntu version of the application instead?

---

### Post by cariboo on 2010-12-03
I would suggest you use the latest version of [unetbootin]("http://unetbootin.sourceforge.net/") in Windows.

---

### Post by efflandt on 2010-12-04
If you regularly download the daily iso, **zsync** would go quicker than downloading the whole thing regularly.  It updates your last iso to the most recent version by downloading only parts it needs to and backs up the previous one.  I wrote a script to do that and put it in my ~/bin in maverick:

```
#!/bin/bash
cd ~/Downloads # actually used full path
zsync http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso.zsync
```You generally cannot install proprietary video drivers on a USB iso, or do certain updates for kernels and other things that happen from the existing kernel image and squashfs file system before persistent data (casper-rw) is loop mounted.  So you really cannot follow along with everything just doing updates from the iso itself.

I have nvidia GT 430, so I tried libgl1-mesa-dri-experimental on the alpha1 iso, and it does work for glxinfo and glxgears (at about 5% of nvidia driver speed).  Some excepts from glxinfo:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4

OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.9
OpenGL shading language version string: 1.20

The live iso still complains, so it will not do unity, but the regular desktop works fine (I am posting from it).

I have been running a regular install of natty on 8 GB USB flash with nvidia drivers, and doing updates by just booting (recovery) and selecting "fix packages", then rebooting.  Not sure if that is a technically correct way to update, but is easy.  But it is way too slow on cheap USB, so I just installed alpha1 on SSD and will see how that goes.

---

### Post by MacUntu on 2010-12-04
> **efflandt said:**
> The live iso still complains, so it will not do unity

Weird, this worked fine for me. I booted the ISO, enabled the universe repositories with ```
sudo software-properties-gtk
```then did```
sudo apt-get update
sudo apt-get install libgl1-mesa-dri-experimental
``` logged out and back in, and tadaaa - Compiz/Unity was running just fine. :)

---

### Post by C.S.Cameron on 2010-12-04
Am I understanding right that doing an update/upgrade will now revise filesystem.squashfs?

Or does it just write stuff to casper-rw quickly filling a small flash drive?

If the later it should be noted that casper-rw can be mounted and stuff deleted if required to make it bootable again.

---

### Post by jfernyhough on 2010-12-04
> **C.S.Cameron said:**
> Or does it just write stuff to casper-rw quickly filling a small flash drive?This is what happens.> If the later it should be noted that casper-rw can be mounted and stuff deleted if required to make it bootable again.How do you do this? (Yeah, I could use Google but it's easier for people following the thread. ;))

---

### Post by C.S.Cameron on 2010-12-04
> **jfernyhough said:**
> This is what happens.How do you do this? (Yeah, I could use Google but it's easier for people following the thread. ;))

[http://ubuntuforums.org/showpost.php?p=7055983&postcount=2](http://ubuntuforums.org/showpost.php?p=7055983&postcount=2)

A good source of stuff to delete is in var/cache/apt/archives

Use gksu nautilus to get there

Edit
Now that I think about it I recall computer janitor will clean up the archives folder in a persistent install.

---

### Post by KegHead on 2010-12-04
Hi!

I'm running the usb key on a dell mini 9 w/no problems.

Updating and upgrading is ok.

It is very slow.

I don't really like the Unity tool bar.

I guess I'm old school and prefer the Gnome toolbars.

Is there any way to remove unity?

Thanks!

KegHead

---

### Post by plun on 2010-12-04
> **MacUntu said:**
> Weird, this worked fine for me. I booted the ISO, enabled the universe repositories with ```
sudo software-properties-gtk
```then did```
sudo apt-get update
sudo apt-get install libgl1-mesa-dri-experimental
``` logged out and back in, and tadaaa - Compiz/Unity was running just fine. :)

How can you install something on this....:confused:

This is NOT a real persistent USB install, much more work to fix a real one.

:confused:

---

### Post by cariboo on 2010-12-04
> **MacUntu said:**
> Weird, this worked fine for me. I booted the ISO, enabled the universe repositories with ```
sudo software-properties-gtk
```then did```
sudo apt-get update
sudo apt-get install libgl1-mesa-dri-experimental
``` logged out and back in, and tadaaa - Compiz/Unity was running just fine. :)


I'll confirm this, I just tried it myself,. My netbook with 945 chipset works out of the box.

Has anyone come up with an ATI/AMD solution?

BTW use ubuntu as the username and no password.

---

### Post by ronacc on 2010-12-04
startup disk creator will not let me select my zsync'd .iso as a source , it insists on using my dvd drive as the source even though there is no disk of any kind in it and it also mounts the dvd drive  as a nonexistant disk . 64bit natty , up to date , anyone else seeing this ?

---

### Post by ronacc on 2010-12-04
how do I make persistent space on a usbstick prepared with unetbootin ?

---

### Post by madjr on 2010-12-04
> **ronacc said:**
> how do I make persistent space on a usbstick prepared with unetbootin ?

i wonder this too

---

### Post by C.S.Cameron on 2010-12-04
> **ronacc said:**
> how do I make persistent space on a usbstick prepared with unetbootin ?

There are a couple of methods:

Pendrivelinux.com offers a casper-rw generator, use this to make a casper-rw file of suitable size for your flashdrive. You can generate a second one and rename it home-rw and it will store your home folder only. Maximum size for these is 4GB.
Then you need to modify syslinux.cfg, Add "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

The method I prefer is to use persistent partitions. 
Instead of using -rw files, create an ext2,3 or 4 partition and name it casper-rw, and optionally create a home-rw one also.
Modify syslinux.cfg as shown above.
This method is not limited to the 4GB FAT32 file size.

---

### Post by ronacc on 2010-12-04
I found out some more about my startup disk creator problem , if I have the usbstick inserted when I run startup disk creator it defaults to the dvd drive as source and cannot be changed , if I leave the usbstick unpluged until after I select the source I get a little further but still problems , when I plug the usbstick in udev mounts it so startup disk creator wont write to it , it will however erase the disk but then udev immediately remounts it , if I unmount the disk by selecting safely remove then udev immediately remounts it , if I unmount the drive by selecting "eject" it dissapears and startup disk creator does not see it . 2 hours of chasing my tail and I booted into my mangy install and made a startup disk with no problem .

---

### Post by cariboo on 2010-12-05
I created 4Gb of persistent space, but is wasn't used when I enabled 3D, I have to re-install libgl1-mesa-dri-experimental every time I boot from the live USB key. The way to get around that would be, to do an install to my usb key.

---

### Post by C.S.Cameron on 2010-12-05
Testing with a full install to flash drive would be the way to go for testing Natty.
It is the same as running from hard drive except for speed.
Nvidia drivers work and you can use update and upgrade,  Even upgrading versions work.
4GB is the minimum size for Ubuntu but the more the better.

---

### Post by Vorian on 2010-12-05
I always always always run out of room with a usb stick.  For the price of a large one, you could buy a "testing" HDD

---

### Post by plun on 2010-12-05
> **cariboo907 said:**
> I created 4Gb of persistent space, but is wasn't used when I enabled 3D, I have to re-install libgl1-mesa-dri-experimental every time I boot from the live USB key. The way to get around that would be, to do an install to my usb key.

Well... it works but I must also delete the casper-rw file on the FAT32 partition

I followed this:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

> To make the persistence larger (> 4GB), while still on your normal Ubuntu Installation, mount the pendrive if it is not mounted already. View the files in the FAT32 partition of the pendrive. You will now be able to see a file called casper-rw. It will be the same size as the value set on the slider. **Delete this file**. Open gparted >>>  See URL

It gives me a persistant drive.... but all updates including a initramfs fails...:---)

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.37-7-generic
[B]cryptsetup: WARNING: failed to detect canonical device of aufs
cryptsetup: WARNING: could not determine root device from /etc/fstab
cp: cannot stat `/vmlinuz': No such file or directory[/B]
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for python-support ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-support ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Down to "Method 1"...... but !

> Failure to do this will cause the GRUB on your hard disk to be changed and render the system unbootable from the hard disk, requiring you to boot from a CD and reinstall GRUB to the hard disk (possibly requiring a chroot to the hard disk filesystem first).

Time for a breakage maybe...;)

---

### Post by isaacahloe on 2010-12-05
i'm having the same problems with upgrading/updating. i can't get the nvidia driver to work. i don't think it will without initramfs working/updating

---

### Post by jerrylamos on 2010-12-05
> **whiprush said:**
> Hi everyone,

I've started this wiki page on how to create your own persistent Natty USB key so you can test and file bugs on Natty without having to break your existing computer:

[https://wiki.ubuntu.com/Unity/InstallUSBKey](https://wiki.ubuntu.com/Unity/InstallUSBKey)

Feel free to update the instructions if you find they are missing bits or if something is too complicated.

USB is a 33 GB hard drive.

Followed your instructions to the letter, I think.

Created 4 GB persistence file, the most allowed.

It's not persistent.

When I boot, it says "Try Ubuntu......or Install" so I do the "Try..."

Nothing remains of the previous boot.

I tried all the Function Key help notes and didn't see a thing,

?

Not much use without persistence.

BTW, what's that big fat panel on the left using up nearly an inch of my screen and how do I get rid of it?

Thanks, Jerry

---

### Post by C.S.Cameron on 2010-12-05
> **jerrylamos said:**
> USB is a 33 GB hard drive.

Followed your instructions to the letter, I think.

Created 4 GB persistence file, the most allowed.

It's not persistent.

When I boot, it says "Try Ubuntu......or Install" so I do the "Try..."

Nothing remains of the previous boot.

I tried all the Function Key help notes and didn't see a thing,

?

Not much use without persistence.

BTW, what's that big fat panel on the left using up nearly an inch of my screen and how do I get rid of it?

Thanks, Jerry

You could check that the casper-rw file exists and that text.cfg file has the word " persistence" in it.

---

### Post by rogerdean on 2010-12-06
Thanks CS

I have the same symptoms as jerrylamos. casper-rw does exist and the contents of txt.cfg is -

```
default live
label live
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
label live-install
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
label check
menu label ^Check disc for defects
kernel /casper/vmlinuz
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
menu label Test ^memory
kernel /install/mt86plus
label hd
menu label ^Boot from first hard disk
localboot 0x80
```

Any suggestions?
Cheers

---

### Post by C.S.Cameron on 2010-12-06
You can make a new ext2, 3 or 4 partition using gparted and name it casper-rw,
Or you can get a casper-rw generator from pendrivelinux.com and drop the casper-rw file into the usb root.
A Partition named home-rw will make a seperate home partition also.

Your text.cfg file looks ok.

---

### Post by rogerdean on 2010-12-06
Thanks CS. I think I'll come back at alpha2...

---

### Post by castrojo on 2010-12-06
Ok so I made a USB key and I'm going to try to install onto another USB key to see if I can then boot off of that and then be able to add nvidia drivers, etc.

Anyone ever try this before? The installer maintainer tells me that it should be totally possible and it should work.

---

### Post by ronacc on 2010-12-06
I never tried a usb key to usb key install but I have done usb key to SD card and CD to both usb key and sd card installs on my EEE . so I don't see why key to key wouldn't work .

---

### Post by cariboo on 2010-12-06
I'm in the process of doing it right now, but for some reason, it's taking a fairly long time.

I'll have to check to see if USB 2 got disabled in the bios, on the system I'm using to do it.

---

### Post by Framli on 2010-12-06
I have an on-key install. Which is great but write operations are rather slow. Good idea to check the bios for usb2.

---

### Post by KegHead on 2010-12-06
Hi!

A question about grub.

On upgrades I'm asked to make changes to grum on my hd and key.

Any suggestions/help?

Other than that, it's running smooth on a mini 9.

KegHead

---

### Post by cariboo on 2010-12-06
what kind of changes to grub?

---

### Post by KegHead on 2010-12-06
Hi!

I don't recall, but I'm asked to make changes to my hd or usb pen.

I'v indicated to change my usb pen.

I'll post on my next update/upgrade.

Thank you for your reply.

KegHead

---

### Post by cariboo on 2010-12-06
I'm running from an 8Gb thumb drive on another system. I used Friday's Live CD to create it. I enabled the nvidia restricted drivers first thing, rebooted and started Unity. It's now in the process of doing updates, with no problems so far.

---

### Post by KegHead on 2010-12-06
Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; The grub-pc package is being upgraded.  This menu allows you to select      
 &#9474; which devices you'd like grub-install to be automatically run for, if       
 &#9474; any.                                                                        
 &#9474;                                                                             
 &#9474; It is recommended that you do this in most situations, to prevent the       
 &#9474; installed GRUB from getting out of sync with other components such as       
 &#9474; grub.cfg or with newer Linux images it will have to load.                   
 &#9474;                                                                             
 &#9474; If you're unsure which drive is designated as boot drive by your BIOS,      
 &#9474; it is often a good idea to install GRUB to all of them.                     
 &#9474;                                                                             
 &#9474; Note: It is possible to install GRUB to partition boot records as well,     
 &#9474; and some appropriate partitions are offered here.  However, this forces     
 &#9474; GRUB to use the blocklist mechanism, which makes it less reliable, and      
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by KegHead on 2010-12-06
Package configuration






                &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                &#9474; GRUB install devices:                       &#9474; 
                &#9474;                                             &#9474; 
                &#9474;    [ ] /dev/sda (15434 MB, STT_FEM16GHDL)   &#9474; 
                &#9474;    [ ] /dev/sdb (2019 MB, Transcend_2GB)    &#9474; 
                &#9474;                                             &#9474; 
                &#9474;                                             &#9474; 
                &#9474;                   <Ok>                      &#9474; 
                &#9474;                                             &#9474; 
                &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by jerrylamos on 2010-12-06
> **C.S.Cameron said:**
> You could check that the casper-rw file exists and that text.cfg file has the word " persistence" in it.

Yes there is a casper-rw, /cdrom/casper-rw 4G large.

There isn't any text.cfg in the system.

There is a /cdrom/syslinux/txt.cfg which has:

```
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
```

however the word "persistent" does not show up on when I do F6 on "Try Ubuntu...." so I put it in manually when I booted.

Hmmm.  Now to reboot....

Finally got persistent.  wiki ubuntu USB persistent said to:
sudo gparted
resize the partition down
create a new partition
format to ext4
label casper-rw
apply...

Basically the Gnome System Administration Startup Disk Creator does not generate a workable casper-rw partition.  It did put a 4G file in the root named casper-rw, however usb natty couldn't use it, and Lucid LTS from hard drive said unknown format.

Jerry

---

### Post by Arrowstar on 2010-12-06
> **Framli said:**
> I have an on-key install. Which is great but write operations are rather slow. Good idea to check the bios for usb2.

I had a clean Maverick install on an 8 GB USB drive.  It was essentially out-of-the-box with the exception of nVidia drivers.  I decided to upgrade it to Natty to play around with the new Unity interface.  Slow does not describe it... the upgrade is ~300 MB of new packages, and I started it this morning around 9 AM.  It's now almost 6 PM and the upgrade has not finished yet.  Needless to say, bring some :popcorn:. :D

---

### Post by jerrylamos on 2010-12-06
> **jerrylamos said:**
> Yes there is a casper-rw, /cdrom/casper-rw 4G large.

There isn't any text.cfg in the system.

There is a /cdrom/syslinux/txt.cfg which has:

```
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
```

however the word "persistent" does not show up on when I do F6 on "Try Ubuntu...." so I put it in manually when I booted.

Hmmm.  Now to reboot....

Jerry

Nope.  Not persistent.  Only thing that persisted is changes to /cdrom/syslinux/txt.cfg.  They do show up when I boot, but nothing else is preserved.

Shot enough time on this.  

Cheers, Jerry

---

### Post by C.S.Cameron on 2010-12-06
> **whiprush said:**
> Ok so I made a USB key and I'm going to try to install onto another USB key to see if I can then boot off of that and then be able to add nvidia drivers, etc.

Anyone ever try this before? The installer maintainer tells me that it should be totally possible and it should work.

I've done this but not with Natty, with grub2 you end up with the first pendrive on the boot menu as well as whatever other hard disks on the computer have O/s's.

---

### Post by ocean223 on 2010-12-06
Just did it on a Mini9, It works. Suggest you remove the SSD though. Had to boot three times. Finally got display to work. (Maybe I'm impatient.)
Changed com-biz settings to ahhhhhhhh the middle one.

---

### Post by KegHead on 2010-12-07
Hi!

Downloaded upgrades today w/no problems.

Does anyone know where the auto-hide function is to disable unity?

I have a mini 9 with limited real estate on the screen.

Thanks!

KegHead

---

### Post by castrojo on 2010-12-07
> **C.S.Cameron said:**
> I've done this but not with Natty, with grub2 you end up with the first pendrive on the boot menu as well as whatever other hard disks on the computer have O/s's.

Thanks for the tip, I had already ran into it and had to fix my grub menu. My USB->USB install ended up not working, but I haven't had time to investigate yet.

---

### Post by cariboo on 2010-12-07
I built a USB drive using the Natty iso on a dvd, It took a fairly long time when it came to doing the update, but it did complete sucessfully. Running from the USB device isn't as fast as running from the hard drive, but it is usable.

Grub still lists the partitions from the system I installed from, but a bit of editing should fix that.

---

### Post by JeyPeyy on 2010-12-08
Mine won't boot. I waited for 10 minutes, should I really wait more than that long for it to boot? My computer isn't THAT old. It's from 2008 I think. It has an Intel Core 2 duo (two cores @ 3GHz) and 2 GB memory.

I know it's not supposed to be as fast as a normal installation, but I have never experienced a boot this slow from a live USB before.

I've checked md5sum.

---

### Post by KegHead on 2010-12-08
Wow!

My mini 9 w/atom processor fires up quickly.

How did you create your key?

KegHead

---

### Post by ronacc on 2010-12-08
did a usb key to usb key install , only problem I ran into was when I installed there were 2 usb keys plugged into the box and when I booted the install there was only 1 so the drive letter designation was one "too high" corrected that in grub.cfg and it booted fine and retained the nvidia driver and other things I installed on reboot , I installed grub to the usb key and used bios to set boot order to usb first so that it didn't mess with my regular grub since I'm just using the usb to check daily's . It is kind of slow , a boot from usd or sd card is not that slow on my EEE which has much lower spec's than my desktop .Unity is looking better , still not my cup of tea but thats just me .

---

### Post by KegHead on 2010-12-08
Jeypevy,

what size usb?

2gb is the minimum.

KegHead

---

### Post by JeyPeyy on 2010-12-08
4GB. I put 1GB as persistent.

---

### Post by ronacc on 2010-12-08
could be a bad "burn" one of the startupdisk creator installs I did was like that just a black screen after grub , reformated and redid it and it worked fine .

---

### Post by KegHead on 2010-12-08
Hi!

I would reformat and follow the #1 post.

KegHead

---

### Post by JeyPeyy on 2010-12-08
I get all the way to plymouth, but it just seems to load forever. I just reformated and followed post 1, but it still won't work. Maybe it has a problem with recognizing some of my hardware. My hard drive is formated in a pretty special way. I have Ubuntu, Fedora and Windows installed on it. Ubuntu and Fedora shares the same home partition (though not the same user folder, it uses symlinks to one common folder so that it shares normal files but not configuration files).

---

### Post by ronacc on 2010-12-08
if you installed the iso to the usb key using startupdisk creator your HD setup shouldn't matter , it would be just like booting from the live cd your HD's arent even mounted .

---

### Post by cariboo on 2010-12-08
> **JeyPeyy said:**
> I get all the way to plymouth, but it just seems to load forever. I just reformated and followed post 1, but it still won't work. Maybe it has a problem with recognizing some of my hardware. My hard drive is formated in a pretty special way. I have Ubuntu, Fedora and Windows installed on it. Ubuntu and Fedora shares the same home partition (though not the same user folder, it uses symlinks to one common folder so that it shares normal files but not configuration files).

It may be a hardware problem, what graphics chipset do you have? I did a fresh install on my netbook last night, and with the latest daily build, I got a black screen on first boot. I restarted in recovery mode and selected failsafeX from the menu, which got me to the desktop, where I could update to the latest kernel, to fix the black screen problem. My system uses the Intel 945 chip set..

---

### Post by JeyPeyy on 2010-12-08
> **ronacc said:**
> if you installed the iso to the usb key using startupdisk creator your HD setup shouldn't matter , it would be just like booting from the live cd your HD's arent even mounted .

Oh, ok, I thought it was mounted on /media or something. 



[QUOTE=cariboo907]It may be a hardware problem, what graphics chipset do you have? I did a fresh install on my netbook last night, and with the latest daily build, I got a black screen on first boot. I restarted in recovery mode and selected failsafeX from the menu, which got me to the desktop, where I could update to the latest kernel, to fix the black screen problem. My system uses the Intel 945 chip set..[/QUOTE]

I have an ASUS GeForce 9600GT, which is the same thing as nVidia GeForce 9600GT only re-branded, if I'm not mistaken.  Again, I'm not getting a black screen, I get all the way to the loading screen (plymouth).

---

### Post by cariboo on 2010-12-08
Try starting with nomodeset enabled, at the startup screen press any key to get the menu, then press F6 and enable nomodeset in the menu press esc and enter, this is the replacement for safe mode. I've had to use it with different Nvidia cards over the years.

---

### Post by JeyPeyy on 2010-12-08
> **cariboo907 said:**
> Try starting with nomodeset enabled, at the startup screen press any key to get the menu, then press F6 and enable nomodeset in the menu press esc and enter, this is the replacement for safe mode. I've had to use it with different Nvidia cards over the years.

That didn't work. I got a different boot up screen with simple text on "ubuntu", but it wouldn't boot.

I tried the USB on my laptop, and it worked, so it's probably a hardware issue.

---

### Post by jerrylamos on 2010-12-08
cd build as of 12/08 still no persistent.  The boot line says persistent, there is a 4G casper-rw.  Create a test file, reboot, it's gone.

This is a 36 GB USB hard drive.

Is there any way to ask Natty if it thinks it is persistent?  What does it test?

Thanks, Jerry

---

### Post by C.S.Cameron on 2010-12-09
> **jerrylamos said:**
> cd build as of 12/08 still no persistent.  The boot line says persistent, there is a 4G casper-rw.  Create a test file, reboot, it's gone.

This is a 36 GB USB hard drive.

Is there any way to ask Natty if it thinks it is persistent?  What does it test?

Thanks, Jerry

This might be easier to trace if you delete your casper-rw file and create an ext3 partition to the right of the FAT32 Ubuntu partition and name it casper-rw.
Then you can check what is in it.
You can also mount the casper-rw file and have a look inside.
I usually change my desktop background to confirm persistence.

---

### Post by jerrylamos on 2010-12-09
> **C.S.Cameron said:**
> This might be easier to trace if you delete your casper-rw file and create an ext3 partition to the right of the FAT32 Ubuntu partition and name it casper-rw.
Then you can check what is in it.
You can also mount the casper-rw file and have a look inside.
I usually change my desktop background to confirm persistence.

The "startup disk creator" makes a casper-rw file that cannot be displayed or read: "Unknown format".

Your comment about creating another partition works.  I found that suggestion in [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent).

My opinion the usb startup disk creator in Natty does not create a persistent startup.  Maybe if I can shake some time loose I'll write a launchpad bug.

Thanks, Jerry

---

### Post by C.S.Cameron on 2010-12-09
> **jerrylamos said:**
> The "startup disk creator" makes a casper-rw file that cannot be displayed or read: "Unknown format".

Your comment about creating another partition works.  I found that suggestion in [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent).

My opinion the usb startup disk creator in Natty does not create a persistent startup.  Maybe if I can shake some time loose I'll write a launchpad bug.

Thanks, Jerry

Following to mount and edit the casper-rw file:

[http://ubuntuforums.org/showpost.php?p=7055983&postcount=2](http://ubuntuforums.org/showpost.php?p=7055983&postcount=2)

---

### Post by KegHead on 2010-12-09
Hi!

Upgrade/update went great today.

My 2 gb usb drive is almost out of room.

Any ideas?

KegHead

---

### Post by ronacc on 2010-12-09
heres an interesting problem , I have a couple of sandisk cruiser usb keys that have hidden partitions with some kind of windows crap on them , I can't deleted those partitions no mater what I try or delete the stuff in them . I hate to risk running dban on them brcause that would risk every other drive in the box and I'm too lazy to disconnect all of them , any Ideas ? gparted don't even see those partitions , ubiquity sees them if I try to install to that stick and claims it is going to format them but then doesn't and then fails trying to install grub to a write protected partition so I need to get rid of them .

---

### Post by KegHead on 2010-12-09
Hi1

this is on my 2 gb usb drive any way to free up room?

---

### Post by cariboo on 2010-12-09
<offtopic>

Just a hint when taking screen shots, set the delay to more than 0 secs, then you won't see  the screenshot application screen.

</offtopic>

---

### Post by matt_symes on 2010-12-09
Hi

> Ideas ? gparted don't even see those partitions , ubiquity sees them if I  try to install to that stick and claims it is going to format them but  then doesn't and then fails trying to install grub to a write protected  partition so I need to get rid of them .If it's anything like my western union hard drive then it is protected by the firmware and cannot be deleted. The only thing i could do on that was disable it (the software on it) via a firmware update. Irritating.

I have no idea if it the same for a pen drive, but if you find out please post back here because i also have a sandrive pen drive. Maybe i'll try on mine. If i do i will post back the results.

Kind regards

---

### Post by ronacc on 2010-12-09
I couldn't do it under linux but it can be done under windows or you can get an application from sandisk for a Mac that will do it , I took the Mac option since I don't do windows .check the sandisk support site for info .

---

### Post by C.S.Cameron on 2010-12-09
> **KegHead said:**
> Hi1

this is on my 2 gb usb drive any way to free up room?

A 2GB persistent USB does not have much room to free up.
You could try mounting casper-rw file and deleting stuff out of it.

---

### Post by jerrylamos on 2010-12-10
> **C.S.Cameron said:**
> A 2GB persistent USB does not have much room to free up.
You could try mounting casper-rw file and deleting stuff out of it.

Don't update.  Download a new CD Build every so often and make a new USB install.  Of course you then have to do your personalization etc. all over again.  I have a partition on the hard drive with all the stuff I use to get going again.

I conclude Ubuntu must be doing as much testing as they want without making CD images available for all of us.  There's got to be something they can omit to make the image fit, example omit Open Office which can be downloaded after the CD is booted.  I use Open Office Write all the time but there's a whole lot of testing I can do without it, and load it if needed.

Jerry

---

### Post by ronacc on 2010-12-10
or it could be they can't  make a cd image that will boot to a useable desktop right now .

---

### Post by KegHead on 2010-12-10
Hi C.S. Cameron!

Which files in casper can be deleted?

Thanks!

BTW-It looks like today's upgrade freed up some room on my 2gb drive.

KegHead

---

### Post by enigmageek on 2010-12-13
Hello. I have a handful of Sandisk Cruzers with the U3 partition. I ran the U3 program in W.I.N.E. and told it to delete itself. The you can use Palimsest a.k.a. gnome-disk-utlity to format/partition it. I'm running on Maverick on a Cruzer with all my updates and personal settings :)

---

### Post by enigmageek on 2010-12-13
Hello. Have you tried apt-get autoremove and apt-get clean? After installation and upgrades the apt cache holds the packages. My sticks are 2 GiG and I dedicated 1 GiG to personal persistent data. Good luck.

---

### Post by KegHead on 2010-12-13
Hi1

So far update/upgrade running ok. It looks like the process has deleted some files to free up room.

BTW-does anyone know what cryptsettup is?

Thanks!

KegHead

---

### Post by efflandt on 2010-12-13
Is persistence working from USB iso yet?  I didn't even notice that it did not work in natty alpha until I did this:

```
efflandt@natty-ssd:~$ ls /media
1C23-10CF  vdisk
efflandt@natty-ssd:~$ sudo mount -o loop /media/1C23-10CF/casper-rw /media/vdisk
efflandt@natty-ssd:~$ grep DISKNAME /media/1C23-10CF/README.diskdefines
#define DISKNAME  Ubuntu 11.04 "Natty Narwhal" - Alpha amd64
efflandt@natty-ssd:~$ ls /media/vdisk
lost+found
```I did notice it when I tried Kubuntu natty iso on USB because codecs I tried to install were not there next boot.

So currently I have Ubuntu natty on SSD and Kubuntu natty regular install on a cheap 8 GB USB.  SSD updates fly, but for USB flash updates, you might as well go take a nap, because it is going to take awhile (significantly more than 10 times longer).

---

### Post by jerrylamos on 2010-12-13
> **efflandt said:**
> Is persistence working from USB iso yet?  I didn't even notice that it did not work in natty alpha until I did this:

```
efflandt@natty-ssd:~$ ls /media
1C23-10CF  vdisk
efflandt@natty-ssd:~$ sudo mount -o loop /media/1C23-10CF/casper-rw /media/vdisk
efflandt@natty-ssd:~$ grep DISKNAME /media/1C23-10CF/README.diskdefines
#define DISKNAME  Ubuntu 11.04 "Natty Narwhal" - Alpha amd64
efflandt@natty-ssd:~$ ls /media/vdisk
lost+found
```I did notice it when I tried Kubuntu natty iso on USB because codecs I tried to install were not there next boot.

So currently I have Ubuntu natty on SSD and Kubuntu natty regular install on a cheap 8 GB USB.  SSD updates fly, but for USB flash updates, you might as well go take a nap, because it is going to take awhile (significantly more than 10 times longer).

I've got my personalization on another partition and am pretty used to getting it up and running.

So periodically I do an rsync update from CD Daily Build, make a new install either on a spare partition or USB, then do my personalization.

USB is persistent by making a second partition on the USB with gparted and labelling it casper-rw.

Have fun, Jerry

p.s. natty hasn't bee breaking much (yet) so I've been doing a bit of tinycore linux on the side....

---

### Post by KegHead on 2010-12-14
Hi!

Upgrade went smooth today.

Installed bleach bit to clear up files-worked great.

KegHead

---

### Post by KegHead on 2010-12-15
Ditto yesterday.

Any other success stories?

Do you think it's too early to install on my ssd?

KegHead

---

### Post by jerrylamos on 2010-12-15
> **KegHead said:**
> Ditto yesterday.

Any other success stories?

Do you think it's too early to install on my ssd?

KegHead

I'm running Natty on four test systems updating every couple days or so.  A problem I've hit after update on a couple of the pc's is booting and gnome-desktop does not appear.  Sometimes I can get it going with 
Ctrl-Alt-T 
gnome-desktop &
sometimes not.  Then I boot in recovery mode and do a fix broken packages and try to boot again.  Hopefully.

Based on previous Ubuntu's at this stage I'd expect update to make the partition unusable a few times, and even after Beta.

I'm in it looking for bugs.  All the pc's are multiboot Lucid, Meerkat, Natty, Lubuntu, tiny core, slitaz, Debian, ... so I can boot something or other and my data is backed up.  I hope.

Jerry

---

### Post by vishnu on 2010-12-16
I went ahead and made a USB Key install of Natty.  Boots fine but and I allocated 200MB of storage for saving data.  Is there a way to keep system config saved from one boot to the next?  Would be nice t be able to configure my desktop and look and feel the way I want it and have that saved for the next boot.

---

### Post by C.S.Cameron on 2010-12-16
> **vishnu said:**
> I went ahead and made a USB Key install of Natty.  Boots fine but and I allocated 200MB of storage for saving data.  Is there a way to keep system config saved from one boot to the next?  Would be nice t be able to configure my desktop and look and feel the way I want it and have that saved for the next boot.

The "Stored in reserved extra space" option of Startup disk creator should be saving your system config from one boot to the next.
Some people seem to be having problem with the casper-rw file.
Delete it, shrink the FAT32 partition with gparted and create a new ext2, 3 or 4 partition and name it casper-rw.
Several people have reported that this fixes persistence.

---

### Post by vishnu on 2010-12-16
Excellent. Thanks - I'll give it a go.

---

### Post by KegHead on 2010-12-16
Hi!

Huge upgrade today.

Only change that I can see:

1. I'm asked for a password...do I need to have one or is there a work around?

Thanks!

Keghead

---

### Post by C.S.Cameron on 2010-12-16
> **KegHead said:**
> Hi!

Huge upgrade today.

Only change that I can see:

1. I'm asked for a password...do I need to have one or is there a work around?

Thanks!

Keghead

I think when it starts asking for a password something is broken.

---

### Post by cariboo on 2010-12-16
I ran into a situation where I needed a password, I used **ubuntu** with no password.

---

### Post by shuttleworthwannabe on 2010-12-17
Hi there I am posting from USB with persistent install; this is what I did:

1. I have Ubuntu installed (in this case I have Ubuntu 11.04 Alpha daily 16-12-2010) on hard drive on another test machine; not sure if this is necessary or you could do the USB install via a live CD running on machine. I downloaded a new ISO from the daily cdimage and saved on hard drive.

2. I launched USB creator, and pointed to the ISO I had downloaded earlier.

3. Inserted the USB, and formatted it using the tool
4. Created a persistence of about 4GB (max on my 8GB USB stick). Completed the installation. took about 10 mins or so.


 persistence will not work yet. You will have to do this to make it work:
1. Remove the USB install after step #4 above; and reinsert in the machine with the Ubuntu HDD install; 
2. Delete casper-rw on the USB (yes nothing will happen to the USB install)
3. Then fireup gparted and resize and format a new partition on the USB--I did 4GB in ext2 (logical); label it casper-rw. all should go smoothly. remove the USB safely.
5. Now test the USB install on another machine. I tested the USB install on my Dell Vostro 3700;

it has 2 hardware issues: broadcom wireless and nvidia graphics. When I booted from USB on this Dell, it went fine, but landed on "classic desktop" because of "...no 3d...". I then installed the nvidia drivers from hardware install (popped up on its own)--this was a big mistake in retrospect, because as you will see later, it conflicts with the 'experimental" driver which is the proper driver for graphic and 3D to use Unity desktop.
Make sure you have a live internet connection via ethernet cable. You can try and install the broadcom drivers from the restricted drivers pop up--it worked for me, but gave me an "system error..."--not sure what this was, but when I rebooted into the USB, my wireless card worked fine.

then do to synaptic and check universe in the repository. search for libgl1-mesa-dri-experimental and install this. Restart into the USB. (Note: I had to completely remove all traces of nvidia drivers I had installed earlier)

This time, all should be working: Persistence, Wireless, and 3d-desktop, Unity comes on by default.

Hope this experience helps others.

Thanks
S

---

### Post by KegHead on 2010-12-17
Hi!

Another huge upgrade today.

No issues.

No request for password.

KegHead

---

### Post by ErikNJ on 2010-12-17
> **shuttleworthwannabe said:**
> Hi there I am posting from USB with persistent install; this is what I did:

1. I have Ubuntu installed (in this case I have Ubuntu 11.04 Alpha daily 16-12-2010) on hard drive on another test machine; not sure if this is necessary or you could do the USB install via a live CD running on machine. I downloaded a new ISO from the daily cdimage and saved on hard drive.

2. I launched USB creator, and pointed to the ISO I had downloaded earlier.

3. Inserted the USB, and formatted it using the tool
4. Created a persistence of about 4GB (max on my 8GB USB stick). Completed the installation. took about 10 mins or so.


 persistence will not work yet. You will have to do this to make it work:
1. Remove the USB install after step #4 above; and reinsert in the machine with the Ubuntu HDD install; 
2. Delete casper-rw on the USB (yes nothing will happen to the USB install)
3. Then fireup gparted and resize and format a new partition on the USB--I did 4GB in ext2 (logical); label it casper-rw. all should go smoothly. remove the USB safely.
5. Now test the USB install on another machine. I tested the USB install on my Dell Vostro 3700;

it has 2 hardware issues: broadcom wireless and nvidia graphics. When I booted from USB on this Dell, it went fine, but landed on "classic desktop" because of "...no 3d...". I then installed the nvidia drivers from hardware install (popped up on its own)--this was a big mistake in retrospect, because as you will see later, it conflicts with the 'experimental" driver which is the proper driver for graphic and 3D to use Unity desktop.
Make sure you have a live internet connection via ethernet cable. You can try and install the broadcom drivers from the restricted drivers pop up--it worked for me, but gave me an "system error..."--not sure what this was, but when I rebooted into the USB, my wireless card worked fine.

then do to synaptic and check universe in the repository. search for libgl1-mesa-dri-experimental and install this. Restart into the USB. (Note: I had to completely remove all traces of nvidia drivers I had installed earlier)

This time, all should be working: Persistence, Wireless, and 3d-desktop, Unity comes on by default.

Hope this experience helps others.

Thanks
S

I will give this a shot myself.  I think it's super important that Natty testing be performed with the proprietary NVidia drivers in addition to nouveau-experimental.

For example, in another distro, I had major performance issues with the NVidia driver due to its interaction with cairo (and how the new cairo renders gradients).  However, There was no issue at all when using nouveau-experimental.  I'd hate to see this overlooked in Natty testing due to the use of nouveau only.

Anyway, it'd be kinda' nice if testing drivers while remaining on a USB drive were a bit easier to do.

---

### Post by cariboo on 2010-12-17
I think you'll find if you do a quick survey, that more of us are using nvidia-current, than nouveau, out of 4 of my system with nvidia cards, 3 are running the restricted drivers, and 1 nouveau.

---

### Post by KegHead on 2010-12-18
Hi!

Ditto other posts!

Still see no need for unity, at least on my mini 9.

Maybe for my desktop.

KegHead

---

### Post by jerrylamos on 2010-12-18
> **KegHead said:**
> Hi!

Ditto other posts!

Still see no need for unity, at least on my mini 9.

Maybe for my desktop.

KegHead

On my desktops I run linux for applications.  Unity takes an inch of the screen for hieroglyphics.  No thanks.  I fill my screen with applications I don't need redundant pictures hogging space.

Even little tiny core covers up their hieroglyphics when I run applications.  If there's a way to cover up Unity I haven't found it.  So I run classic.

Jerry

---

### Post by Framli on 2010-12-18
What about autohide?

---

### Post by KegHead on 2010-12-18
Hi!

From what I read Alpha 2 will have autohide.

Please correct me if I'm wrong.

KegHead

---

### Post by matt_symes on 2010-12-18
Well i hope alpha 2 is better than alpha 1. I can't even get Unity and it's not from want of trying. I feel like i'm missing all the fun.

---

### Post by Framli on 2010-12-18
Thank you KegHead, I'm already using it (you can activate it via ccsm). The autohide post was directed at jerrylamos :

> **jerrylamos said:**
> On my desktops I run linux for applications.  Unity takes an inch of the screen for hieroglyphics.  No thanks.  I fill my screen with applications I don't need redundant pictures hogging space.
Even little tiny core covers up their hieroglyphics when I run applications.  If there's a way to cover up Unity I haven't found it.  So I run classic.
Jerry

---

### Post by KegHead on 2010-12-18
Hi Matt,


Did you download from post #1?

Any upgrade problems?

If so, go a head and re download.

Should solve your problem.

KegHead

---

### Post by jerrylamos on 2010-12-19
> **matt_symes said:**
> Well i hope alpha 2 is better than alpha 1. I can't even get Unity and it's not from want of trying. I feel like i'm missing all the fun.

Matt, as far as I can tell Unity is "blacklisted" from most of the integrated video graphics.  

At the moment it's also broken on ati radeon on CD Live.

If you like lots of "eye candy" try Kubuntu.

Right now for this posting I'm using Tiny Core which does an automatic autohide no extra code required.  I get to use the whole screen for applications.  Tiny Core is very limited on function which is why I use Ubuntu mostly.

On the topic of this thread, I did get "Oversized"  Natty running on a 40 gigabyte USB hard drive persistent by using a separate partition labelled casper-rw.  The ubuntu procedure creates a bootable USB but I had to manually create the persistent partition with gparted.

Jerry

---

### Post by matt_symes on 2010-12-19
> Matt, as far as I can tell Unity is "blacklisted" from most of the integrated video graphics. 

Thankyou. That would explain alot.

EDIT: Already have Kubuntu :)


matthew@matthew-laptop:~$ sudo blkid
/dev/sda1: LABEL="System_restore_win7" UUID="DAA41C49A41C2B11" TYPE="ntfs" 
/dev/sda2: LABEL="Windows_7_boot" UUID="921C18621C18441F" TYPE="ntfs" 
/dev/sda3: LABEL="Windows_7" UUID="A2984D43984D1767" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu_10.04" UUID="3d48429c-7361-4ab8-8689-54407673b141" TYPE="ext4" 
/dev/sda6: UUID="b1c6171a-075e-4291-af69-64baf751d10e" TYPE="swap" 
/dev/sda7: LABEL="OpenSuse" UUID="56a4c951-b189-45cb-91e6-76c83b765044" TYPE="ext4" 
/dev/sda8: LABEL="Natty" UUID="8db60ccd-ec5d-44cc-bdff-b640e4c1fdc1" TYPE="ext4" 
/dev/sda9: LABEL="Fedora-14" UUID="3d35b416-3b1b-467d-892c-ac2095c0ab18" TYPE="ext4" 
/dev/sda10: LABEL="Arch_Linux" UUID="6aa72302-2b4f-432c-953a-33c7513bfa47" TYPE="ext4" 
/dev/sda11: LABEL="Kubuntu 10.10" UUID="4be47bac-e107-4068-b31b-fc5452f2f2a3" TYPE="ext4" 
/dev/sda12: UUID="ef9ae3cc-e084-4664-bf0e-ae9bac39dace" TYPE="ext4" 
/dev/sda13: UUID="f8dc5390-f494-4963-95ee-c27ecbf4fea1" TYPE="ext4" 
matthew@matthew-laptop:~$

EDIT2: Sorry for the off topic reply on this thread

---

### Post by meborc on 2010-12-20
in the wiki and in this thread many people have mentioned that this kind of setup would be much slower then the real install

I understand that this is mainly due to the nature of USB, but what about USB 3.0 ? :) Has someone tested running ubuntu from USB 3.0 stick with compatible computer?

Would be interesting to know...

---

### Post by jerrylamos on 2010-12-21
> **meborc said:**
> in the wiki and in this thread many people have mentioned that this kind of setup would be much slower then the real install

I understand that this is mainly due to the nature of USB, but what about USB 3.0 ? :) Has someone tested running ubuntu from USB 3.0 stick with compatible computer?

Would be interesting to know...

USB is slower however plenty fast enough to get into Unity trouble on boot.

Another choice is to make a 1 gb partition and mount the iso image there.  It's faster than USB but slower than regular installation.  I'm doing than on my IBM Thinkpad ati radeon where Natty A1 boots to a splotchy purple screen and a cursor.  That's it.  When the CD live mounted on the 1 gb partition will work I'll try install, multiboot of course.  Oversize is no problem for that setup.

Jerry

---

### Post by KegHead on 2010-12-22
Hi!

I'm out of the country until next year!

I'll resume testing next year!

Happy Holidays!

KegHead

---

### Post by Mobidoy on 2010-12-22
> **jerrylamos said:**
> USB is slower however plenty fast enough to get into Unity trouble on boot.

Another choice is to make a 1 gb partition and mount the iso image there.  It's faster than USB but slower than regular installation.  I'm doing than on my IBM Thinkpad ati radeon where Natty A1 boots to a splotchy purple screen and a cursor.  That's it.  When the CD live mounted on the 1 gb partition will work I'll try install, multiboot of course.  Oversize is no problem for that setup.

Jerry

You have somewhere to point me to do that ISO mounting procedure ?

---

### Post by Quackers on 2010-12-23
I made a Natty usb key but it doesn't boot :-(
I am just getting the flashing cursor at top left. Bootloader problem?
Here's a screenshot of what's on the key, is anything missing? 
I used the startup disc creator - did I do something wrong?
Thanks.

---

### Post by jerrylamos on 2010-12-23
> **Mobidoy said:**
> You have somewhere to point me to do that ISO mounting procedure ?
I'm using the iso on hard drive partition setup to test Natty on my IBM Thinkpad T40.  Compiz does something that doesn't work on ati radeon mobility 7500 and so far Compiz developers haven't fixed it, so I try every day to see if the next daily build will work. It's a mess really since Ubuntu natty persists in trying to boot CD live Unity whether it will run or not, and some fancy stuff has to be done to get classic running.

I use "rsync" which downloads the differences between the iso I have and the new build.

To boot iso from a hard drive partition:
-- Use gparted to make a partition, I do 1 gb in size.  Usual gparted cautions here, don't mess up.  Format ext3 and label so it will show up on "Places" file viewer reasonably.  I used "Live".
-- I code an exec as follows for putting the iso on partiton 6.  Caution here, don't mess up any other partition!
In whatever folder you have the .iso:
```

gedit Live6
#! /bin/bash
mkdir /tmp/install_cd
sudo mount natty-desktop-i386.iso -o loop /tmp/install_cd
sudo mkdir /mnt/installer
# ACHTUNG!  Make sure the /dev/sda is the intended partition!
sudo mount /dev/sda6 /mnt/installer
sudo cp -rv /tmp/install_cd/* /mnt/installer
sudo cp -rv /tmp/install_cd/.disk /mnt/installer
sudo umount /tmp/install_cd
exit #
save
quit
sudo chmod 777 Live6
./Live6
```
takes a little while.  A bunch of files get put on the partition.
Now create an entry for Grub2.  For ramdisk I think it has to be at least maybe 128k I'm not sure.  I've got lots of memory so I haven't tested.
```

sudo gedit /etc/grub.d/06_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above
sudo gedit /etc/grub.d/06_custom
menuentry "Live natty on sda6" {
set root=(hd0,6)
linux /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=384000 ro quiet
initrd /casper/initrd.lz
}
exit #
save
quit
sudo chmod 777 /etc/grub.d/06_custom
sudo update-grub
```
Reboot and the grub menu should list the live entry first.  If you'd rather it were last, then use 40_custom instead of 06_custom.

Now if you want persistence, you could try to live partition:
sudo touch /media/Live/casper/casper-rw
reboot with "persistent" in the linux line.  I haven't tried it.

For the next day's iso, I do rsync then the Live6 exec above.

Natty CD Live still busted on 20101223.  Only thing that works is Ctrl-Alt-F1 and the various suggestions in the forums to get classic mode from there.

Have fun, Jerry

---

### Post by KegHead on 2011-01-06
Hi!

Back to testing today.

Download w/no problems.

KegHead

---

### Post by tjeremiah on 2011-01-07
Last night I finally figured it out how to save my settings on the USB. But I have a question. Is there a way to bypass the WELCOME "Try Ubuntu" "Install Ubuntu" screen when first booting up?

---

### Post by KegHead on 2011-01-07
Hi!

I think a permanent install is the only way.

Please correct me if I'm in error.

KegHead

---

### Post by tjeremiah on 2011-01-07
> **KegHead said:**
> Hi!

I think a permanent install is the only way.

Please correct me if I'm in error.

KegHead

so its normal to see the welcome screen I guess when you do persistent then. I thought I was the only one seeing the welcome screen after an update. I guess its normal but I wish you can boot right to the desktop.

---

### Post by KegHead on 2011-01-07
Hi!

It's there to give option for just a peek or to install etc.

KegHead

---

### Post by KegHead on 2011-01-08
Bonjour!

Same old same old.

I read Banshee is going to be the default mp.

Any updates?

KegHead

---

### Post by Harry33 on 2011-01-08
> **KegHead said:**
> Bonjour!

Same old same old.

I read Banshee is going to be the default mp.

Any updates?

KegHead

More info on banshee and mono  here:
[http://ubuntuforums.org/showthread.php?t=1661772](http://ubuntuforums.org/showthread.php?t=1661772)

---

### Post by KegHead on 2011-01-08
Hi!

It looks like banshee.

Thanks!

KegHead

---

### Post by onemanclapping on 2011-01-17
I'm having a problem:

I created a Startup USB stick with Natty using usb-creator-gtk and adjusting the persistence to 2GB (my stick is 4GB).

First weird thing: when I booted, I only had 380MB of free space on the stick.

Second weird thing: persistence doesn't work - I even tried saving a file at Home and it wasn't there after reboot.

I already tried different values for persistence, with no success.

Does anyone have any ideas, or is it just the blue Monday effect in my laptop? :P

I'm using Ubuntu 10.10 and a HP Mini 311.

---

### Post by jerrylamos on 2011-01-17
> **onemanclapping said:**
> I'm having a problem:

I created a Startup USB stick with Natty using usb-creator-gtk and adjusting the persistence to 2GB (my stick is 4GB).

First weird thing: when I booted, I only had 380MB of free space on the stick.

Second weird thing: persistence doesn't work - I even tried saving a file at Home and it wasn't there after reboot.

I'm using Ubuntu 10.10 and a HP Mini 311.


I used gparted to create two partitions on the USB stick.  The first partition is to put the usb image in.  The second one is labeled casper-rw and the usb seems to recognize it and use it for persistence.  The usb create makes a casper-rw file inside the first partition which doesn't seem to get used.

Now I also have a usb hard drive. I had a left over laptop hard drive with a very sick XP on it, so I bought one of the housings that connect to USB for it and formatted it for Linux.  Then I just plain flat used the Ubuntu CD Live to install a real Ubuntu on it.  It's about 38 GB and so far the oversized Ubuntu daily builds will fit....speed isn't bad either.

Jerry

---

### Post by onemanclapping on 2011-01-18
> **jerrylamos said:**
> I used gparted to create two partitions on the USB stick.  The first partition is to put the usb image in.  The second one is labeled casper-rw and the usb seems to recognize it and use it for persistence.  The usb create makes a casper-rw file inside the first partition which doesn't seem to get used.
Worked perfectly! But what's happening with the 'standard' procedure? I used to do that and it worked... Or is it a Natty issue?

Thanks Jerry!

---

### Post by cariboo on 2011-01-18
> **onemanclapping said:**
> Worked perfectly! But what's happening with the 'standard' procedure? I used to do that and it worked... Or is it a Natty issue?

Thanks Jerry!

It is an issue, and the devs are aware of it.

---

### Post by KegHead on 2011-01-19
Hi!

I'm no longer testing 11.04.

I'm actually looking at Mint for my Mini 9.

Maybe Debian.

I hope the Unity situation works out as I really love 10.10.

KegHead

---

### Post by jerrylamos on 2011-01-19
> **KegHead said:**
> Hi!

I'm no longer testing 11.04.

I'm actually looking at Mint for my Mini 9.

Maybe Debian.

I hope the Unity situation works out as I really love 10.10.

KegHead

I find logging in with "classic desktop no effects" on 11.04 Natty to be solid and capable.

Jerry

---

### Post by jerrylamos on 2011-01-20
Today's daily build is HUGE!  765 MB.  I loaded it into a 1 GB hard disk partition and booted it on IBM Thinkpad T40.  Complains I don't have the hardware for 3D acceleration, says "change session", and just sat there with wallpaper and cursor.

Re-booted specifying recovery mode by adding:
single
to the boot line.  Yay! came up with a couple icons, Examples and Install.  Then right clicked to get a launcher, so I made one with command
gnome-terminal
selected that, issued some command lines as in the thread "No Gnome panel" and got a top panel.  A bit screwed up but functional enough.
Selected the power switch applet, then did a logout/log in selecting ubuntu panel safe mode.
Up and working!

Now if only the "change session" would get me to the login screen so that I could change session sure would save a lot of hassle.

Anyway, bloated though it is, it's running!  (gnome-panel of course, the one that works)

Jerry

---

### Post by jerrylamos on 2011-01-20
Hmm.  I do a save post using the fat 765 MB CD Live, it never completes as far as the screen says, waiting for Ubuntu.  Instead it actually did do the save so I wound up with triplicates.

Could someone delete posts #129 and #130 however that is done?

Thanks, Jerry

---

### Post by jerrylamos on 2011-01-20
Dupe

---

### Post by KegHead on 2011-01-26
Hi!

Tried Mint-not interested.

Looking at Xubuntu 11.04--looks interesting!

KegHead

---

### Post by KegHead on 2011-02-11
Hi!

Tried Natty A2 todays build.

Had lots of problems. Compiz crashed on my atom based desktop.

Anyone else?

KegHead

---

### Post by jerrylamos on 2011-03-13
With 13 March Daily Build I'm getting "ubi-partman error code 141" so I entered a launchpad bug #734503.

Do note there are two hard drives and an external USB hard drive, each with several partitions including Lucid LTS, Maverick, Natty.  Maverick CD Live has no problem with this.  A couple times since A3 came out the Natty installer could get by the initial screen for looking at the partitions.  Most of the time it is broken like right now.

Jerry

---

### Post by cariboo on 2011-03-13
There already is a bug report for that exact same item [lpbug]730209[/lpbug]

---

### Post by jerrylamos on 2011-03-13
> **cariboo907 said:**
> There already is a bug report for that exact same item [lpbug]730209[/lpbug]

Yes, that's the error I have.  Since these are multiboot hard drives I'm not about to delete the running installs.  Ubiquity fails before even showing what partitions it did identify.  

Jerry

---

### Post by VMC on 2011-03-13
> **jerrylamos said:**
> Yes, that's the error I have.  Since these are multiboot hard drives I'm not about to delete the running installs.  Ubiquity fails before even showing what partitions it did identify.  

Jerry

Jerry, there's a way around it, but its convoluted. If you have a spare hard drive - or maybe a flash drive would work.

What I did was unplug the internal hard drive - making the BIOS disabled didn't work, then plug in the external hard drive with unallocated partitions. Then let ubiquity continue with manual install.I copied that partition over to my internal hard drive. [I said it was convoluted].

---

### Post by jerrylamos on 2011-03-14
> **cariboo907 said:**
> There already is a bug report for that exact same item [lpbug]730209[/lpbug]

Just running install up to the point of partman caused changes to the USB hard drive.  

It was my mistaken impression that it wouldn't change anything to just running install to see what it would list as partitions.  Install had not proceeded to the point of even showing the window with "Change" on it.

Wrong.  Grub 2 was altered on the USB hard drive.

It was a scramble to get a Maverick booted to straighten out the USB hard drive with update-grub and grub-install.

More of us could do more testing on Natty if it would install.  

Tail end of February I couldn't get install to work, a day or two in the beginning of March it did work so I quick installed on my test pc's and have been doing updates since.

It's going to be a long time before I try to test the install script on Natty again.

Jerry

---

### Post by KegHead on 2011-03-14
Hi!

I gave up on 11.04.

I'm going to try again1

KegHead

---

