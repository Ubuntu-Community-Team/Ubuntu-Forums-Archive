---
title: "Problems connecting Samsung YP-S3 Ogg Vorbis Player"
date: 2008-08-02
forum: Multimedia Software
---

### Post by Rabenschwinge on 2008-08-02
Hello,

since I had I accidently gave my last Ogg Vorbis player a ride in the washing machine I bought a new one - Samsung, same as last. But somehow udev does not seem to handle it correctly, while I can see it in lsusb it does not mount automatically. Is there anyway to enforce this, or to mount it manually?

syslog excerpts:
```
Aug  2 15:31:02 schatten kernel: [ 3020.537210] usb 2-10: new high speed USB device using ehci_hcd and address 7
Aug  2 15:31:02 schatten kernel: [ 3020.670203] usb 2-10: configuration #1 chosen from 1 choice
Aug  2 15:31:02 schatten NetworkManager: <debug> [1217683862.858713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4e8_5091_363f4618000000d9'). 
Aug  2 15:31:02 schatten NetworkManager: <debug> [1217683862.887365] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4e8_5091_363f4618000000d9_if0').
```

lsusb -v output:
```
Bus 002 Device 007: ID 04e8:5091 Samsung Electronics Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04e8 Samsung Electronics Co., Ltd
  idProduct          0x5091 
  bcdDevice            1.00
  iManufacturer           1 Samsung Electronics Co.,Ltd.
  iProduct                2 S3
  iSerial                 3 363f4618000000d9
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
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
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               2
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

---

### Post by stoneater on 2008-08-13
The Samsung S3 is an MTP-only device.

The problem is the mtp support over linux.
MTP is an extension of the USB standard, and it is made by Microsoft.
As a result MTP support on linux is not complete.
I've been searching a lot to solve this problem.
The only way for me was to setup a virtual machine with windows inside linux....
I think we have to wait a new firmware by samsung enabling UMS support (it works just like and usb drive) or wait for a better MTP support on Linux 
Anyway I saw there is a new firmware there:
[http://www.anythingbutipod.com/forum/showthread.php?t=32690](http://www.anythingbutipod.com/forum/showthread.php?t=32690)
but I didn't test it.

Regards
Stoneater

---

### Post by mlaverdiere on 2008-08-30
Here's what I did to have the Samsung YP-S3 works perfectly in UMS mode with Ubuntu Hardy (after some digging, fumbling, try & error, etc.):

1.  First, a functional UMS firmware must be installed on the S3.  [The one available right now is provided by Samsung Korea]("http://www.yepp.co.kr/support/support_file_down_sms.jsp?pds_num=1863&seq_num=2") ([See this page an updated and complete list of available firmwares]("http://forum.generationmp3.com/Tous_les_derniers_firmwares_Samsung_UMS_surtout-t57064.html"). It has to be installed with the the proper config.dat file (description after) at the root of the device, then, after unplugging the device, the firmware upgrade/change will be performed automatically. Obviously, to be able to do this, the device has to be mounted first in MTP mode. I did this with Windows XP (with Windows Media Player, version 10 or superior installed). It's probably possible to do it with Ubuntu by now, after having installed mtpfs (sudo apt-get install mtpfs) and fumbling around with config files.  Here's some more info:


[LIST]
[*]The config.dat file has to be created, with the following content:
    
YP-S3
KR KO UMS
    
With this file, you will have the Korean language activated, but you'll be able to switch to your preferred language in the /settings/language menu (I think I have managed once to perform the upgrade by using "US US UMS" instead of "KR KO UMS" and then having English as the interface language, but I'm not sure; anyway, the "KR KO UMS" was suggested in one forum and for sure, it worked).
[*]Other interesting ressources:
[LIST]
[*]For a complete liste of Samsung YP (and other DAP) firmwares, [see this unofficial page]("http://www.anythingbutipod.com/forum/showthread.php?t=32690")
[*]For another description of the procedure, [see this thread]("http://www.anythingbutipod.com/forum/showthread.php?t=33445&amp;highlight=yp-s3")
[*]If yout want to try to have the S3 work in MTP mode under Linux/Ubuntu, see [this]("https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/131744")  and [this]("http://linuxtechie.wordpress.com/2008/03/09/ubuntu-804-hardy-heron-brings-better-mtp-support/"); (Note:  I didn't try seriously to make the S3 mount in MTP mode with Linux, so I'm not sure if it will work... but I think it could!)
[/LIST]
 
[/LIST]
 
2.  Once the UMS firmware is correctly installed, plug the S3 and you should have 2 new removable USB media storage devices recognized, one big (3.7 GB) for the data (music, video, etc,) and another one small (40 MB) that appears to be reserved for the S3 ROM, with system and config files; If, like me, you just want the data partition (the big 3.7 GB one) to be automounted and visible, you can add this line in your fstab file (make sure that the UUID corresponds to the one allocated to the S3 system/config partition on your system

UUID=0000-CCCC vfat rw,nosuid,nodev,relatime,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,noauto 0 0


3.  In Ubuntu Hardy, the S3 (with the UMS firmware) is recognized as a regular USB device, instead of a Digital Audio Player (DAP). It doesn't prevent you to move music (or other) files on the S3 with Nautilus (or other file manager) and play them, but it may be annoying since audio application, like Rhythmbox, won't be able to recognize the device correctly; To have the S3 recognized as a DAP, [see the solution provided in this bug report]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/252457") (in fact, this is not really a bug, since the S3 is quite new; this report has been made with the hope that future Ubuntu versions will automatically recognize the S3 as a DAP).

In order to have the modification effective, don't forget to run the following command:  sudo /etc/init.d/hal restart

Hope this helps.

---

### Post by whitmad on 2008-09-16
Splendid - this worked just fine for me with only one small alteration - the root directory of my S3 when connected to Windows XP was not writeable, but copying the S3.ROM and config.dat files to the Data directory had the desired effect.

Many thanks

---

### Post by agoodno on 2008-11-15
I've followed all the directions posted by mlaverdiere and my device is showing now Korean firmware (Settings->System->About reports Firmware Version 1.50c KR) and I've switched back to English language.  The problem is now Hardy is not mounting it.  Using dmesg, I've verified that it is being recognized but is saying:

[98473.127162] usb 4-6: new high speed USB device using ehci_hcd and address 4
[98473.260194] usb 4-6: configuration #1 chosen from 1 choice

I've read up on udev and udevinfo and think I need to manually mount but don't know which device to use.  So,

sudo mount /dev/<usb46?> /mnt/usb

So, how do I find the device name and why is it not automounting?

Andy

---

### Post by mlaverdiere on 2008-11-16
Hum, it should mount automatically, like any other UMS USB device...  

Anyway, you can try the following command to figure out what's going on and try to manually mount your S3:



1.  Just after you have plugged the S3, type the following command:

dmesg

You should see something like this, at the end of the output:

[47260.132085] usb 2-3: new high speed USB device using ehci_hcd and address 5
[47260.269919] usb 2-3: configuration #1 chosen from 1 choice
[47260.270898] scsi12 : SCSI emulation for USB Mass Storage devices
[47260.273001] usb-storage: device found at 5
[47260.273046] usb-storage: waiting for device to settle before scanning
[47266.272633] usb-storage: device scan complete

If you don't see anything like this, it would probably mean that the kernel is not recognizing the S3 (it could be the case if you use a custom compile kernel).



2.  Now use the following command

sudo fdisk -l

It should report something like this (sorry, my system is in French, but you should get the idea, i.e. the red part indicates that the S3 is mountable on /dev/sdc1, being a 4GB fat16 partition):  

Disque /dev/sda: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xb0016565

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        4042    32467333+   7  HPFS/NTFS
/dev/sda2           29158       30401     9988096    7  HPFS/NTFS
/dev/sda3            4043       29157   201736237+   5  Extended
/dev/sda5            4043       28134   193518958+  83  Linux
/dev/sda6           28135       29157     8217216   82  Linux swap / Solaris

Les entrées de la table de partitions ne sont pas dans l'ordre du disque

Disque /dev/sdc: 4030 Mo, 4030692864 octets
255 heads, 63 sectors/track, 490 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xffffffff

Périphérique Amorce    Début         Fin      Blocs    Id  Système
[COLOR="Red"]/dev/sdc1               1         485     3893244    6  FAT16[/COLOR]
Partition 1 a des débuts différents physique/logique (non Linux?):
     phys=(1023, 254, 63) logique=(0, 0, 9)
Partition 1 a des fins différentes physique/logique:
     phys=(1023, 254, 63) logique=(484, 175, 11)



3.  Now, you should be able to mount the S3 as /dev/sdc1 (based on the above output - on your system, it may be different) as a vfat device, on a mounting point (directory) that you have manually created (let's say /media/S3) with the following command:

sudo mount -t vfat /dev/sdc1 /media/S3


Hope this helps.

---

### Post by Qchan on 2008-12-24
[b][color=darkred]
The problem is that this device doesn't seem to work in Intrepid Ibex. I followed what mlaverdiere said to the T. 

1) I downloaded the Korean firmware
2) I created the config.dat file with the proper information inside.
3) I placed both files in the root directory of the device in Windows and then unplugged the device.

4) The device installed the firmware. Once I started it, It displayed Korean.

5) I navigated through the device and set it back to English.
6) I plugged the device back in and it still acts as an MTP device. 

It doesn't act like a USM device in either Windows or Linux.
I even tried running dmesg to check what I get after plugging the device in. I see words showing the device is being detected. Even lsusb shows the device. However, when I do sudo fdisk -l, it doesn't show its partition at all.

I also tried installing mtpfs and tried to get the device to read that way, and there was no luck whatsoever. I tried plugging this baby in several other Linux machines and no luck at all. 

Did I leave anything out? Who knows.
[/b][/color]

---

### Post by laxwrestler on 2008-12-28
the problem is this device isn't supported by libmtp.  there is a ticket in their source forge bug tracker.  i reccommend monitoring it for updates if you have this problem.  

As far as updating the firmware, i'm not sure but it seems like samsung has updated the newer s3's so the ums firmware can't be loaded.  after some searching it seems several people (myself included) have been able to follow the instructions for updating firmware, which will lead to a language change to korean, however no change from MTP to UMS.

It is weird though, on the samsung us website, the s3 is listed as being UMS compatible.  I also sent samsung an email about this although i am skeptical about recieving a response. we shall see i suppose.

ALSO, i can't seem to get windows XP running in virtualbox to recognize the s3 through usb.  this my first time messing with virtualbox though so if anyone had any help with that i'd appreciate it.  I REALLY don't want to have to boot up windows to put crap on this thing.  damn christmas presents.

---

### Post by Schitso on 2008-12-29
This may interest someone:

```
tyler@kaylee-laptop:~$ lsusb -d 04e8:5091
tyler@kaylee-laptop:~$ sudo lsusb -d 04e8:5091
Bus 005 Device 003: ID 04e8:5091 Samsung Electronics Co., Ltd 
```

---

### Post by laxwrestler on 2008-12-29
yeah ubuntu recognizes it but the mtp library can't handle it.  in case anyone else was wondering you have to download the proprietary version of virtualbox for usb support.  they have pretty good instructions for setting it up.  this seems like the easiest solution for now unless you have a computer running windows just sittin around.

---

### Post by Schitso on 2008-12-30
Solved! (Using MTP)

Add the following to /etc/udev/rules.d/45-libmtp8.rules

```
# Samsung YP-S3
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5091", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```

