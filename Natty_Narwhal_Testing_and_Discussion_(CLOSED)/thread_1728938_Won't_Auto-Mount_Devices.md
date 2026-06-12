---
title: "Won't Auto-Mount Devices"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Armando Penblade on 2011-04-14
Running a nearly clean install of 11.04 Beta, 32-bit (because the 64-bit installer is apparently borked for me and a couple of other people? I posted about it elsewhere and no one had a solution, sadly). Ubuntu no longer auto-mounts attached devices, like my iPod and external hard drive. having to go into terminal and manually fudge with that stuff is precisely the sort of thing I use Ubuntu to avoid, so anyone have any suggestions about why it would start doing this out of the blue?

I don't mind using Terminal to fix the issue, so long as it stays fixed, of course ;)

---

### Post by Armando Penblade on 2011-04-14
More interesting: if I do manually mount the iPod, it isn't seen by programs like Banshee and Rhythmbox (mounted to /media/ipod). If I open up GTKpod iPod Manager, however, it sees it just fine. I've rebooted a few times now. No luck :-/

---

### Post by Armando Penblade on 2011-04-14
Upon further review, it appears that devices aren't being added to or accounted for by fstab or mtab. Any reason why things wouldn't show up there automatically? I was under the understanding that all of this stuff was handled automatically for several years now.

---

### Post by mc4man on 2011-04-14
See no issues here with either externel drives or devives such as an ipod. This is both added afer boot or connected while booting.
Everything shows up in mtab, as far as fstab never saw any point to adding externals unless one needed to change from the default mount option for such.
Do you have media automount disabled?

---

### Post by Armando Penblade on 2011-04-14
I didn't realize mtab was preferable here; when I tried mount commands earlier, it would always tell me it couldn't find it in etc/fstab. How would I go about adding these things in there, because they aren't there by default.

I do have automount enabled in gconf settings. What's weird is that this worked up until about 4 reboots ago when it suddenly stopped.

Copied below is my mtab, which seems to completely lack entries for any of the connected devices. How would I add one to it?

> /dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/armandopenblade/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=armandopenblade 0 0

---

### Post by mc4man on 2011-04-15
> How would I add one to it?
I guess you misunderstood me - "Everything _shows up_ in mtab" means -  If i plug in a device (external drive, ipod, flash drive) it shows up in mtab. If I remove the device it is removed from mtab
mtab is dynamic, you don't edit it (at least I don't

---

### Post by Armando Penblade on 2011-04-16
So any idea what might be preventing these drives and devices from automounting?

---

### Post by dino99 on 2011-04-16
playing/tweaking with fstab/mtab is highly scary, better to set your prefs with mountmanager (look at synaptic)

---

### Post by Armando Penblade on 2011-04-17
I've repeatedly used mountmanager to setup automount for my devices, but they will not automount. I must still do it manually, and when I do, in the case of the ipod, Banshee and Rhythmbox can't "see" it, while with my Droid, it won't mount as writeable by "my" user, so I must open Nautilus from terminal as su to even access the files on my Droid's SD Card.

