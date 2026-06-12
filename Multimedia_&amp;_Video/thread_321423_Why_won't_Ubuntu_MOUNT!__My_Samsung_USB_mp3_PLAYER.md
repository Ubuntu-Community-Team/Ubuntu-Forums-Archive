---
title: "Why won't Ubuntu MOUNT?!  My Samsung USB mp3 PLAYER?"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by Ubuntu Joe on 2006-12-18
All right . . . I can't figure this out AT ALL!

I just bought a brand new Samsung YP-U2J because everyone said how "great' in worked in Ubuntu . . . Unfortunately, I can't get Ubunt to even NOTICE when I insert it . . . much less MOUNT IT!!  I think these guys are FAT 32, so they should be a piece of cake, right?  I've tried TWO now right out of the box, and neither seems to want to work with me . . . Here's what dmsg gives me:

```
[17180047.632000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[17180047.764000] usb 4-1: configuration #1 chosen from 1 choice
[17180047.948000] usbcore: registered new driver libusual
[17180047.988000] Initializing USB Mass Storage driver...
[17180047.988000] scsi0 : SCSI emulation for USB Mass Storage devices
[17180047.988000] usb-storage: device found at 2
[17180047.988000] usb-storage: waiting for device to settle before scanning
[17180047.988000] usbcore: registered new driver usb-storage
[17180047.988000] USB Mass Storage support registered.
[17180052.988000] usb-storage: device scan complete
[17180053.212000] usb 4-1: USB disconnect, address 2

```

Help a brutha out!  I needs my TUNES!!

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by aysiu on 2006-12-19
Plug it in and then post the output of these commands: ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Ubuntu Joe on 2006-12-19
```
thom@ubuntu-joe:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         122      979933+  82  Linux swap / Solaris
/dev/hda2             123        1581    11719417+  83  Linux
/dev/hda3            1582        3648    16603177+  83  Linux

```


```
thom@ubuntu-joe:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              12G  2.5G  8.1G  24% /
varrun                252M   80K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  112K  9.9M   2% /proc/bus/usb
udev                   10M  112K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-10-386/volatile
/dev/hda3              16G  2.3G   13G  16% /home
/dev/hdc              424M  424M     0 100% /media/cdrom0

```


```
thom@ubuntu-joe:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=c6b9ab89-7bec-44ad-aa31-0b21dec6d25b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=4d6a39ad-a776-4e6c-925b-76ca16a183c9 /home           ext3    defaults        0       2
# /dev/hda1
UUID=0a59fcaf-7f96-4bfa-83aa-332a720a770a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```


THANK YOU!!!

---

### Post by aysiu on 2006-12-19
And it was plugged in physically when you ran that first command? Usually, even if it's not mounted, it'll appear in the list of devices from *sudo fdisk -l*

---

### Post by Ubuntu Joe on 2006-12-19
would you like the *entire* list?  I only copied what I thought applied to the USP devices . . . I could have missed something . . .

---

### Post by aysiu on 2006-12-19
> **saalota said:**
> would you like the *entire* list?  I only copied what I thought applied to the USP devices . . . I could have missed something . . .
Yes. Please post the entire output of the ```
sudo fdisk -l
``` command. Thanks.

---

### Post by Ubuntu Joe on 2006-12-19
I'll have to wait until I get home, but I'll hit you then . . . Thx . . .

---

### Post by Ubuntu Joe on 2006-12-19
this really is everything . . .

```
thom@ubuntu-joe:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         122      979933+  82  Linux swap / Solaris
/dev/hda2             123        1581    11719417+  83  Linux
/dev/hda3            1582        3648    16603177+  83  Linux

```

---

### Post by Craig Caldwell on 2006-12-20
> **saalota said:**
> this really is everything . . .

```
thom@ubuntu-joe:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         122      979933+  82  Linux swap / Solaris
/dev/hda2             123        1581    11719417+  83  Linux
/dev/hda3            1582        3648    16603177+  83  Linux

```

You might want to try lsusb to see if your player shows up.

---

### Post by Ubuntu Joe on 2006-12-20
So . . .

```
sudo lsusb
```

??

---

### Post by Craig Caldwell on 2006-12-20
> **saalota said:**
> So . . .

```
sudo lsusb
```

??

this is my out put when I type lsusb into a terminal.

```
  craig@craig-desktop:~$ lsusb
Bus 002 Device 003: ID 040d:6205 VIA Technologies, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000  
craig@craig-desktop:~$ 

  
```

---

### Post by Ubuntu Joe on 2006-12-20
And here"s what that gets me:

```
thom@ubuntu-joe:~$ sudo lsusb
Password:
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

:( 

Is there no hope for me?

---

### Post by Ubuntu Joe on 2006-12-20
All right, this is bizaar . . . When I first plug the device in, i get this:

```
thom@ubuntu-joe:~$ sudo lsusb
Bus 004 Device 005: ID 04e8:5054 Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
```

**Then,** a few seconds later, I get this:

```
thom@ubuntu-joe:~$ sudo lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
```

What gives?!?!

](*,)

---

### Post by Craig Caldwell on 2006-12-21
> **saalota said:**
> All right, this is bizaar . . . When I first plug the device in, i get this:

```
thom@ubuntu-joe:~$ sudo lsusb
Bus 004 Device 005: ID 04e8:5054 Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
```

**Then,** a few seconds later, I get this:

```
thom@ubuntu-joe:~$ sudo lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
```

What gives?!?!

](*,)

Ok here's the deal.
You are going to have to go to the Samsung international web site and figure out how to flash your player with an international firmware.
This will allow your player to mount under linux.
I had to do the same thing with my iriver t10.
Your player is probably set for MTP and you need it to be UMS.
Best of luck.

---

### Post by Ubuntu Joe on 2006-12-21
I *thought *it might be a firmware issue!

But, how, oh how, will I flash the firmware, if it won't mount?!?!?

Don't tell me . . . I have to do it under Windows?

Ick.

---

### Post by Ubuntu Joe on 2006-12-21
Anyone like to guess what?

Samsung hasn't yet released a firmware update for my model of mp3 player . . . So, does that mean I'm just out of luck?

---

### Post by Craig Caldwell on 2006-12-21
> **saalota said:**
> Anyone like to guess what?

Samsung hasn't yet released a firmware update for my model of mp3 player . . . So, does that mean I'm just out of luck?

The firmware I used for my iriver t10 is actually from the Australian site.
It won't be a upgrade per-say but a move from restrictive firmware to a drag and drop firmware.
You just need to search samsung enthusiast sites for tips.
I did read on another forum that some one has flashed their player and others had UMS firmware out of the box.

good luck.

---

### Post by Ubuntu Joe on 2006-12-22
Grumble . . .

But thatnks for all your help!

I'll see what I can do . . .

---

### Post by xyzz on 2006-12-25
try remove ehci_hcd module and plug it in again

sudo rmmod ehci_hcd

---

### Post by ldbooth on 2007-01-10
I am having a similar problem, with a Samsung YP-U1 mp3 player (usb connection). Mine was working fine, but I did some updates and uninstalled banshee (i think the cause). 
When I do
```
sudo fdisk -l
```

My output is:

```
Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1873    15044841   83  Linux
/dev/hda2            1874        1991      947835   82  Linux swap / Solaris
/dev/hda3   *        1992        3516    12249562+   c  W95 FAT32 (LBA)
/dev/hda4            3517        3647     1052226    c  W95 FAT32 (LBA)

Disk /dev/sda: 1041 MB, 1041367040 bytes
227 heads, 56 sectors/track, 160 cylinders
Units = cylinders of 12712 * 512 = 6508544 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         160     1016932    b  W95 FAT32