After that, add yourself to the group "audio" and restart your computer.
Problem fixed :D

Do note that you may need to manually add "MTP Media Device" in Amarok.

---

### Post by FlipJones on 2009-01-18
1) can i make this work out of the box with just that edited line?

2) group "audio" ?

---

### Post by Qchan on 2009-01-19
> **Schitso said:**
> Solved! (Using MTP)

Add the following to /etc/udev/rules.d/45-libmtp8.rules

```
# Samsung YP-S3
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5091", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```

After that, add yourself to the group "audio" and restart your computer.
Problem fixed :D

Do note that you may need to manually add "MTP Media Device" in Amarok.

[b][color=darkred]
I did this, and it didn't work for me. I'm assuming you did something before adding an MTP device to Amarok.
[/b][/color]

---

### Post by Enigmacat on 2009-02-15
For some reason, I am unable to add:
```

# Samsung YP-S3
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5091", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

```

I keep getting:
```

Could not save the file /etc/udev/rules.d/45-libmtp8.rules.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

```

What the H#$l! I am the only user on my system, what does it mean I don't have permission?

---

### Post by laxwrestler on 2009-02-16
how are you opening the file? you need root permissions to edit it. Try running this command from the terminal. applications > accessories > terminal.

sudo gedit /etc/udev/rules.d/45-libmtp8.rules

