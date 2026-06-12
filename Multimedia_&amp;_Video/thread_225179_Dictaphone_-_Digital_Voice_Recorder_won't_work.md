---
title: "Dictaphone - Digital Voice Recorder won't work"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by kayas80 on 2006-07-29
I am having problems connecting an Olympus VN-960PC digital voice recorder to my PC with a USB 2.0 cable.

When the dictaphone is connected to my computer via the USB cable a message appears on the dictaphone stating it is connected to the PC. Ubuntu however doesn't do anything i.e.  it doesn't show the device under Computer, or it doesn't auto-load a folder as it does when a USB pen drive is connected, for example.

I have gone to System > Preferences > Removable Drives and Media to make sure it is set to automount, which it is. When I go to the console I do have a glimmer of hope though: 

```

kayas80@kayas80:~$ lsusb
Bus 005 Device 008: ID 07b4:020d Olympus Optical Co., Ltd Digital Voice Recorder VN-240PC
Bus 005 Device 002: ID 0424:a700 Standard Microsystems Corp.
Bus 005 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0518:0002 EzKEY Corp.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000

``` 

So it is recognised but I can't interact with the device. Does anyone have a suggestion as to how I might be able to get it load the device so I can copy audio files from dictaphone to PC? This thread offers some ideas, but I don't really understand it: [http://www.ubuntuforums.org/showthread.php?t=137369&highlight=digital+voice+recorder](http://www.ubuntuforums.org/showthread.php?t=137369&highlight=digital+voice+recorder)

Many thanks

---

### Post by christhemonkey on 2006-07-29
Try typing this into a terminal:
```
sudo mkdir /media/dictaphone
sudo mount -t vfat /dev/sdb1 /media/dictaphone 
```

Replacing /dev/sdb1 and vfat with the actual usb location and vfat with the actual filesystem.

---

### Post by kayas80 on 2006-07-29
> **christhemonkey said:**
> Try typing this into a terminal:
```
sudo mkdir /media/dictaphone
sudo mount -t vfat /dev/sdb1 /media/dictaphone 
``` 
Replacing /dev/sdb1 and vfat with the actual usb location and vfat with the actual filesystem.

How do I find out what type of file system it is, also how do I find out the USB location? thanks

---

### Post by christhemonkey on 2006-07-29
Well, most usb type memory sticks do use fat32 (which is the vfat driver).
As for finding out where the usb location is, 
there is probably an easy way, but i dont know it.
So i just use trial and error (note: usb device nodes are from /dev/sda1 - /dev/sdz9999, so sd then a letter and a number)

---

### Post by kayas80 on 2006-07-29
> **christhemonkey said:**
> Well, most usb type memory sticks do use fat32 (which is the vfat driver).
As for finding out where the usb location is, 
there is probably an easy way, but i dont know it.
So i just use trial and error (note: usb device nodes are from /dev/sda1 - /dev/sdz9999, so sd then a letter and a number)

I'm not too sure how to do that. Does anyone know of an easy way to find out?

---

### Post by christhemonkey on 2006-07-30
```
fdisk -l /dev/sd* 
```
This should give you several sets of output, one of which will look like this:

```
Disk /dev/sda: 1048 MB, 1048313856 bytes
33 heads, 61 sectors/track, 1017 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1017     1023580    b  W95 FAT32
```

For that example, the driver is vfat and the usb device node is /dev/sda1
Any help needed, just let us know.

---

### Post by kayas80 on 2006-07-31
> **christhemonkey said:**
> ```
fdisk -l /dev/sd* 
``` This should give you several sets of output, one of which will look like this:

```
Disk /dev/sda: 1048 MB, 1048313856 bytes
33 heads, 61 sectors/track, 1017 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1017     1023580    b  W95 FAT32
``` 
For that example, the driver is vfat and the usb device node is /dev/sda1
Any help needed, just let us know.



I tried that but no luck. There are appear to be no devices starting with S*

---

### Post by christhemonkey on 2006-07-31
That is to say a lower case s?
I would find it very strange for there to be no devices using any of the /dev/sd*'s.

---

### Post by kayas80 on 2006-07-31
> **christhemonkey said:**
> That is to say a lower case s?
I would find it very strange for there to be no devices using any of the /dev/sd*'s.



Here was what it returns:

```
kayas80@kayas80:~$ fdisk -l /dev/s
sequencer   shm/        sndstat     stdin
sequencer2  snd/        stderr      stdout

```

---

### Post by Zyphrexi on 2006-09-28
this probably has absolutely no bearing... but i plugged in a ws-100 and it just worked.

---

