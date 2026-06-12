---
title: "Banshee Folder Issue"
date: 2015-04-14
forum: Multimedia Software
---

### Post by Lightning Dragon on 2015-04-14
Hello,

My Banshee won't remember the folders I add. After reboot they vanish and I have to readd all the folders for my music again. Every reboot. I thought it was because I cleared cache or something, but I haven't done that. Here are some snapshots of the first two tabs in Preferences in case this can help solve the issue.

[http://i.imgur.com/Tq0k9LC.png](http://i.imgur.com/Tq0k9LC.png)
[http://i.imgur.com/1eWfldl.png](http://i.imgur.com/1eWfldl.png)

**Information:**

output of "uname -r" is 
```
3.16.0-34-generic

```
output of "uname -a" is 
```
Linux LightningDragon 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
output of "lsb_release -a" is
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

```
output of "aplay -l" is
```

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
output of "lspci" is
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

```

If I need to share anymore information, I will be glad to. 

**Further Details:**
I have my music on an external drive and while Banshee "remembers" the songs playing them results in an "X" next to it and no sound. It forgets the location/url to the folders. 

So what could be the issue?


Thank you for reading! ):P

---

### Post by dino99 on 2015-04-14
i'm not a banshee user, so only propose to glance at this faq; possibly some extensions might help; who knows ?
[http://banshee.fm/support/faq/](http://banshee.fm/support/faq/)

---

### Post by Lightning Dragon on 2015-04-14
> **9d9 said:**
> i'm not a banshee user, so only propose to glance at this faq; possibly some extensions might help; who knows ?
[http://banshee.fm/support/faq/](http://banshee.fm/support/faq/)

It would certainly be weird if an extension prevented the software from deleting folder locations but I've seen things do silly things before so I am definitely going to check this out right this instant. Thank you regardless for the help! :)

As for the rest of the FAQ, I don't get any errors or reports just a little x next to all the song titles but it sounds like the bit at the end. I decided to run Banshee through the terminal and this is what I got. Just thought it would be helpful to share:

```

[Info  05:29:54.902] Running Banshee 2.6.2: [Ubuntu 14.04.1 LTS (linux-gnu, x86_64) @ 2014-08-12 14:04:38 UTC]

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkComponent) to class (__gtksharp_49_Hyena_Gui_BaseWidgetAccessible) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_50_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_50_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_56_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_56_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_62_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_62_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_68_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_68_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_74_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:13213): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_74_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init
[Warn  05:29:55.266] Caught an exception - GLib.GException: Icon 'process-working' not present in theme (in `gtk-sharp')
  at Gtk.IconTheme.LoadIcon (System.String icon_name, Int32 size, IconLookupFlags flags) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.Widgets.TaskStatusIcon..ctor () [0x00000] in <filename unknown>:0 
[Info  05:29:55.506] Updating web proxy from GConf
[Info  05:29:55.565] All services are started 0.564475

(Banshee:13213): GLib-CRITICAL **: Source ID 149 was not found when attempting to remove it
[Info  05:29:55.948] AmazonMP3 store redirect URL: http://integrated-services.banshee.fm/amz/redirect.do/
<memory>:1: Invalid color constant '#121212

    GtkTextView::error-underline-color =  '
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::even-row-color' of type `GdkColor' from rc file value ""#121212\n\n\tGtkTextView::error-underline-color =  "" of type `gchararray'
[Info  05:29:56.144] nereid Client Started
[Info  05:29:56.166] GStreamer version 1.2.4.0, gapless: True, replaygain: False
[Info  05:29:56.204] AppleDeviceSource is ignoring unmounted volume Games
[Info  05:29:56.204] AppleDeviceSource is ignoring unmounted volume 500 GB Volume
[Info  05:29:56.205] AppleDeviceSource is ignoring unmounted volume Storage
bpm_detect got error: Your GStreamer installation is missing a plug-in. gstdecodebin2.c(3928): gst_decode_bin_expose (): /GstPipeline:pipeline/GstDecodeBin:decodebin:
no suitable plugins found
bpm_detect got error: Internal data flow error. midiparse.c(1289): gst_midi_parse_loop (): /GstPipeline:pipeline/GstDecodeBin:decodebin/GstMidiParse:midiparse0:
streaming task paused, reason not-linked (-1)

```

I'm guess that's causing my issues but glancing at it looks like it is just related to themes, not the actual program. But what do I know. #-o

---

### Post by dino99 on 2015-04-14
Looks like the Trusty archives packages (here banshee) is doing a durty use of old api (apps not updated)
Why not moving to vivid now ?

---

### Post by coffeecat on 2015-04-14
> **Lightning Dragon said:**
> **Further Details:**
I have my music on an external drive and while Banshee "remembers" the songs playing them results in an "X" next to it and no sound. It forgets the location/url to the folders.

How are you mounting the external drive?

---

### Post by speartip on 2015-04-14
You need to make sure that the External Drive your files are on, is 1st of all turned on, then is mounted at boot.
Also what type of file system is it? NTFS, EXT4, etc...
More info will mean we can help you better.

---

### Post by Lightning Dragon on 2015-04-14
Hello, and thank you for the replies guys!

> **9d9 said:**
> Looks like the Trusty archives packages (here banshee) is doing a durty use of old api (apps not updated)
Why not moving to vivid now ?

How do I stop that and what is vivid?

> **coffeecat said:**
> How are you mounting the external drive?

I'm not sure. I just have them plugged in and then they automatically mount on boot.

> **speartip said:**
> You need to make sure that the External Drive  your files are on, is 1st of all turned on, then is mounted at boot.
Also what type of file system is it? NTFS, EXT4, etc...
More info will mean we can help you better.

How can I make sure it is the first turned on and mounted?

It is NTFS.

---

### Post by coffeecat on 2015-04-14
> **Lightning Dragon said:**
> 
How do I stop that and what is vivid?

Vivid is the codename for Ubuntu 15.04 which is due to be released in just over a week. I suggest you don't upgrade simply because you have a problem with Banshee. Banshee should work just fine in 14.04. Let's concentrate on what’s going wrong for you. 

> **Lightning Dragon said:**
> 
I'm not sure. I just have them plugged in and then they automatically mount on boot.

I should imagine they are being mounted by means of udisks rather than using /etc/fstab. In which case the mountpoint may change from time to time, and this will confuse Banshee. In such a situation it's better to have a line in /etc/fstab. Let's get some information. Boot up with the external drive(s) switched on so that they mount. Now run these terminal commands and post the output:

```
cat /etc/fstab
sudo blkid
sudo fdisk -lu
mount
```

NTFS is fine for your music collection, by the way.

---

### Post by Lightning Dragon on 2015-04-14
> **coffeecat said:**
> Vivid is the codename for Ubuntu 15.04 which is due to be released in just over a week. I suggest you don't upgrade simply because you have a problem with Banshee. Banshee should work just fine in 14.04. Let's concentrate on what’s going wrong for you. 



I should imagine they are being mounted by means of udisks rather than using /etc/fstab. In which case the mountpoint may change from time to time, and this will confuse Banshee. In such a situation it's better to have a line in /etc/fstab. Let's get some information. Boot up with the external drive(s) switched on so that they mount. Now run these terminal commands and post the output:

```
cat /etc/fstab
sudo blkid
sudo fdisk -lu
mount
```

NTFS is fine for your music collection, by the way.

Ah, yea, I would prefer to stick with 14.04 LTS. :)

Here are the outputs you requested:

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d5cad172-4a97-44c5-82fd-8a6d4871a39d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=5263-5DAA  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=e25ccd0b-5fa3-4212-ad90-07d477583371 none            swap    sw              0       0

```

```

sudo blkid
/dev/sda1: UUID="5263-5DAA" TYPE="vfat" 
/dev/sda2: UUID="d5cad172-4a97-44c5-82fd-8a6d4871a39d" TYPE="ext4" 
/dev/sda3: UUID="e25ccd0b-5fa3-4212-ad90-07d477583371" TYPE="swap" 
/dev/sdb1: UUID="641C-3B35" TYPE="vfat" 
/dev/sdb3: UUID="AA941EAA941E78D1" TYPE="ntfs" 
/dev/sdc: LABEL="Storage" UUID="5019579071277F6F" TYPE="ntfs" 
/dev/sdd1: LABEL="Games" UUID="3EF44951F4490D19" TYPE="ntfs" 
/dev/sde1: LABEL="Music" UUID="98A49458A4943AA8" TYPE="ntfs" 
/dev/sdf1: LABEL="Programs" UUID="8C6CF4986CF47E70" TYPE="ntfs" 
/dev/sr1: LABEL="WD SmartWare" TYPE="udf" 
/dev/sdg1: LABEL="Storage II" UUID="DA88A6BA88A69493" TYPE="ntfs" 

```

```

sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13f81513

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not start on physical sector boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not start on physical sector boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty

Partition table entries are not in disk order

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe24a688d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x68f5c20d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1953520127   976760032+   7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdf: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sdg: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0bde545d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048   975400959   487699456    7  HPFS/NTFS/exFAT

```

```

mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=LightningDragon)
/dev/sr1 on /media/LightningDragon/WD SmartWare type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,uhelper=udisks2)
/dev/sdf1 on /media/LightningDragon/Programs type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdg1 on /media/LightningDragon/Storage II type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sde1 on /media/LightningDragon/Music type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```

---

### Post by coffeecat on 2015-04-14
I'll concentrate on your sde Music external drive – I'm assuming this is the one that Banshee is using. At the moment it is being automounted on /media/LightningDragon/Music, and that ought to be consistent. So I'm not 100% convinced this is the problem, but it would be better to have your sde drive mounted by means of /etc/fstab anyway. Let's see if that solves the problem. Be warned though, that you will have to empty and rebuild the Banshee library – it will not know about the new mountpoint – see below.

First thing, here's a useful community wiki page about mounting Windows partitions:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

But I'll guide you through adding a line in /etc/fstab for sde.

First you need to create a mount point. I prefer mountpoints in /media where you will see a line in the left pane of the file manager to correspond. Some people prefer using /mnt, and you don't get it showing in the file manager. I'll take you through mounting on a sub-folder in /media.

Open a terminal, and...

```
sudo mkdir /media/Music
```

You now need to add a line to /etc/fstab for sde1. Open gedit with root privileges with...

```
sudo -H gedit
```

You may come across advice not to open a GUI app with sudo, but to use gksu or gksudo. Absolutely correct, but gksu is not installed by default in Ubuntu anymore, so to make things simple we'll use sudo with the -H option. That avoids the problem of vanilla sudo.

Add this line to the end of your /etc/fstab. 

```
UUID=98A49458A4943AA8  /media/Music  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
```

As an alternative, if you want to be able to move things to trash, use this line:

```
UUID=98A49458A4943AA8  /media/Music  ntfs-3g  defaults,uid=1000,windows_names,locale=en_US.utf8  0 0
```

If you do want to use that second line, check that your UID is 1000 with the terminal command...

```
id
```

Once you've typed in the new line (best if you copy paste from this post) and checked it, save and close gedit.

Now unmount your Music partition:

```
sudo umount /dev/sde1
```

Now remount it with your new fstab line:

```
sudo mount -a
```

You now have to do something about the library in Banshee. It will not be able to find any of your music files on the new mountpoint. Right-click on All Artists &#8594; Remove from Library. Do **not** choose Delete from Drive. Ouch! You might want to make sure you have adequate backups of your music library. You don't want only one copy on the drive you are using every day.
I'll concentrate on your sde Music external drive – I'm assuming this is the one that Banshee is using. At the moment it is being automounted on /media/LightningDragon/Music, and that ought to be consistent. So I'm not 100% convinced this is the problem, but it would be better to have your sde drive mounted by means of /etc/fstab anyway. Let's see if that solves the problem. Be warned though, that you will have to empty and rebuild the Banshee library – it will not know about the mountpoint – see below.

First thing, here's a useful community wiki page about mounting Windows partitions:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

But I'll guide you through adding a line in /etc/fstab for sde.

First you need to create a mount point. I prefer mountpoints in /media where you will see a line in the left pane of the file manager to correspond. Some people prefer using /mnt, and you don't get it showing in the file manager. I'll take you through mounting on a sub-folder in /media.

Open a terminal, and...

```
sudo mkdir /media/Music
```

You now need to add a line to /etc/fstab for sde1. Open gedit with root privileges with...

```
sudo -H gedit
```

You may come across advice not to open a GUI app with sudo, but to use gksu or gksudo. Absolutely correct, but gksu is not installed by default in Ubuntu anymore, so to make things simple we'll use sudo with the -H option. That avoids the problem of vanilla sudo.

Add this line to the end of your /etc/fstab. 

```
UUID=98A49458A4943AA8  /media/Music  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
```

As an alternative, if you want to be able to move things to trash, use this line:

```
UUID=98A49458A4943AA8  /media/Music  ntfs-3g  defaults,uid=1000,windows_names,locale=en_US.utf8  0 0
```

If you do want to use that second line, check that your UID is 1000 with the terminal command...

```
id
```

Once you've typed in the new line (best if you copy paste from this post) and checked it, save and close gedit.

Now unmount your Music partition:

```
sudo umount /dev/sde1
```

Now remount it with your new fstab line:

```
sudo mount -a
```

You now have to do something about the library in Banshee. It will not be able to find any of your music files on the new mountpoint. Right-click on All Artists &#8594; Remove from Library. Do **not** choose Delete from Drive. Ouch!

Now Media &#8594; Import Media and go through your routine to import all your music from the drive.

If you have playlists I'm afraid you're on your own. I don't bother with playlists. I think they will need rebuilding. 

That's about everything. Make sure your sde drive is switched on before you boot up. If it isn't, you'll get an error message telling you that the partition is unavailable and asking whether you want to retry, skip, etc.
Now Media &#8594; Import Media and go through your routine to import all your music from the drive.

If you have playlists I'm afraid you're on your own. I don't bother with playlists. I think they will need rebuilding. 

That's about everything. Make sure your sde drive is switched on before you boot up. If it isn't, you'll get an error message telling you that the partition is unavailable and asking whether you want to retry, skip, etc.

---

### Post by Lightning Dragon on 2015-04-15
Hello,

@coffeecat

Okay got to remounting the drive but it says "[mntent]: line 14 in /etc/fstab is bad".

edit

Ah, I had to comment out the mount options (add an "#"). Okay, moving on. Sorry for the delay. Oh, and backups will not be possible...at least it would take days because I have 200GB of music. But I will make a backup first as per your advice. :)

edit 2

Okay, did everything up to reimporting. I can create the playlists again but I want to know what location I import the folders from. The same location as before, correct? Because the one in Media/Music is empty, but the same old location from before leads me to my music.

---

### Post by coffeecat on 2015-04-15
> **Lightning Dragon said:**
> Okay got to remounting the drive but it says "[mntent]: line 14 in /etc/fstab is bad".

edit

Ah, I had to comment out the mount options (add an "#"). 

I do not follow you. You should **not** comment out the mount options - it will simply not work if you do. If you got a "line XX is bad" message at first then that means you made a mistake in transcribing the fstab line.  Please post the output of:

```
cat /etc/fstab
```

> **Lightning Dragon said:**
> Okay, did everything up to reimporting. I can create the playlists again but I want to know what location I import the folders from. The same location as before, correct? Because the one in Media/Music is empty, but the same old location from before leads me to my music.

Best stop right there. If /media/Music is empty, then it means that your new fstab line is not working (see above). You need to fix that first before re-importing your music.

---

### Post by Lightning Dragon on 2015-04-15
> **coffeecat said:**
> I do not follow you. You should **not** comment out the mount options - it will simply not work if you do. If you got a "line XX is bad" message at first then that means you made a mistake in transcribing the fstab line.  Please post the output of:

```
cat /etc/fstab
```



Best stop right there. If /media/Music is empty, then it means that your new fstab line is not working (see above). You need to fix that first before re-importing your music.

That would explain it being empty. :-P 

I did the output and for some reason the name of the drive changed. I never altered it so I don't know how it happened, just before I did the commands it was just "Music". Anyways...here is the output:

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d5cad172-4a97-44c5-82fd-8a6d4871a39d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=5263-5DAA  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=e25ccd0b-5fa3-4212-ad90-07d477583371 none            swap    sw              0       0
#UUID=98A49458A4943AA8  /media/Music's Drive  ntfs-3g  defaults,uid=1000,windows_names,locale=en_US.utf8  0 0=

```

And I checked uid and it was 1000, by the way.

---

### Post by coffeecat on 2015-04-15
Here is your problem:

> **Lightning Dragon said:**
> ```

#UUID=98A49458A4943AA8  /media/Music's Drive  ntfs-3g  defaults,uid=1000,windows_names,locale=en_US.utf8  0 0=

```



1 - You've commented the line out - as you said - which means it will be ignored. It's non-functional.

2 - Why did you put the mountpoint as "media/Music's Drive"???? There are strict syntax rules to be followed. You have created a custom mountpoint at /media/Music (I hope) with the command *sudo mkdir /media/Music*. That is what you must refer to in /etc/fstab. When the system parses that line, it gets to "Music's Drive", can't make head or tail of it and comes up with the error message you saw.

3 - There is a spurious = sign at the end of the line. Please take it out.

Once you've corrected all those errors you will need to go through the unmount and mount steps I describe before.

---

### Post by Lightning Dragon on 2015-04-15
> **coffeecat said:**
> Here is your problem:



1 - You've commented the line out - as you said - which means it will be ignored. It's non-functional.

2 - Why did you put the mountpoint as "media/Music's Drive"???? There are strict syntax rules to be followed. You have created a custom mountpoint at /media/Music (I hope) with the command sudo mkdir /media/Music. That is what you must refer to in /etc/fstab. When the system parses that line, it gets to "Music's Drive", can't make head or tail of it and comes up with the error message you saw.

3 - There is a spurious = sign at the end of the line. Please take it out.

Once you've corrected all those errors you will need to go through the unmount and mount steps I describe before.

1. Removing it now.

2. I never altered the name of anything, I don't know how that happened. But I have changed it back and made the edits to the fstab file.

3. That's not actually there, I accidentally included it in the output.

I have redone everything and will now reboot after importing the music to see if the issue is gone. :)

EDIT

Oh my GOD! It worked! And guess what else? I think it fixed my Spotify issue, which sort of did the same thing! Thank you so much coffeecat! I can listen to my music without  hassle!  :guitar:

---

### Post by coffeecat on 2015-04-15
> **Lightning Dragon said:**
> 
Oh my GOD! It worked! And guess what else? I think it fixed my Spotify issue, which sort of did the same thing!

"It worked!" Of course it did! :wink:

I don't have any experience of spotify but perhaps that was the same problem of differing mountpoints. Whenever you have applications accessing files on partitions other than the root one, and particularly if the application has libraries such as Banshee or some photo management software, it is always better to ensure the other partitions are mounted consistently. And that means using /etc/fstab.

I note you have other external drives that you access regularly. You might want to consider mounting them the same way. All the information you need is in this thread and the community wiki page I linked earlier. The problem with external drives is as I mentioned earlier. If you forget to switch them on before booting up, you will see an error message. That is why I prefer to keep my music and photos in a partition on an internal drive.

---

### Post by Lightning Dragon on 2015-04-15
> **coffeecat said:**
> "It worked!" Of course it did! :wink:

I don't have any experience of spotify but perhaps that was the same problem of differing mountpoints. Whenever you have applications accessing files on partitions other than the root one, and particularly if the application has libraries such as Banshee or some photo management software, it is always better to ensure the other partitions are mounted consistently. And that means using /etc/fstab.

I note you have other external drives that you access regularly. You might want to consider mounting them the same way. All the information you need is in this thread and the community wiki page I linked earlier. The problem with external drives is as I mentioned earlier. If you forget to switch them on before booting up, you will see an error message. That is why I prefer to keep my music and photos in a partition on an internal drive.

I really think it is the same issue, as so far Spotify is reading my Local Files just fine (they would report "broken files" upon reboot as well). I'm going to have to re-add all my music first to make sure but I'm pretty sure it is fixed now. 

Yes, I access them every single day. So I will do just that, but how can I mount them if they have long names or spaces? I added a new drive the other day while in Windows and called it "Work's Backups". I would rename the drive but I already have Windows tied to it (symlinks, taskbar shortcuts, file memory etc etc) and would hate to find them all broken in Windows upon reboot.

[SIZE=1]I would do that but my internal drives are much smaller and I would rather keep the sata connections on the motherboard free for just OSes or game storage. [/SIZE]

---

### Post by coffeecat on 2015-04-15
> **Lightning Dragon said:**
> how can I mount them if they have long names or spaces? I added a new drive the other day while in Windows and called it "Work's Backups". I would rename the drive but I already have Windows tied to it (symlinks, taskbar shortcuts, file memory etc etc) and would hate to find them all broken in Windows upon reboot.

The partition name doesn't matter that much. In /etc/fstab the partition is defined by means of its UUID, and you can create a mountpoint with whatever name you wish, thus avoiding spaces. For "Work's Backups" I would create /media/WorksBackups or /media/Works_Backups. Problem solved.

You can escape spaces in /etc/fstab but it's probably more elegant and certainly easier to avoid them in the first place. It's also advisable to avoid characters which are invalid in NTFS filesystems:

[https://support.microsoft.com/en-us/kb/177506](https://support.microsoft.com/en-us/kb/177506)

The "windows_names" mount option prevents you from creating files or folders with those characters, but you would be able to create a mountpoint with them using mkdir. I don't think such would create a
problem, but it's best avoided.

---

### Post by Lightning Dragon on 2015-04-15
> **coffeecat said:**
> The partition name doesn't matter that much. In /etc/fstab the partition is defined by means of its UUID, and you can create a mountpoint with whatever name you wish, thus avoiding spaces. For "Work's Backups" I would create /media/WorksBackups or /media/Works_Backups. Problem solved.

You can escape spaces in /etc/fstab but it's probably more elegant and certainly easier to avoid them in the first place. It's also advisable to avoid characters which are invalid in NTFS filesystems:

[https://support.microsoft.com/en-us/kb/177506](https://support.microsoft.com/en-us/kb/177506)

The "windows_names" mount option prevents you from creating files or folders with those characters, but you would be able to create a mountpoint with them using mkdir. I don't think such would create a
problem, but it's best avoided.

Hello,

I have done the steps for all the other drives except the one/s with spaces. It was very easy. :KS

So in fstab I could do either "/media/WorksBackups" or "/media/Works_Backups"?  If so, am I missing something? I tried both and upon remounting I get "fuse: failed to access mountpoint /media/X: No such file or directory", where "X" is both options tried.

edit'

Nevermind, solved it by doing it like this "/media/Work's\040Backups". Now it is all mounted to /media and working as the Music folder! :D

---

### Post by coffeecat on 2015-04-15
> **Lightning Dragon said:**
> 
So in fstab I could do either "/media/WorksBackups" or "/media/Works_Backups"?  If so, am I missing something? I tried both and upon remounting I get "fuse: failed to access mountpoint /media/X: No such file or directory", where "X" is both options tried.

That would mean you had not created the mountpoints /media/WorksBackups or /media/Works_Backups. You have to create the mountpoint first. I see you've got there with escaping the space in /etc/fstab. If, by chance, you created a mountpoint /media/Work's Backups and then tried /media/WorksBackups in /etc/fstab it wouldn't work, of course.

---

### Post by Lightning Dragon on 2015-04-15
> **coffeecat said:**
> That would mean you had not created the mountpoints /media/WorksBackups or /media/Works_Backups. You have to create the mountpoint first. I see you've got there with escaping the space in /etc/fstab. If, by chance, you created a mountpoint /media/Work's Backups and then tried /media/WorksBackups in /etc/fstab it wouldn't work, of course.

Doh! Such simplicity escaped me. #-o 

Yes, I just escaped the spaces. Was super easy when I remembered the "\040" thing.

Anyways, all is well now! All externals have been remounted in /media and my music works even after reboot in Banshee/Spotify.

Thanks coffecat, once again, for the great and simplified help! I really appreciate it. :)

---