---

### Post by ricemark20 on 2009-03-10
> **Schitso said:**
> Solved! (Using MTP)

Add the following to /etc/udev/rules.d/45-libmtp8.rules

```
# Samsung YP-S3
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5091", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```

After that, add yourself to the group "audio" and restart your computer.
Problem fixed :D

Do note that you may need to manually add "MTP Media Device" in Amarok.

Didn't work.  The file saves, but even after restart, nothing shows up.  Yes, I did add myself to the group "audio"

---

### Post by Schitso on 2009-03-23
Make sure you put
```
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5091", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```
by the other ATTR entires and 
```
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5091", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```
by the other ATTRS entries.

Also, post the output of theses:
```

lsusb -d 04e8
sudo lsusb -d 04e8

```

---

### Post by atropa on 2009-04-26
All the tricks above didn't do the job for me.
The only thing that worked was to get the Korean UMS firmware
(which is now not available anymore from Samsung, but you can get it eg from anythingbutipod), connect it to a windows pc and load the new firmware.
Now it works like a charm.

---

### Post by ricemark20 on 2009-05-02
> **atropa said:**
> All the tricks above didn't do the job for me.
The only thing that worked was to get the Korean UMS firmware
(which is now not available anymore from Samsung, but you can get it eg from anythingbutipod), connect it to a windows pc and load the new firmware.
Now it works like a charm.

I tried the Korean firmware, but I don't think the config.dat file is right.
What did you use?

---

### Post by jaleos on 2009-05-05
Try (checking before you mtpfs and libmtp installed on your system)

Create a folder in /home or /home/username  with the name you want, for example

```
$ mkdir /home/"username"/YP

```
And proceeded to mount your device in it.

```
$ sudo mtpfs /home/"username"/YP -o allow_other

```
You should show a volume icon on the desktop. You can treat as a single disc.
From Amarok> Playlist> Add Media can also work with the contents of YP, once mounted.

Unloading

```
$ sudo umount /home/"username"/YP 

```
Since the icon> right click> unmount volume do not operate for lack of permits, but that is in your hands.

However it is advisable to check the hardware support offered Linux before you buy, although there is almost nothing that can not be done, it will always be more comfortable, and you encourage manufacturers to think at all before releasing their product. While there will always be that ******* birthday :D.

I hope you find useful
Best regards,

Translated by google, sorry

---

### Post by JR_Moneybags on 2009-05-05
Jaleos.

What luck! I was just coming on tonight to find out how to get the YP-S3 working.

Works brilliantly in as far as mounting, however browsing the filesystem in Nautilus is not working well for me.

I am able to view and open folders, however I am unable to see any files. Also I have been unable to copy any more than 3-4 files to the device at any time before receiving the error:
"Transport endpoint is not connected"

Any ideas?

---

### Post by jaleos on 2009-05-06
Hello
Never had this problem. I think you should do a check now.  
First check that installed the mtp-tools 
You can 
```
$ mtp-detect
```
if it prints out a lot of information about the connected MTP-devices, than you are almost done (see man mtp-tools for some very interesting options)

To mount a MTP device you need the package fuse, to check
```
lsmod | grep fuse
```
To load
```
$ sudo modprobe fuse
```
Verify that your user is a member of the group fuse
```
$ grep fuse /etc/group
```
Add user
```
$ sudo adduser "JR_Moneybags" fuse
```
It is also necessary to install the package fuse-utils (to use fusermount) 

Check if there is allready a proper rule for your device, in my case
```
$ gedit /etc/udev/rules.d/45-libmtp7.rules
```
You can reconfigure your dynamic linker run-time bindings
```
ldconfig
```  

Others who will work with libmtp should be in the audio group (look above group fuse)

You can see other problems with "mount" and "ls -la"

