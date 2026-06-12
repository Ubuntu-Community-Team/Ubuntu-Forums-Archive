---
title: "Memorex MP3 Player MMP8585C"
date: 2009-08-02
forum: Multimedia Software
---

### Post by Silvernail on 2009-08-02
I have recently purchased one of the above devices. It does not mount on my  system.  Of the 18 other threads on this board concerning this device, I did not see any of this type information presented. I am not knowledgable enough to work through it to figure where to mount my MP3 player to download some music.



Last 2 lines of 'dmesg' after  plugging device into USB port.
```

[  148.049642] usb 4-1: new high speed USB device using ehci_hcd and address 3
[  148.184321] usb 4-1: configuration #1 chosen from 1 choice

``` 
Results of 'sudo lsusb -vv'
```

Bus 004 Device 003: ID 10d6:2300 Actions Semiconductor Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x10d6 Actions Semiconductor Co., Ltd
  idProduct          0x2300 
  bcdDevice            1.00
  iManufacturer           1 .
  iProduct                2 Media Player
  iSerial                 3 9E5D7F0655923E41840B20F1AD9CC3AF
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration        238 MSFT100&#65533;
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               4
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```
From /dev

```

crw-rw----  1 root   root    254,   1 2009-08-02 01:39 usbdev1.1_ep81
crw-rw----  1 root   root    254,   2 2009-08-02 01:39 usbdev2.1_ep00
crw-rw----  1 root   root    254,   3 2009-08-02 01:39 usbdev2.1_ep81
crw-rw----  1 root   root    254,   4 2009-08-02 01:39 usbdev3.1_ep00
crw-rw----  1 root   root    254,   5 2009-08-02 01:39 usbdev3.1_ep81
crw-rw----  1 root   root    254,   8 2009-08-02 01:39 usbdev3.2_ep00
crw-rw----  1 root   root    254,   9 2009-08-02 01:39 usbdev3.2_ep81
crw-rw----  1 root   root    254,   6 2009-08-02 01:39 usbdev4.1_ep00
crw-rw----  1 root   root    254,   7 2009-08-02 01:39 usbdev4.1_ep81
```
Notice the difference in time.
Above was at boot time.
Below was at time of plugging device into USB port.
```

crw-rw----  1 root   root    254,  10 2009-08-02 01:42 usbdev4.3_ep00
crw-rw----  1 root   root    254,  11 2009-08-02 01:42 usbdev4.3_ep01
crw-rw----  1 root   root    254,  12 2009-08-02 01:42 usbdev4.3_ep82
crw-rw----  1 root   root    254,  13 2009-08-02 01:42 usbdev4.3_ep83

```

Dohicky Hardware Manager reconnized it and displayed some information but Nautilus did not.

Could someone point me toward further information to help me get my MP3 player working?

'lsusb' tells us it is Bus 4 and Dev 3. Would that mean this it wants to live on '/sdd3'?

Thanks for any help you can give.

---

### Post by Silvernail on 2009-08-02
Very early this morning I got up to check something and Dohicky, lsusb, and dmesg showed this to be Bus 4  Dev 8.

---

### Post by Silvernail on 2009-08-02
Very early this morning I got up to check something and Dohicky, lsusb, and dmesg showed this to be Bus 4  Dev 8.

Later in the day another plug in gave me Bus 4 Dev 6 and this dialog took place between me and my computer.

```
dave@gadabout:~$ mount /dev/sdd6
mount: can't find /dev/sdd6 in /etc/fstab or /etc/mtab
```

