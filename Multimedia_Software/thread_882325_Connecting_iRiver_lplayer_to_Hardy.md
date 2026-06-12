---
title: "Connecting iRiver lplayer to Hardy"
date: 2008-08-06
forum: Multimedia Software
---

### Post by devosion on 2008-08-06
I just purchased myself an iRiver lplayer and finding it a little harder than usual to get the device connected. The lplayer comes with two usb configurations MSC and MTP. The device came pre-configured for MTP, but shortly after getting it connected to my usb I changed it to MSC so I can read it as a mass storage device. Unfortunately though when I chose to transfer data the lplayer acts like it gets connected but ubuntu does not mount the device. I've browsed the lplayers page on the iriver site but there is no additional information.

What is noteworthy is that lsusb does display my lplayer. So at the very least it is being recognized. Any ideas how I can mount it so I can copy files?

> Bus 005 Device 022: ID 4102:1042 iRiver, Ltd. 

Went ahead and gave the mtp-tools a shot and changed the lplayer back to mtp compatibility. Initial mtp-detect displays only:

> Attempting to connect device(s)
Detect: No Devices have been found


Running it as root is a different story altogether:

> 
Attempting to connect device(s)
Device 1 (VID=4102 and PID=1142) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 4102
   idProduct: 1142
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Microsoft device descriptor 0xee:
        0000: 1203 4d00 5300 4600 5400 3100 3000 3000   ..M.S.F.T.1.0.0.
        0010: fe00                                      ..
Microsoft device response to control message 1, CMD 0xfe:
        0000: 2800 0000 0001 0400 0100 0000 0000 0000   (...............
        0010: 0001 4d54 5000 0000 0000 0000 0000 0000   ..MTP...........
        0020: 0000 0000 0000 0000                       ........
Microsoft device response to control message 2, CMD 0xfe:
        0000: 2800 0000 0001 0400 0100 0000 0000 0000   (...............
        0010: 0001 4d54 5000 0000 0000 0000 0000 0000   ..MTP...........
        0020: 0000 0000 0000 0000                       ........
Device info:
   Manufacturer: iriver
   Model: iriver E100
   Device version: TP-0.31-N-ENG
   Serial number: 4FDD98183679F5CAF3C86A9B2FE5A30D
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; microsoft.com/WMDRMPD: 10.1; microsoft.com/WMPPD: 10.0;
   Detected object size: 64 bits


...additional information from the command is in my attached file. So at this point im tempted to switch to MTP and try to get rhythmbox to detect and write to and from the device. Unfortunately though im back to a stand still as to what to do. Please assist.

---

### Post by wolfen69 on 2008-08-06
what is the drive formatted as? it's not something proprietary, is it?

do ```
sudo fdisk -l
``` and post here what comes up.

---

### Post by devosion on 2008-08-07
This is what I got after running that command:

> 
Disk /dev/sdb: 3961 MB, 3961520128 bytes
122 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 7564 * 512 = 3872768 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?           1           1           0    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 255, 0) logical=(0, 0, 1)
Partition 1 has different physical/logical endings:
     phys=(0, 0, 0) logical=(567816, 114, 4)
Partition 1 does not end on cylinder boundary.


I had to switch back to MSC in order to run this otherwise lsusb wasn't detecting it as MTP.

---

### Post by devosion on 2008-08-07
bumping for a chance

---

### Post by therblack on 2008-08-08
Hi,

I had the same problem...I kind of got around it by mounting the player manually via something like:

sudo mkdir /media/lplayer/
sudo mount -t vfat -o sync,uid=XXX,gid=XXX /dev/sdc /media/lplayer/

where XXX is my user id and /dev/sdc is where it mounted via usb (you may need to put /dev/sdb judging from your post).

It is strange!  I tried reformating the disk using gparted, but that didn't work (when I unplugged it and plugged it back in, the disk was again unrecognized by linux).

Somewhat differently, my playlists seem to be all out of order (track 5 followed by track 1 etc).  Have you noticed this?

cheers

Richard

---

### Post by crabclaw on 2008-10-14
I have the exact same problem, lplayer not recognised by ubuntu, anyone find a solution to this problem?

It's being recognised but it's not being mounted. and I don't know what to do.

---

### Post by happyisland on 2008-10-14
I also have the same problem. I have to manually mount the dang thing every time I connect it, which is a hassle. I had hoped the new HAL updates would have helped, but they didn't.

---

### Post by ajcham on 2008-10-18
> **crabclaw said:**
> I have the exact same problem, lplayer not recognised by ubuntu, anyone find a solution to this problem?

It's being recognised but it's not being mounted. and I don't know what to do.

I too have this issue.  I just received my Lplayer this morning and it worked fine with MSC connection.  I wanted to try out MTP, which didn't work so changed back to MSC only to find that this no longer worked either.

Mounting the disk manually does work for me (see therblack's post above).  It would be a pain having to do this every time so I've added a launcher icon to my desktop - I now just have to click the icon before navigating to the appropriate folder.

Not sure why this problem occurs - although it may be that the device formats itself in a non-standard way.

It's a real shame because I'm almost perfectly satisfied with my player - were it not for this little niggle and the fact that it doesn't sort my album tracks properly.

---

### Post by vovkasm on 2009-02-25
Same trouble: after switch to MTP and back, lplayer does not auto mounted with ubuntu.
Solution:
```

(if you iriver device /dev/sdg)
$ sudo gparted /dev/sdg
(make partition table and fat32 partition)

```
Reconnect device and whoa, it's mounted now ;-)

---

### Post by therblack on 2009-02-25
Yeah, you know I tried this (or at least I thought I did), and it worked great but then it stopped working.  I can't quite remember, but I think it reverted back to the old behaviour after I turned it off and then back on.

I'll try it tonight.  Thanks

---