I also install libnjb5 and packages -dev -doc and -examples for libmtp (do not know if it will be good for work)

This way you should do a proper diagnosis for your MTP device
This works without problems on my system.
I hope you have more luck

--jaleos

---

### Post by tomcat2007 on 2009-05-07
I have realized limited success with Intrepid & Jaunty using the following process:

sudo apt-get install mtpfs mtp-tools
sudo adduser tomcat2007 fuse
sudo mtpfs /home/tomcat2007/mounts/samsung -o allow_other

The OS sees the device, mounts it, but cannot see all of the file system.  

Nautilus displays the root filesystem but when clicking into /Music, nothing is displayed although there are filesystems containing MP3s.

Bash displays the root filesystem without problems, but when cding into /Music, the attributes, ownership, size, & timestamps are garbled although the filesystem names within are correctly represented.

I tried the mount specifying -o subtype=FAT32 and again with -o subtype=FAT but achieve the same result.

Anyone got any suggestions?

I have also been unable to get this thing to work in a v2.2.2 VirtualBox XP SP3 client although USB seems to work just fine.  Installed all the proprietary crapware and WMP11... but no cigar.

---

### Post by jaleos on 2009-05-07
You've tried as root ? 
```
$ sudo mtpfs /home/jaleos/samsung -o allow_root
$ sudo su
root@Core-Duo:/home/jaleos# ls -la
drwxrwxrwx  2 root   root            0 1970-01-01 01:00 samsung

root@Core-Duo:/home/jaleos/samsung/Music# ls -la
total 0
drwxrwxrwx 2 root root 0 1970-01-01 01:00 .
drwxrwxrwx 2 root root 0 1970-01-01 01:00 ..
drwxrwxrwx 2 root root 0 1970-01-01 01:00 Capoeira
drwxrwxrwx 2 root root 0 1970-01-01 01:00 De todo
drwxrwxrwx 2 root root 0 1970-01-01 01:00 Hardstyle
drwxrwxrwx 2 root root 0 1970-01-01 01:00 Hip-Hop
```

root@Core-Duo:/home/jaleos# nautilus 
and with two windows you can work graphically :), best working as root!.

or as a user ?
```
$ mtpfs /home/jaleos/samsung
$ ls -la
drwxrwxrwx  2 jaleos jaleos          0 1970-01-01 01:00 samsung

jaleos@Core-Duo:~/samsung$ ls -la
total 3
drwxrwxrwx  2 jaleos jaleos    0 1970-01-01 01:00 .
drwxr-xr-x 62 jaleos jaleos 2808 2009-05-07 01:29 ..
drwxrwxrwx  2 jaleos jaleos    0 1970-01-01 01:00 Music

```

---

### Post by tomcat2007 on 2009-05-08
Tried as a normal user initially, but since you mentioned running related items as root,  I get the same thing (mounting for root and starting nautilus & bash as root)  Nautilus shows filesystems in / but nothing in them.  Bash shows "D????????? ? ? ? ?                   ? New Songs"

---

### Post by JR_Moneybags on 2009-05-09
I have pretty much the same problem as tomcat.

As far as diagnosing my device - I have problems at nearly every step.
Starting with mtp-detect

```
libmtp version: 0.3.6

Listing raw device(s)
   Found 1 device(s):
   Samsung: YP-S3 (04e8:5091) @ bus 0, dev 0
Attempting to connect device(s)
usb_claim_interface(): Operation not permitted
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.

```