```
dave@gadabout:~$ sudo cat /etc/fstab
[sudo] password for dave: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6e47c899-9ada-4290-96e0-3b1e599958d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=7aafee9c-0cdb-4e21-9682-64c2c37b9563 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

``````

dave@gadabout:~$ ls /media/cdrom0
ls: cannot access /media/cdrom0: No such file or directory

``````

dave@gadabout:~$ ls /dev/scd0
/dev/scd0

``````

dave@gadabout:~$ ls /dev/scd0 -l
brw-rw----+ 1 root cdrom 11, 0 2009-08-02 10:02 /dev/scd0

``````

dave@gadabout:~$ mount /dev/scd0
mount: mount point /media/cdrom0 does not exist


``````

dave@gadabout:/$ dir -l
total 236
drwxr-xr-x   2 root root   4096 2009-03-11 21:20 bin
drwxr-xr-x   3 root root   4096 2009-07-30 13:06 boot
lrwxrwxrwx   1 root root     11 2008-03-16 20:27 cdrom -> media/cdrom
...................................

drwxr-xr-x   2 root root   4096 2009-08-02 10:03 media
...........................................
``````

dave@gadabout:/$ ls media
``````

dave@gadabout:/$ ls cdrom
``````

cdrom
``````

dave@gadabout:/$ ls cdrom -l
lrwxrwxrwx 1 root root 11 2008-03-16 20:27 cdrom -> media/cdrom
``````

dave@gadabout:/$ dir cdrom -l
lrwxrwxrwx 1 root root 11 2008-03-16 20:27 cdrom -> media/cdrom
dave@gadabout:/$
```

And then this is the out put for 'mtab'.
```

dave@gadabout:~$ cat /etc/mtab
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-24-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
dave@gadabout:~$ 

```

I'm at the end of what I need to show or were to go. Can anyone teach me?
Thanks
Dave

---

### Post by Silvernail on 2009-08-02
If I'd read what my computer was telling me maybe I could do better.
It says in '/etc/fstab' that my mp3 playes shows up as 'sda6'. And it does show in '/dev', but when it try to mount it, I get this message:
> 
dave@gadabout:~$ sudo mount -t auto sda6 /dev/audio
mount: special device sda6 does not exist
dave@gadabout:~$ 

Any suggestions here? And what should I mount to?

Thanks
Dave

---

### Post by cecst on 2009-09-16
> **Silvernail said:**
> I have recently purchased one of the above devices. It does not mount on my  system.  Of the 18 other threads on this board concerning this device, I did not see any of this type information presented....
<snip>
Results of 'sudo lsusb -vv'
[code]
Bus 004 Device 003: ID 10d6:2300 Actions Semiconductor Co., Ltd 
<snip>


Mounting usb devices automatically requires udev rules, which still have an aura of magic to me. I think the formats change, so that tutorials from a few years ago don't work.

Anyway, the following worked for me under Ubuntu 9.04 (Jaunty):
 1) sudo apt-get install usbmount
 2) insert the device into the USB drive
 3) reboot
 4) during rebooting, the device is recognized as a USB drive to which you can
    write (and presumably read). I copied some mp3 files to the device, and it
    played them after I unmounted the device and disconnected the USB cable.
 5) however, the device was *not* recognized when I reinserted it. There is something
    magic about the rebooting sequence that I have not looked into.
 6) credit for the above sequence goes to someone else; I read it on one of the boards.

---

### Post by Silvernail on 2009-09-16
Thanks for the information.  I'll get back to the mp3player as soon as I finish with the EASYCAP Cable Capture device.

Thanks.
Dave

---

### Post by cecst on 2009-09-16
> **Silvernail said:**
> Thanks for the information.  I'll get back to the mp3player as soon as I finish with the EASYCAP Cable Capture device.

Thanks.
Dave

You are most welcome. There is a gotcha that I just found out about: I did create
a udev file (see below) but it did not do anything even after restarting (/etc/init.d/udev restart) until I rebooted with the device plugged in. As it happened, I reinstalled jaunty on that machine today (wiping out that file),
and the clean os, even with usbmount installed, did not recognize the device even on reboot.

So, I recreated the udev file (/etc/udev/rules.d/10-custom.rule) with contents (all on one line):
BUS="usb", SYSFS{product}="Actions Semiconductor*", KERNEL="sd*", NAME{ignore_remove}="mp3", MODE="666"

Then, after rebooting with the device in place, its contents were mapped to /media/disk from /dev/sdb.

Hope this helps - Larry

---

