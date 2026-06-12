---
title: "Two mounting questions"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by bjordan555 on 2009-11-06
I'm running 9.04. I have two related, but separably answerable mounting questions.  

Q1: I have a usb external hard drive mounted automatically at /media/usb0.  I'd like to change this to automatically mount to /media/DATADRIVE.  I am OK with this changing if I change my bus ordering.  I've tried to set this with MountManager, but it doesn't seem to stick, even after saving the configuration. What's the best way to do this?

Q2: I have network storage that's accessible through either webdav or SSH.  I'd like to have this mounted as a accessible directory in the local file system, so that, for example, I can save to this storage from within an appliction that doesn't let me navigate to /home/.gvfs. 

Thanks for any input,

Ben

---

### Post by Bunnybugs on 2009-11-06
At first, you can change the Hardware-adress of your USB-device @ the Partition Manager (System>Administration>Disk Utility)

And the second, I really don't know, sorry for that

---

### Post by pebo on 2009-11-06
For Q2, you can use [sshfs]("https://help.ubuntu.com/community/SSHFS") to mount your share to a mount point in your home directory.

---

### Post by MountainX on 2009-11-06
> **bjordan555 said:**
> I'm running 9.04. I have two related, but separably answerable mounting questions.  

Q1: I have a usb external hard drive mounted automatically at /media/usb0.  I'd like to change this to automatically mount to /media/DATADRIVE.  I am OK with this changing if I change my bus ordering.  I've tried to set this with MountManager, but it doesn't seem to stick, even after saving the configuration. What's the best way to do this?


I have not tried this, but here's an idea:
use the command blkid to get the UUID of your usb HDD.
then edit /etc/fstab to tell it how to mount and where to mount.

> **bjordan555 said:**
> 
Q2: I have network storage that's accessible through either webdav or SSH.  I'd like to have this mounted as a accessible directory in the local file system, so that, for example, I can save to this storage from within an appliction that doesn't let me navigate to /home/.gvfs. 


For this, I can tell you what I have done and what works. I used SSH to mount storage over the Internet or LAN. Here are example commands:

```
sudo nano /etc/fstab
```

Add something like this on one line, replacing the values with your own:
```
sshfs#your_user_name@192.168.1.1:/ /media/your_storage_name fuse rw,user,auto,fsname=sshfs#your_user_name@192.168.1.1:/ 0 0
```

your_user_name = your user name to log in to the storage device/system
192.168.1.1 = your LAN or WAN IP address
/media/your_storage_name = the local path where you want the storage mounted

---

### Post by like2watch on 2009-11-09
Hi MountainX

Per your suggestion I entered the following in Terminal
sudo nano /etc/fstab

This opened another Terminal window containing this

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=12e17861-6c3b-4c3d-8b73-1e688b22f09f /               ext3    relatime,erro$
# swap was on /dev/sda5 during installation
UUID=8d3a5153-d6e4-44ad-b687-efb189018526 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I modified your line as follows
sshfs#madman@192.168.2.106:/ /media/r4r fuse rw,user,auto,fsname=sshfs#enduser@192.168.2.108:/ 0 0

and pasted it into the window but I can't save and exit.

There are several "Commands" at the bottom of the window, one of which reads
^X
in inverse video followed by Exit but typing ^X only adds those keystrokes to the other text - does not save/exit

My brief reference to Terminal Commands says File/Close Window will exit Terminal but when I do so, I get a warning that a process is running and closing will kill it.  If I proceed to do so, the window closes but when I reopen it, the file has reverted to its original state.

Sooo,

Is my edit correct and if so, how do I save and exit?

Thanks

---

### Post by MountainX on 2009-11-09
> **like2watch said:**
> Hi MountainX

Per your suggestion I entered the following in Terminal
sudo nano /etc/fstab

This opened another Terminal window containing this

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=12e17861-6c3b-4c3d-8b73-1e688b22f09f /               ext3    relatime,erro$
# swap was on /dev/sda5 during installation
UUID=8d3a5153-d6e4-44ad-b687-efb189018526 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I modified your line as follows
sshfs#madman@192.168.2.106:/ /media/r4r fuse rw,user,auto,fsname=sshfs#enduser@192.168.2.108:/ 0 0

and pasted it into the window but I can't save and exit.

There are several "Commands" at the bottom of the window, one of which reads
^X
in inverse video followed by Exit but typing ^X only adds those keystrokes to the other text - does not save/exit

My brief reference to Terminal Commands says File/Close Window will exit Terminal but when I do so, I get a warning that a process is running and closing will kill it.  If I proceed to do so, the window closes but when I reopen it, the file has reverted to its original state.

Sooo,

Is my edit correct and if so, how do I save and exit?

Thanks

To save, use Control-X, then "yes" to save, then enter to accept. 

For more on how to use the nano editor, enter this in a terminal:

```
man nano
```
or google "nano editor how-to"

---