I get further with
$ sudo mtp-detect
```
libmtp version: 0.3.6

Listing raw device(s)
   Found 1 device(s):
   Samsung: YP-S3 (04e8:5091) @ bus 0, dev 5
Attempting to connect device(s)
Error 7: Found a bad handle, trying to ignore it.
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 04e8
   idProduct: 5091
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 5
      Device entry info:
         Vendor: Samsung
         Vendor id: 0x04e8
         Product: YP-S3
         Vendor id: 0x5091
         Device flags: 0x00001204
Microsoft device descriptor 0xee:
	0000: 1203 4d00 5300 4600 5400 3100 3000 3000	..M.S.F.T.1.0.0.
	0010: 0400                                   	..
Microsoft device response to control message 1, CMD 0x04:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000 0403 0904 3a03 5300	............:.S.
	0030: 6100 6d00 7300 7500 6e00 6700 2000 4500	a.m.s.u.n.g. .E.
	0040: 6c00 6500 6300 7400 7200 6f00 6e00 6900	l.e.c.t.r.o.n.i.
	0050: 6300 7300 2000 4300 6f00 2e00 2c00 4c00	c.s. .C.o...,.L.
	0060: 7400 6400 2e00 0803 5300 3300 0000 2203	t.d.....S.3...".
	0070: 3900 3900 3900 6500 6600 3200 3600 3000	9.9.9.e.f.2.6.0.
	0080: 3000 3000 3000 3000 3000 3000 6400 3500	0.0.0.0.0.0.d.5.
	0090: 0008 74b5 cb08 74b5 cf08 74b6 0908 74b6	..t...t...t...t.
	00a0: 1100 0000 0000 0000 0200 0000 0022 0100	............."..
	00b0: 0022 0200 0000 0000 0000 0000 8000 0000	."..............
	00c0: 0000 0000 0000 0000 0000 0000 0000 0000	................
	00d0: 0000 0000 0000 0000 0100 0002 0000 3b1f	..............;.
	00e0: bf00 3b1f be00 0000 0008 0e1f 0808 0e24	..;............$
	00f0: cc08 0e27 d808 0e29 7408 0e2c 0808 0e2e	...'...)t..,....
	0100: 6808 0e2f 0008 0e2f d408 0e30 e808 0e32	h../.../...0...2
	0110: 7808 0e33 f800 0000 0000 0000 0000 0000	x..3............
	0120: 0000 0000 0000 0000 0022 0100 0022 0200	........."..."..
	0130: 00ff ffff ffff ffff ff00 0000 040b ec00	................
	0140: 000b ec00 0005 f600 0005 f600 0002 fb00	................
	0150: 0000 2462 0300 11f9 0300 1ad2 0300 2462	..$b..........$b
	0160: 0200 24f9 0300 0cd2 0100 2462 0100 2172	..$.......$b..!r
	0170: 0100 11f9 0100 2195 0100 1ad2 0100 2c8a	......!.......,.
	0180: 0100 26af 0100 3c78 0100 2eaa 0100 24f9	..&...<x......$.
	0190: 0100 24f9 0100 37ae 0100 2edd 0100 36c7	..$...7.......6.
	01a0: 0100 36d2 0100 3677 0000 0009 9900 000b	..6...6w........
	01b0: f600 000e f300 0013 b500 0016 b100 001d	................
	01c0: e600 0027 3b00 0029 9f00 002f d800 0035	...';..).../...5
	01d0: d200 003b ce00 0041 c800 0047 8600 004d	...;...A...G...M
	01e0: be00 0053 7c00 0057 6400 005a c400 0060	...S|..Wd..Z...`
	01f0: 3500 0066 1c00 006b 8e00 0071 7500 007d	5..f...k...qu..}
	0200: fe00 0009 da00 000b f600 000e f300 0013	................
	0210: b500 0017 4e00 001d e600 0027 3b00 0029	....N......';..)
	0220: 9f00 002f d800 0035 d200 003b ce00 0041	.../...5...;...A
	0230: c800 0047 8600 004d be00 0053 7c00 0059	...G...M...S|..Y
	0240: b400 005f b000 0065 6d00 0066 1c00 006b	..._...em..f...k
	0250: 8e00 0071 7500 007d fe00 0009 da00 000b	...qu..}........
	0260: f600 000e f300 0013 b500 0017 ec00 001e	................
	0270: f900 0028 a300 0029 9f00 002f d800 0035	...(...).../...5
	0280: d200 003b ce00 0041 c800 0047 8600 004d	...;...A...G...M
	0290: be00 0053 7c00 0059 b400 005f b000 0065	...S|..Y..._...e
	02a0: 6d00 006b a600 0071 6300 0077 9c00 0084	m..k...qc..w....
	02b0: 1000 0009 da00 000b f600 000e f300 0013	................
	02c0: b500 0016 b100 001d e600 0027 3b00 0029	...........';..)
	02d0: 9f00 002f d800 0035 d200 003b ce00 0041	.../...5...;...A
	02e0: c800 0047 8600 004d be00 0053 7c00 0059	...G...M...S|..Y
	02f0: b400 005f b000 0062 cf00 0066 1c00 006b	..._...b...f...k
	0300: 8e00 0071 7500 007d fe00 000a dc00 000c	...qu..}........
	0310: 9400 000e f300 0015 b800 0017 ec00 0022	..............."
	0320: 6400 002b 3a00 002d dd00 0033 b600 0038	d..+:..-...3...8
	0330: 9900 003e e400 0045 2d00 004a 1800 004d	...>...E-..J...M
	0340: be00 0056 7c00 0059 b400 0063 2000 0069	...V|..Y...c ..i
	0350: 1200 006f 8400 0075 7600 007b e800 008b	...o...uv..{....
	0360: 3900 0009 da00 000b f600 000e f300 0013	9...............
	0370: b500 0016 b100 001e f900 0029 4100 002b	...........)A..+
	0380: 1e00 0031 9000 0037 c100 003b ce00 0041	...1...7...;...A
	0390: c800 0047 8600 004d be00 0053 7c00 0057	...G...M...S|..W
	03a0: 6400 005a c400 0060 3500 0066 1c00 006b	d..Z...`5..f...k
	03b0: 8e00 0071 7500 007d fe00 0009 da00 000b	...qu..}........
	03c0: f600 000e f300 0013 b500 0017 ec00 001e	................
	03d0: f900 0029 4100 002b c500 0031 9000 0037	...)A..+...1...7
	03e0: c100 003d f400 0044 2500 0047 8600 004d	...=...D%..G...M
	03f0: be00 0053 7c00 0059 b400 005f b000 0065	...S|..Y..._...e
Microsoft device response to control message 2, CMD 0x04:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000 0403 0904 3a03 5300	............:.S.
	0030: 6100 6d00 7300 7500 6e00 6700 2000 4500	a.m.s.u.n.g. .E.
	0040: 6c00 6500 6300 7400 7200 6f00 6e00 6900	l.e.c.t.r.o.n.i.
	0050: 6300 7300 2000 4300 6f00 2e00 2c00 4c00	c.s. .C.o...,.L.
	0060: 7400 6400 2e00 0803 5300 3300 0000 2203	t.d.....S.3...".
	0070: 3900 3900 3900 6500 6600 3200 3600 3000	9.9.9.e.f.2.6.0.
	0080: 3000 3000 3000 3000 3000 3000 6400 3500	0.0.0.0.0.0.d.5.
	0090: 0008 74b5 cb08 74b5 cf08 74b6 0908 74b6	..t...t...t...t.
	00a0: 1100 0000 0000 0000 0200 0000 0022 0100	............."..
	00b0: 0022 0200 0000 0000 0000 0000 8000 0000	."..............
	00c0: 0000 0000 0000 0000 0000 0000 0000 0000	................
	00d0: 0000 0000 0000 0000 0100 0002 0000 3b1f	..............;.
	00e0: bf00 3b1f be00 0000 0008 0e1f 0808 0e24	..;............$
	00f0: cc08 0e27 d808 0e29 7408 0e2c 0808 0e2e	...'...)t..,....
	0100: 6808 0e2f 0008 0e2f d408 0e30 e808 0e32	h../.../...0...2
	0110: 7808 0e33 f800 0000 0000 0000 0000 0000	x..3............
	0120: 0000 0000 0000 0000 0022 0100 0022 0200	........."..."..
	0130: 00ff ffff ffff ffff ff00 0000 040b ec00	................
	0140: 000b ec00 0005 f600 0005 f600 0002 fb00	................
	0150: 0000 2462 0300 11f9 0300 1ad2 0300 2462	..$b..........$b
	0160: 0200 24f9 0300 0cd2 0100 2462 0100 2172	..$.......$b..!r
	0170: 0100 11f9 0100 2195 0100 1ad2 0100 2c8a	......!.......,.
	0180: 0100 26af 0100 3c78 0100 2eaa 0100 24f9	..&...<x......$.
	0190: 0100 24f9 0100 37ae 0100 2edd 0100 36c7	..$...7.......6.
	01a0: 0100 36d2 0100 3677 0000 0009 9900 000b	..6...6w........
	01b0: f600 000e f300 0013 b500 0016 b100 001d	................
	01c0: e600 0027 3b00 0029 9f00 002f d800 0035	...';..).../...5
	01d0: d200 003b ce00 0041 c800 0047 8600 004d	...;...A...G...M
	01e0: be00 0053 7c00 0057 6400 005a c400 0060	...S|..Wd..Z...`
	01f0: 3500 0066 1c00 006b 8e00 0071 7500 007d	5..f...k...qu..}
	0200: fe00 0009 da00 000b f600 000e f300 0013	................
	0210: b500 0017 4e00 001d e600 0027 3b00 0029	....N......';..)
	0220: 9f00 002f d800 0035 d200 003b ce00 0041	.../...5...;...A
	0230: c800 0047 8600 004d be00 0053 7c00 0059	...G...M...S|..Y
	0240: b400 005f b000 0065 6d00 0066 1c00 006b	..._...em..f...k
	0250: 8e00 0071 7500 007d fe00 0009 da00 000b	...qu..}........
	0260: f600 000e f300 0013 b500 0017 ec00 001e	................
	0270: f900 0028 a300 0029 9f00 002f d800 0035	...(...).../...5
	0280: d200 003b ce00 0041 c800 0047 8600 004d	...;...A...G...M
	0290: be00 0053 7c00 0059 b400 005f b000 0065	...S|..Y..._...e
	02a0: 6d00 006b a600 0071 6300 0077 9c00 0084	m..k...qc..w....
	02b0: 1000 0009 da00 000b f600 000e f300 0013	................
	02c0: b500 0016 b100 001d e600 0027 3b00 0029	...........';..)
	02d0: 9f00 002f d800 0035 d200 003b ce00 0041	.../...5...;...A
	02e0: c800 0047 8600 004d be00 0053 7c00 0059	...G...M...S|..Y
	02f0: b400 005f b000 0062 cf00 0066 1c00 006b	..._...b...f...k
	0300: 8e00 0071 7500 007d fe00 000a dc00 000c	...qu..}........
	0310: 9400 000e f300 0015 b800 0017 ec00 0022	..............."
	0320: 6400 002b 3a00 002d dd00 0033 b600 0038	d..+:..-...3...8
	0330: 9900 003e e400 0045 2d00 004a 1800 004d	...>...E-..J...M
	0340: be00 0056 7c00 0059 b400 0063 2000 0069	...V|..Y...c ..i
	0350: 1200 006f 8400 0075 7600 007b e800 008b	...o...uv..{....
	0360: 3900 0009 da00 000b f600 000e f300 0013	9...............
	0370: b500 0016 b100 001e f900 0029 4100 002b	...........)A..+
	0380: 1e00 0031 9000 0037 c100 003b ce00 0041	...1...7...;...A
	0390: c800 0047 8600 004d be00 0053 7c00 0057	...G...M...S|..W
	03a0: 6400 005a c400 0060 3500 0066 1c00 006b	d..Z...`5..f...k
	03b0: 8e00 0071 7500 007d fe00 0009 da00 000b	...qu..}........
	03c0: f600 000e f300 0013 b500 0017 ec00 001e	................
	03d0: f900 0029 4100 002b c500 0031 9000 0037	...)A..+...1...7
	03e0: c100 003d f400 0044 2500 0047 8600 004d	...=...D%..G...M
	03f0: be00 0053 7c00 0059 b400 005f b000 0065	...S|..Y..._...e
Device info:
   Manufacturer: Samsung Electronics Co.,Ltd.
   Model: S3
   Device version: V1.11
   Serial number: 999EF260000000D5
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; microsoft.com/WMPPD: 10.0; microsoft.com/WMDRMPD: 10.1microsoft.com/WMPPD: 11.,; 
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   101b: Get partial object
   100b: Delete object
   100c: Send object info
   100d: Send object
   100f: Format storage
   1011: Self test device
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9810: Get object references
   9811: Set object references
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   9201: Report Added/Deleted Items
Events supported:
   None.
Device Properties Supported:
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd401: Synchronization Partner
Playable File (Object) Types and Object Properties Supported:
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3008: MS Wave
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 1, 2,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   3009: MP3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   300c: ASF
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 353,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   3801: JPEG
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc88: Height UINT32 data type range: MIN 0, MAX 1920, STEP 1 GET/SET
      dc87: Width UINT32 data type range: MIN 0, MAX 3072, STEP 1 GET/SET
   b901: WMA
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 353, 355,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba03: Abstract Audio Album
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 0,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type enumeration: 0, 1,  GET/SET
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX -1, STEP 1 READ ONLY
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  GET/SET
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 1913171968
      FreeSpaceInBytes: 942448640
      FreeSpaceInObjects: 5801
      StorageDescription: S3
      VolumeIdentifier: 999ef260000000d5
Special directories:
   Default music folder: 0x00008007
   Default playlist folder: 0x00008001
   Default picture folder: 0x00008008
   Default video folder: 0x00008009
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00008005
   Default album folder: 0x0000800a
   Default text folder: 0x00008006
MTP-specific device properties:
   Friendly name: S3
   Synchronization partner: &#65246;&#65514;&#65279;&#65514;&#65279;&#65514;&#65279;&#65514;&#65279;&#41185;
libmtp supported (playable) filetypes:
   RIFF WAVE file
   ISO MPEG-1 Audio Layer 3
   Microsoft Advanced Systems Format
   JPEG file
   Microsoft Windows Media Audio
   Ogg container format

Secure Time:
<DRMCLOCK type="status"><VALUE>#20090429 05:20:07Z#</VALUE><FLAG>DRM_CLK_SET</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">CgoKCgoKCgoKCgoKCgoKCgoKCgo=</UNIQUEID><PUBLICKEY private="1">DmY8gbX9MooJfiycb3dbArBgBxWlik9NLRGT7E6r5Lk2E5AT5ZRBKg==</PUBLICKEY><KEYDATA>ecWBoFjSzYF6q8WZR9gMnvki0q4=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>V59riGRAnvmAzriaIpx3vJZ02Yc36Mz6nwtYWjhd0FgsqpQP5VIRMw==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>ua4klifJHY6wbT1M9qa3aQ2Jur0=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.105.105</SECURITYVERSION><CERTIFICATE private="1">DmY8gbX9MooJfiycb3dbArBgBxWlik9NLRGT7E6r5Lk2E5AT5ZRBKgIEaWldIOD2VhCH645ZbQ7/SwtNtwnBNpJ7pPv9bf/mGz86oFwt7vJZcihh</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><FEATURES><CLOCK>2</CLOCK><SECURECLOCK><URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL><PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY></SECURECLOCK><METERING>1</METERING><LICENSE_ACQ>1</LICENSE_ACQ><LICENSE_SYNC>1</LICENSE_SYNC><ENCRYPTION>1</ENCRYPTION><SYMMETRIC_OPT>1</SYMMETRIC_OPT></FEATURES><LIMITS><MAXCHAINDEPTH>2</MAXCHAINDEPTH><MAXLICENSESIZE>10240</MAXLICENSESIZE><MAXHEADERSIZE>5120</MAXHEADERSIZE></LIMITS><PUBLICKEY>2hOkxOCK1QPe10JHYvfVUjYjLBMzXCftotZMbbB+VhO0gpWYnFSNJA==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>zVgOV3F4q2xlvMfFBZtW/YaNhE/9IBGpQpxDJG4cljg81O1sxP/KhA==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>1229</AUTH_ID><PUBLICKEY>8l60FgPW1vHhfaAFYkoYXMMHTFZCfCf98BXPcKJLbBjofB1fy8Bcbw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>LpLd030TMk4F6v2kAjf3LecPk0UOgCjPmQrGsKUfmyRBTRujDP3/LQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>YoS6xu8BvaENyvqIISjhFbO5wmakFMYg2/C8ALN0uuXvYRVe3JJZYw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
Segmentation fault

```
however it ends with a segmentation fault.