### Post by Silvernail on 2009-09-22
I copied the 10-custom.rules to the udevd directory.
When I rebooted, I did not get an icon on my desktop. Was I suppose to?

> 
dave@gadabout:/var/log$ ls /media/disk
ls: cannot access /media/disk: No such file or directory
dave@gadabout:/var/log$ ls /deb/sdb1
ls: cannot access /deb/sdb1: No such file or directory
dave@gadabout:/var/log$ 


> 
dave@gadabout:~$ dmesg | grep usb
[   26.044369] usbcore: registered new interface driver usbfs
[   26.044396] usbcore: registered new interface driver hub
[   26.052155] usbcore: registered new device driver usb
[   26.056698] usb usb1: configuration #1 chosen from 1 choice
[   26.160330] usb usb2: configuration #1 chosen from 1 choice
[   26.264214] usb usb3: configuration #1 chosen from 1 choice
[   26.403808] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   26.527788] usb usb4: configuration #1 chosen from 1 choice
[   26.835102] usb 1-1: device not accepting address 2, error -71
[   26.849519] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   26.984223] usb 4-1: configuration #1 chosen from 1 choice
[   27.215785] usb 4-1: USB disconnect, address 2
[   27.272457] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   27.280707] usb 3-2: configuration #1 chosen from 1 choice
[   27.297734] usbcore: registered new interface driver hiddev
[   27.301015] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input2
[   27.301675] input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.2-2
[   27.301691] usbcore: registered new interface driver usbhid
[   27.301695] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.484869] usb 4-1: new high speed USB device using ehci_hcd and address 4
[   30.619557] usb 4-1: configuration #1 chosen from 1 choice
[   47.076884] usbcore: registered new interface driver libusual
[   47.177484] usbcore: registered new interface driver usb-storage
[   47.177582] usb-storage: device found at 4
[   47.177584] usb-storage: waiting for device to settle before scanning
[   50.654395] usb-storage: device scan complete
dave@gadabout:~$ 


After turning the mp3 player off and on several times.
> 
dave@gadabout:~$ dmesg | grep usb
[  163.397529] usb 4-1: USB disconnect, address 4
[  163.637442] usb 4-1: new high speed USB device using ehci_hcd and address 5
[  163.772223] usb 4-1: configuration #1 chosen from 1 choice
[  164.624427] usb 4-1: USB disconnect, address 5
[  164.666900] usb 1-1: new full speed USB device using uhci_hcd and address 4
[  164.670044] usb 1-1: not running at top speed; connect to a high speed hub
[  164.672285] usb 1-1: configuration #1 chosen from 1 choice
[  164.802485] usb 1-1: USB disconnect, address 4
[  164.982715] usb 4-1: new high speed USB device using ehci_hcd and address 7
[  165.117169] usb 4-1: configuration #1 chosen from 1 choice
[  165.144031] usb-storage: device found at 7
[  165.144037] usb-storage: waiting for device to settle before scanning
[  165.388106] usb 4-1: USB disconnect, address 7
dave@gadabout:~$ 


I evidently left it in an off postion, try again.
> 
[  165.710940] usb 4-1: new high speed USB device using ehci_hcd and address 8
[  165.845690] usb 4-1: configuration #1 chosen from 1 choice
[  179.986435] usb 4-1: USB disconnect, address 8
[  180.020499] usb 1-1: new full speed USB device using uhci_hcd and address 5
[  180.025208] usb 1-1: not running at top speed; connect to a high speed hub
[  180.026875] usb 1-1: configuration #1 chosen from 1 choice
[  180.154222] usb 1-1: USB disconnect, address 5
[  180.349460] usb 4-1: new high speed USB device using ehci_hcd and address 10
[  180.484006] usb 4-1: configuration #1 chosen from 1 choice
[  180.511097] usb-storage: device found at 10
[  180.511103] usb-storage: waiting for device to settle before scanning
[  180.948005] usb-storage: device scan complete


