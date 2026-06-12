---
title: "iPod doesn't automount in  Jaunty"
date: 2009-05-19
forum: Multimedia Software
---

### Post by m_memmory on 2009-05-19
I've installed Jaunty and have just one problem with it - when I connect my iPod 5G to it Ubuntu doesn't auto-mount the drive.  It used to on previous versions but doesn't anymore.  I've tried different cables & different USB ports but still the same - on the iPod it does show that it's charging so I know it is connected and if I run 
```
sudo fdisk -l
``` 

then I get the corresponding information to do with my iPod:

```
Disk /dev/sdc: 80.0 GB, 80026361856 bytes
84 heads, 62 sectors/track, 7502 cylinders
Units = cylinders of 5208 * 2048 = 10665984 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          13      128394    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13        7503    78022222    b  W95 FAT32
```

Now I can force my iPod to mount if I type in

```
sudo mount -t vfat -o rw /dev/sdc2 /media/ipod/
```

But then any program that I want to run that can have access to the iPod I have to run with sudo and I have to copy/delete files through the terminal which is rather annoying.

Is there anything that I can do to get this to auto-mount every time that I plug it in?  Every other USB device that I have (an external hard drive & a couple of memory sticks) all auto-mount as soon as they are connected so I don't know why my iPod isn't.

On a side note (not sure if this is indicative of a similar problem) I have found that Ubuntu only reads/detects one of my DVD drives - my DVD-RW drive doesn't seem to be recognised when I put anything in it.

---

### Post by ursus262 on 2009-05-19
I have this problem too.  A quick way round is to use the file manager (Dolphin in KDE).  This forces the ipod to mount.  Following on from that, the ipod interfaces normally with Jaunty.  Any ideas anyone?

---

### Post by jnutz on 2009-06-09
I'm also having this problem. Unfortunately Nautilus file manager doesn't seem to force the mount either, so I'm stuck. My iPod is the 4 gig nano.

---

### Post by dislocated on 2009-06-15
I have a 4 gig nano and it suddenly stopped showing up on the desktop in Jaunty and Rhythmbox couldn't see it either. In other words, it also wasn't automounting.

Couldn't figure it out since it used to work fine. The iPod seemed to be working OK. I unplugged and gave it a reset just in case, and then it automounted with the next plug-in. Go figure.

Hope this helps someone.

---

### Post by jnutz on 2009-06-17
After a reboot with the ipod plugged in it was mounted and I haven't had a problem since (yet). 

My problem now is that my music is on a network drive (smb) and gtkpod doesn't seem to recognize the drive even though it's mounted and shows in /media/

---

### Post by siabost on 2009-07-04
To add to this, I run Jaunty on two PCs. One an older Celeron single-core based one (but still quite fast)  and the other a brand new PC based around an AMD Athlon chip.

On the older machine my Nano 8Gb i-Pod auto-mounts perfectly every time & on the new one it doesn't at all! Howzat?

I'm going to try some of the temp fixes mentioned here & will report back.

EDIT:
My PC wont boot with the iPod plugged in - seems to get stuck trying to boot from it thinking it's a CD!
Dolphin doesn't force it to auto-mount either.
lshw in terminal produces this for my usbs:
 >     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd

---

### Post by mschering on 2010-05-19
I had the same problem. In my case the ipod was completely full. I mounted the ipod like described at the top of this post and removed one mp3 file. Then I unmounted it and unplugged the device.

Then I reattached it and it worked again! I did this with ubuntu 10.04

---