As for lsmod | grep fuse
- I get nothing

and sudo modprobe fuse
module fuse is not found

---

### Post by ricemark20 on 2009-05-09
> **tomcat2007 said:**
> Tried as a normal user initially, but since you mentioned running related items as root,  I get the same thing (mounting for root and starting nautilus & bash as root)  Nautilus shows filesystems in / but nothing in them.  Bash shows "D????????? ? ? ? ?                   ? New Songs"

Bash shows the same here.  Files can't be opened from Bash or Nautilus

---

### Post by buale on 2009-05-12
> **JR_Moneybags said:**
> I have pretty much the same problem as tomcat.

As far as diagnosing my device - I have problems at nearly every step.
Starting with mtp-detect

```
libmtp version: 0.3.6

Listing raw device(s)
   Found 1 device(s):
   Samsung: YP-S3 (04e8:5091) @ bus 0, dev 0
Attempting to connect device(s)
usb_claim_interface(): Operation not permitted
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.

```

Same situation with my YP-K5
Try manually unmount your device first and then run mtp-detect
After unmounting my device work with all players (amarok, gnomad2 rhythmbox)
It seems to me that libmtp has some problem with libusb (libmtp depend on libusb)
It's there a way to avoid automatic mounting of the device?
buale

---

### Post by AntoninSlejska on 2009-06-23
I can see the uploaded files after the following commands:```
antonin@antonin-laptop:~$ sudo mtpfs /home/antonin/s3 -o allow_other
antonin@antonin-laptop:~$ sudo mc /home/antonin/s3
```But the files are dislayed in red color and with question-mark before the filename. It is not possible to delete the files or copy files to the player.