Extract from '/var/log/messages.
> 
Sep 22 10:55:48 gadabout pulseaudio[6877]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Sep 22 10:55:48 gadabout pulseaudio[6877]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Sep 22 10:55:48 gadabout pulseaudio[6877]: alsa-util.c: Cannot find fallback mixer control "Mic".
Sep 22 10:58:57 gadabout kernel: [  163.397529] usb 4-1: USB disconnect, address 4
Sep 22 10:59:01 gadabout kernel: [  163.637442] usb 4-1: new high speed USB device using ehci_hcd and address 5
Sep 22 10:59:01 gadabout kernel: [  163.772223] usb 4-1: configuration #1 chosen from 1 choice
Sep 22 10:59:16 gadabout kernel: [  164.624427] usb 4-1: USB disconnect, address 5
Sep 22 10:59:16 gadabout kernel: [  164.666900] usb 1-1: new full speed USB device using uhci_hcd and address 4
Sep 22 10:59:16 gadabout kernel: [  164.670044] usb 1-1: not running at top speed; connect to a high speed hub
Sep 22 10:59:16 gadabout kernel: [  164.672285] usb 1-1: configuration #1 chosen from 1 choice
Sep 22 10:59:17 gadabout kernel: [  164.802485] usb 1-1: USB disconnect, address 4
Sep 22 10:59:20 gadabout kernel: [  164.982715] usb 4-1: new high speed USB device using ehci_hcd and address 7
Sep 22 10:59:21 gadabout kernel: [  165.117169] usb 4-1: configuration #1 chosen from 1 choice
Sep 22 10:59:21 gadabout kernel: [  165.138608] scsi7 : SCSI emulation for USB Mass Storage devices
Sep 22 10:59:23 gadabout kernel: [  165.388106] usb 4-1: USB disconnect, address 7
Sep 22 10:59:27 gadabout kernel: [  165.710940] usb 4-1: new high speed USB device using ehci_hcd and address 8
Sep 22 10:59:28 gadabout kernel: [  165.845690] usb 4-1: configuration #1 chosen from 1 choice
Sep 22 11:02:43 gadabout kernel: [  179.986435] usb 4-1: USB disconnect, address 8
Sep 22 11:02:44 gadabout kernel: [  180.020499] usb 1-1: new full speed USB device using uhci_hcd and address 5
Sep 22 11:02:44 gadabout kernel: [  180.025208] usb 1-1: not running at top speed; connect to a high speed hub
Sep 22 11:02:44 gadabout kernel: [  180.026875] usb 1-1: configuration #1 chosen from 1 choice
Sep 22 11:02:44 gadabout kernel: [  180.154222] usb 1-1: USB disconnect, address 5
Sep 22 11:02:49 gadabout kernel: [  180.349460] usb 4-1: new high speed USB device using ehci_hcd and address 10
Sep 22 11:02:49 gadabout kernel: [  180.484006] usb 4-1: configuration #1 chosen from 1 choice
Sep 22 11:02:49 gadabout kernel: [  180.505813] scsi8 : SCSI emulation for USB Mass Storage devices
Sep 22 11:02:54 gadabout kernel: [  180.991596] scsi 8:0:0:0: Direct-Access     GENERIC  USB DISK DEVICE  1.00 PQ: 0 ANSI: 0 CCS
Sep 22 11:02:54 gadabout kernel: [  181.009041] sd 8:0:0:0: [sdb] 7879273 512-byte hardware sectors (4034 MB)
Sep 22 11:02:54 gadabout kernel: [  181.009906] sd 8:0:0:0: [sdb] Write Protect is off
Sep 22 11:02:54 gadabout kernel: [  181.012652] sd 8:0:0:0: [sdb] 7879273 512-byte hardware sectors (4034 MB)
Sep 22 11:02:54 gadabout kernel: [  181.013275] sd 8:0:0:0: [sdb] Write Protect is off
Sep 22 11:02:54 gadabout kernel: [  181.013286]  sdb: unknown partition table
Sep 22 11:02:54 gadabout kernel: [  181.019691] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Sep 22 11:02:54 gadabout kernel: [  181.019742] sd 8:0:0:0: Attached scsi generic sg2 type 0
Sep 22 11:11:54 gadabout gnome-power-manager: (dave) Doing nothing. Reason: The lid has been closed on ac power.
Sep 22 11:35:18 gadabout -- MARK --
Sep 22 11:55:18 gadabout -- MARK --
Sep 22 12:07:13 gadabout gnome-power-manager: (dave) Doing nothing. Reason: The lid has been closed on ac power.
dave@gadabout:/var/log$ 