I'll paste what happens in System Log when I plug in the iPod to see if anyone can figure out why it's screwing up all my USB devices :(

```
Apr 17 23:30:35 UbuntuPrime kernel: [170106.746718] usb 2-3: USB disconnect, address 7
Apr 17 23:30:35 UbuntuPrime upstart-udev-bridge[335]: Env must be KEY=VALUE pairs
Apr 17 23:30:43 UbuntuPrime kernel: [170114.376047] usb 2-3: new high speed USB device using ehci_hcd and address 8
Apr 17 23:30:43 UbuntuPrime kernel: [170114.511302] scsi12 : usb-storage 2-3:1.0
Apr 17 23:30:44 UbuntuPrime kernel: [170115.511105] scsi 12:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Apr 17 23:30:44 UbuntuPrime kernel: [170115.512417] sd 12:0:0:0: Attached scsi generic sg6 type 0
Apr 17 23:30:44 UbuntuPrime kernel: [170115.595063] sd 12:0:0:0: [sde] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
Apr 17 23:30:44 UbuntuPrime kernel: [170115.596198] sd 12:0:0:0: [sde] Write Protect is off
Apr 17 23:30:44 UbuntuPrime kernel: [170115.596210] sd 12:0:0:0: [sde] Mode Sense: 68 00 00 08
Apr 17 23:30:44 UbuntuPrime kernel: [170115.598054] sd 12:0:0:0: [sde] No Caching mode page present
Apr 17 23:30:44 UbuntuPrime kernel: [170115.598066] sd 12:0:0:0: [sde] Assuming drive cache: write through
Apr 17 23:30:44 UbuntuPrime kernel: [170115.600820] sd 12:0:0:0: [sde] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
Apr 17 23:30:44 UbuntuPrime kernel: [170115.603690] sd 12:0:0:0: [sde] No Caching mode page present
Apr 17 23:30:44 UbuntuPrime kernel: [170115.603701] sd 12:0:0:0: [sde] Assuming drive cache: write through
Apr 17 23:30:44 UbuntuPrime kernel: [170115.605962]  sde: sde1 sde2
Apr 17 23:30:44 UbuntuPrime kernel: [170115.608423] sd 12:0:0:0: [sde] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
Apr 17 23:30:44 UbuntuPrime kernel: [170115.611480] sd 12:0:0:0: [sde] No Caching mode page present
Apr 17 23:30:44 UbuntuPrime kernel: [170115.611491] sd 12:0:0:0: [sde] Assuming drive cache: write through
Apr 17 23:30:44 UbuntuPrime kernel: [170115.611500] sd 12:0:0:0: [sde] Attached SCSI removable disk
Apr 17 23:30:45 UbuntuPrime kernel: [170116.349849] FAT: invalid media value (0x2f)
Apr 17 23:30:45 UbuntuPrime kernel: [170116.349860] VFS: Can't find a valid FAT filesystem on dev sde1.
Apr 17 23:30:45 UbuntuPrime upstart-udev-bridge[335]: Env must be KEY=VALUE pairs
```

---

### Post by Armando Penblade on 2011-04-17
Okay, seriously, this is ridiculous. even after mounting it as su, and running rhythmbox as su, I can't see the ipod in my music apps. Even GTK iPod Manager fails to read/write from the volume even though I set it up so anyone could read/write it in MountManager -.-

**Edit: and apparently I can't load the disk manager from Ubuntu's own settings, and its failure to launch doesn't trigger any errors in any of my system logs?**

---

### Post by cariboo on 2011-04-18
I don't know anything about these Apple devices, but are they formatted as vfat, because if they are, your problem is starring you in the face from your dmesg output.

> FAT: invalid media value (0x2f)
Apr 17 23:30:45 UbuntuPrime kernel: [170116.349860] VFS: Can't find a valid FAT filesystem on dev sde1.

---

### Post by Armando Penblade on 2011-04-18
They are formatted fat32 and are readable on all other computers, and if I build fstab from scratch, mount as su, etc, I can sometimes get programs to read it in Ubuntu 11.04, but not all the time, and my fstab seems to keep getting wiped out? It seems like MountManager might be doing that, even though it has complicated rules for all the drives listed and set to apply.

---

### Post by mc4man on 2011-04-18
Sometimes things go south on their own, other times it's what people do.
This seems more like the latter - I have several installs and all usb devices are detected and auto-mounted just fine. (or if left connected at boot are mounted and available at login.
So what you describe seems quite abnormal - maybe post the fstab you're using.

The syslog entry is fine  - same here with an ipod, the end part is probably because it is both a 'player' and a storage device
(basically the same that you'd see with a flash drive except for those 2 lines.

---

### Post by stanz on 2011-04-18
I've been trying to figure this one out also, with fresh installs - not tweaking or 'doing' anything.
No usb device have been detected and/or auto-mounted at boot.

lsusb returns nadda, passed over mtab/fstab, tried pmount and other usb stuff. Can't do media cards-webcam....none of the toys!
ol'well  :)
Bug #709611
I'm over at qa.testing-got my laptop specs there.

---

### Post by dino99 on 2011-04-18
if you search "ipod" into synaptic, is hipo installed or some libgpod* ?

sudo update-pciids && sudo update-usbids

note: set fstab with the partition you boot on & swap, nothing else, the others will be mounted (by mountall) on request

---

### Post by DougieFresh4U on 2011-04-19
Have been on vacation for 9 days and just noticed this thread. I to am having the issue discussed.
Have never had the problem of my phones/shuffle not being recognized on older versions of Ubuntu. Issue has just popped up with Natty install with no tweaks or adjustments to default install.
When I plug my phone in, it flashes 'Sanyo' very quickly and continuous in menu

---

### Post by dino99 on 2011-04-19
something to try:

[http://ubuntuforums.org/showpost.php?p=10571879&postcount=1](http://ubuntuforums.org/showpost.php?p=10571879&postcount=1)

---

### Post by DougieFresh4U on 2011-04-19
> **dino99 said:**
> something to try:

[http://ubuntuforums.org/showpost.php?p=10571879&postcount=1](http://ubuntuforums.org/showpost.php?p=10571879&postcount=1)

Thanks, no luck.
Here is error that pops up when my Sanyo phone is plugged in:

---

### Post by dino99 on 2011-04-19
is there a menu into your sanyo reader ? In that case format from that menu, not with linux
searching "sanyo" into synaptic, i wonder if bitpim can help

an other way:
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/#comments](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/#comments)

---