---

### Post by Leviathan88 on 2009-11-29
Better late than never.

This is how I got my yp-s3 to work in UMS mode!  I have followed the instructions from page 1 comment #3 to the letter, which has my everlasting appreciation!  The only difference I made is to make the config.dat "dos-compatible" i.e. I did in terminal: ```
todos /path/to/config.dat
``` (type the following in a terminal for explanation)```
apt-cache show tofrodos
```  I am not certain of course but the thought occurred to me that the end of lines in this file may cause havoc, if the text-file config.dat was made on hardy/jaunty?

Anyway first you download the yp-s3 firmware from here: [http://media.generationmp3.com/gmp3/Firmwares/Samsung/SamsungS3/YP-S3%5b20081113092437%5d.zip](http://media.generationmp3.com/gmp3/Firmwares/Samsung/SamsungS3/YP-S3%5b20081113092437%5d.zip)  Still available as of writing this at: [http://www.anythingbutipod.com/forum/showthread.php?t=32690](http://www.anythingbutipod.com/forum/showthread.php?t=32690) (In firefox: ctrl+f type yp-s3 in the box).  Start up win media player 10 or greater, plug in your device (just ignore the synchronization dialogue.) into a windows computer, if you got one lying around?  Copy your S3.ROM and config.dat into the root of your S3 device.  Close win media player, unplug the device.  Shut it down and turn it on, wait for the upgrading firmware message to disappear and plug it into your *buntu box.  Now bash and nautilus behave the way I expect them too.  ;-)

```