---

### Post by Silvernail on 2009-09-23
This is after booting with the device plugged in.

> dave@Dafy:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    144G  4.5G  133G   4% /
tmpfs        tmpfs    498M     0  498M   0% /lib/init/rw
varrun       tmpfs    498M  112K  498M   1% /var/run
varlock      tmpfs    498M     0  498M   0% /var/lock
udev         tmpfs    498M  168K  497M   1% /dev
tmpfs        tmpfs    498M  132K  498M   1% /dev/shm
lrm          tmpfs    498M  2.2M  495M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb6     ext3    2.3G  2.0G  188M  92% /media/usb0
/dev/sdb1     ext3    919G  7.5G  866G   1% /media/usb1


> 
dave@Dafy:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b4800d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      120901   971137251   83  Linux
/dev/sdb2          120902      121601     5622750    5  Extended
/dev/sdb5          121228      121601     3004123+  82  Linux swap / Solaris
/dev/sdb6          120902      121205     2441817   83  Linux
/dev/sdb7          121206      121227      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 4034 MB, 4034187776 bytes
125 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?           1           1           0    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 255, 0) logical=(0, 0, 1)
Partition 1 has different physical/logical endings:
     phys=(0, 0, 0) logical=(554189, 41, 4)
Partition 1 does not end on cylinder boundary.
dave@Dafy:~$ 



> dave@Dafy:/proc$ cat partitions
major minor  #blocks  name

   8        0  156290904 sda
   8        1  153308263 sda1
   8        2          1 sda2
   8        5    2980026 sda5
   8       16  976762584 sdb
   8       17  971137251 sdb1
   8       18          1 sdb2
   8       21    3004123 sdb5
   8       22    2441817 sdb6
   8       23     176683 sdb7
   8       32    3939636 sdc
dave@Dafy:/proc$ 
> dave@Dafy:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9d7a3c74-d189-46be-845f-3160871d14d2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cb590f73-95f1-4fb8-875d-0fc8bec6d0cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
dave@Dafy:/etc$

Is the mp3 player showing up as a CDROM?

> Bus 001 Device 004: ID 10d6:1101 Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player
Bus 001 Device 002: ID 059b:0370 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dave@Dafy:~$ 


Thanks for your time to read all this.

Dave

---

### Post by Cuba71 on 2009-09-25
I have the same VID/PID unit and I have no problems with mounting it, it does it automatically, but it doesn't play the MP3 files I load through Nautilus, it gives me a "format error", I'm not sure if it's refering to the format of the file or the format of the player.

```

Bus 001 Device 014: ID 10d6:1101 Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player

```

---

### Post by Cuba71 on 2009-09-28
I've been able to load songs into my AS mp3 player using Windows Media Player, I tried amarok, rythmbox and nautilus with no success.

---

### Post by fondle-em on 2009-12-10
I've stumbled across what seems like the same MP3 player (no-name, but it identifies itself as the same Actions Semiconductor model according to lsusb).  There's something *very* screwy about either this device or Ubuntu's handling of it.  I can read the Britney Spears video and any files that were included on the unit.  Ubuntu can write to it and read the files written to it.  But once I eject (with the eject button in nautilus, or using the command line) and reconnect it, Ubuntu can't read any of the newly written files anymore, but can still read the ones that were included on the device.  Attempts to use the device to listen to any files added through Ubuntu generate the "Format error" message mentioned earlier in the thread - and whether or not I try and play a file on the device after disconnecting it from the computer has no effect on the files being unusable.

---

### Post by LintonHanes on 2010-01-31
your fdisk output said it all,, the filesystems f'd,, gparted it (partition editor)

---