```

So that may help your case, but what I want to know is or how to mount this guy from here, or tell him to always mount.

My results: I got it up, just by executing:

```
gnome-volume-manager
```

With this method I show a different Icon than before (a HDD instead of an Ipod)

---

### Post by Ubuntu Joe on 2007-01-11
I've tried all your ideas . . . still no dice . . . was it really a good idea to:

sudo rmmod ehci_hcd???

---

### Post by xyzz on 2007-01-24
> **saalota said:**
> I've tried all your ideas . . . still no dice . . . was it really a good idea to:

sudo rmmod ehci_hcd???

you can still load it back with 
```
modprobe ehci_hcd
```
but some of my usb devices have problems with ehci, and removing that module solved my problem with them

---

### Post by TheKiteGuy on 2007-02-06
I've just been having exactly the same problems for the last two hours (device appearing for about five seconds and then disconnected). After about an hour, I'd decided that the Samsung was broken, but thankfully, trial and error worked and it's now working again!

Here's what I did (hopefully some of this might help you and eliminate dead ends):
I'd already upgraded the firmware to version 2.45 US. About a month ago device would automount fine with Edgy whenever I plugged it in (I had installed hal and hal-device-manager many months previously which might have been how this was automounting). Since last month I'd installed about 100 automatic upgrades including various gnome, gtk and kernel applications. Today, when I tried to plug in device it didn't mount like it used to. I suspect that one of the upgrades was responsible for breaking the behaviour.

I'd read about the UMS options on the mp3 players settings menu. I'd tried both ON and OFF. In the end UMS Only = Off worked (haven't checked whether On also works or not).

As suggested above, I tried various combinations of rmmod the module and modprobe the same module before/ during/ after plugging the device in (desperation was setting in) and still couldn't get things to work. 

I'd read about pressing the escape/return button on the device as it was connecting (in the end this was not necessary and was just a red herring).

I installed usbmount from synaptic. When I installed it, when I plugged in the device I got SCSI error 0x70000 related to ehci_hcd displayed when I typed dmesg in a terminal. 

I again tried various combinations of rmmod the module and modprobe the same module and things were still not working. 

I then rebooted the PC with the device not connected. I Reset the device with a pin on the small hole at the bottom. In a terminal, I "sudo rmmod ehci_hcd" and entered the root password. I then plugged in the device. lsusb then showed the device connected permanently (not just for five seconds) and the device reported "connecting" and then "connected". An ipod icon then appeared on the desktop and I was once more able to copy across files.

Hope this helps. I'm not sure whether it was usbmount or the starting again with a clean reboot  before removing the module or both that got things working again.

---

### Post by Ubuntu Joe on 2007-02-06
Wow!

This thing's been sitting under my 'puter table for like two months . . . making me sad . . . I am re-inspired to start meddling with the thing again . . .

Any chance you could help me update the firmware?  Samsung hasn't released any updated for my model . . .

:guitar:

---

### Post by TheKiteGuy on 2007-02-06
Sorry, forgot to mention earlier that my model is the YP-Z5. Your description tied up perfectly with the symptoms I was getting, so forgot that the model was different. I'm pretty sure that it's not a firmware issue, but an issue with the kernel drivers as you were getting exactly what I was getting with the brief connection appearing in lsusb for e.g. five seconds before disconnect. Mine worked previously with the pre-loaded firmware (0.10) and new firmware (2.45) and only stopped working after I updated lots of system files.

Elsewhere on the internet, it appears other people can access your model as a flash drive  (UMS) on Linux so it should work. Have you tried installing usbmount and looking at the last few lines of dmesg shortly after you connect it?

I had a quick look for your mp3 player on the Samsung website and there seems to be an update to the firmware to version 1.352 in Europe:
[http://www.samsung.com/uk/support/productsupport/download/Model_Select2.aspx?type=Digital+Audio+Player&subtype=Flash+Memory&model=YP%2DU2Q&fileType=FM&LSSI=%2Fuk%2Fmodule%2Fssi%2Fleft%2Flmenu%5Fdigitalaudioplayer%5Fflashmemory%2Esec&RSSI=%2Fuk%2Fmodule%2Fssi%2Fright%2Frmenu%5Fdigitalaudioplayer%2Esec]("http://www.samsung.com/uk/support/productsupport/download/Model_Select2.aspx?type=Digital+Audio+Player&subtype=Flash+Memory&model=YP%2DU2Q&fileType=FM&LSSI=%2Fuk%2Fmodule%2Fssi%2Fleft%2Flmenu%5Fdigitalaudioplayer%5Fflashmemory%2Esec&RSSI=%2Fuk%2Fmodule%2Fssi%2Fright%2Frmenu%5Fdigitalaudioplayer%2Esec")

When you can connect to your device, you can update your firmware. I updated my firmware by following the instructions here:
[http://www.anythingbutipod.com/forum/showthread.php?t=4134]("http://www.anythingbutipod.com/forum/showthread.php?t=4134")

---

### Post by Ubuntu Joe on 2007-02-08
Sweet, sweet Jesus . . .

At long last I am able to mount this blasted little device!!!

First of all the eople at Samsung are **_*CLUELESS!!!!!*_**

They've finally added a firmware updater for this *_**utterly**_* premature device . . . and guess what . . . the American firmware upgrader takes it from  a v.1.36 to a v. 1.36 . . . . that's right, no change!  But, for some reason, the European firmware updater you gave me, TheKiteGuy, upgrades it to a v. 3.8 something . . . fabulous!

Every thing's working great but one thing . . . after the total over-haul the Euro Firmware updater gave my device, I don't have Radio anymore . . . bazaar. . . . but I'm not one to look a gift horse in the mouth!  I'm mostly a  "subway rocker" anyway . . . so, no radio's a-okay!!!

Thanks, TheKiteGuy . . . RESOLVED!!!!!!!  (with a wrinkle)

:guitar:

---