sasha@engage:~$ dir /media/S3/
total 10M
-rwx------  1 sasha root 9.9M 2009-11-29 10:31 one_thousand_times.mp3
-rwx------  1 sasha root  296 2009-06-29 18:17 WMPInfo.xml
-rwx------  1 sasha root    6 2009-06-06 01:46 touch.txt
drwx------  2 sasha root 8.0K 2000-01-01 00:00 Albums
drwx------  2 sasha root 8.0K 2000-01-01 00:00 Datacasts
drwx------ 55 sasha root  16K 2000-01-01 00:00 Music
drwx------  3 sasha root 8.0K 2000-01-01 00:00 Pictures
drwx------  2 sasha root 8.0K 2000-01-01 00:00 Playlists
drwx------  3 sasha root 8.0K 2000-01-01 00:00 Recorded\ Files
drwx------  5 sasha root 8.0K 2000-01-01 00:00 SYSTEM
drwx------  2 sasha root 8.0K 2000-01-01 00:00 Texts
drwx------  2 sasha root 8.0K 2000-01-01 00:00 Video

```Just my 2cents.

---

### Post by Qchan on 2009-11-29
[b][color=darkred]
Thankfully this device works out of the box in Karmic Koala.
[/b][/color]

---

### Post by Leviathan88 on 2009-11-29
> **Qchan said:**
> [B][COLOR=darkred]
Thankfully this device works out of the box in Karmic Koala.
[/COLOR][/B]
That I didn't know.  Then again I haven't upgraded to Karmic yet (and probably will not for some time to come).  :D  Thanks anyway.  

Edit - That last bit equals to: I [COLOR=navy]*wait to see which way the cat jumps*[/COLOR]

---

### Post by asdfgt25t on 2012-08-06
end must surely know the names of the two known forms in the style statement that can enhance your personality and match your attireNaeem strengths can [vivienne westwood footwear](http://www.viviennewestwoodfootwear.com) be [vivienne westwood sales](http://www.viviennewestwoodfootwear.com) seen in their evening gowns that are made Simple elegant and timeless pieces that bring confidence in myself our products are the unusual [mens vivienne westwood shoes](http://www.viviennewestwoodfootwear.com/category/mens-vivienne-westwood-shoes/) eyes off the bonds of silk Vivienne is the Spitalfield flower blooms on [vivienne westwood boot](http://www.viviennewestwoodfootwear.com/category/vivienne-westwood-boot/) the uniforms of the materials and links but still ended centuries of historical [black](http://www.viviennewestwoodfootwear.com/tag/black/) events regardless by **vivienne westwood boots**  b trends in the transformation [vivienne westwood boots](http://www.viviennewestwoodfootwear.com) of traditional types in any way lose its appeal   **vivienne westwood sales**  c Vivienne Westwood pumps  carefully looks corset can be refined and intellectual perception  Vivienne Westwood Men Shoes  Among her favorite designers are [vivienne westwood footwear](http://www.viviennewestwoodfootwear.com/category/vivienne-westwood-footwear/) Alexander McQueen Vans Marc Jacobs Urban Outfitters Juicy Couture Louis Vuitton D  G free men Balenciaga and Rich  SkinnySo  Vivienne Westwood Shoes Sale  are just as cheap shoes Vivienne Westwood? Well these boots are not as expensive as you might already be [vivienne westwood and melissa shoes](http://www.viviennewestwoodfootwear.com/tag/vivienne-westwood-and-melissa-shoes/) thinking   Puedes USAR Etiquetas y las siguientes atributos HTML   acronym [vivienne westwood shoe](http://www.viviennewestwoodfootwear.com/category/vivienne-westwood-shoe/)   shares blockquote            FFSDKA122F 
 
 [melissa by vivienne westwood shoes McqueenBelagents  seiklejad.mithio.com](http://seiklejad.mithio.com/node/279684) 
 
 [melissa by vivienne westwood shoes  MarginFreeMall.com](http://marginfreemall.com/content/melissa-vivienne-westwood-shoes)

---

