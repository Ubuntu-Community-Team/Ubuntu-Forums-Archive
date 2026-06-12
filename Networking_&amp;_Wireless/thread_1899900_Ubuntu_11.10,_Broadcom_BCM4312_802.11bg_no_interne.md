---
title: "Ubuntu 11.10, Broadcom BCM4312 802.11b/g no internet connection"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by djehuti on 2011-12-24
Hi everyone, first time with Ubuntu. I only have an internet connection with Windows, so I can't use any Ubuntu package managers/downloaders to make it easier. A friend got me a downloadable form of ndiswrapper which I installed without errors, but now that it's installed I don't know what to do -- whether it's a program or a driver, or where it's located in Ubuntu now, I don't know. I've downloaded the Windows driver for the network controller, but since it's an .EXE, Ubuntu doesn't know how to implement it. What do I do to get the driver recognized in Ubuntu?

Also worth mentioning: I don't have the slightest idea how a tar file works (I've only used deb up to now), so if the solution comes through a tar, I'd appreciate step-by-step directions on how to unpack and run it. The last time I tried, the Makefile was a complete mess. Thanks.  ```
Additional information, if it helps:

0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Dell Device 000b
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information 
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting 
    Capabilities: [13c] Virtual Channel 
    Capabilities: [160] Device Serial Number 16-00-b4-ff-ff-44-3c-d2
    Capabilities: [16c] Power Budgeting 
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb



iwconfig  Wireless-Tools version 30
          Compatible with Wireless Extension v11 to v22.

Kernel    Currently compiled with Wireless Extension v22.

wlan0     Recommend Wireless Extension v21 or later,
          Currently compiled with Wireless Extension v22.

 iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm  
            Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
           
```EDIT: Solved. Turns out Wubi installs Ubuntu 64-bit by default, which my computer seems allergic to. Installed 32-bit, and everything's peachy. Thanks everyone for your help and patience.

---

### Post by gareththered on 2011-12-24
The Broadcom device is supported by Linux.  Have a read of:-

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I know it's difficult to get system set up without an Internet connection - a real chicken and the egg situation.  However, you may be able to download the deb files you need manually from another system or use Ethernet if that is available.

Good luck.

---

### Post by TBABill on 2011-12-24
Can you go to software sources and add your Ubuntu liveCD as a software source? If you can, those files are located on the CD that you need to enable the device (driver and firmware). 

Assuming you can add it as a source, then just ```
sudo apt-get update
```Then go to additional drivers, select the STA driver and click activate. Once it tells you it must restart, either restart OR you can ```
sudo modprobe wl
```Then try to connect about 30 seconds to a minute later.

---

### Post by TBABill on 2011-12-24
In the future if you boot a new Ubuntu version, just click activate on the STA driver and modprobe the driver. THEN when you install after your connection is working, when you first boot into the newly installed system your wireless will already be configured.

---

### Post by djehuti on 2011-12-26
Thanks for the replies. I installed Ubuntu using Wubi (downloaded via torrent), so I don't have a physical CD. Is that what liveCD is referring to, or is there some way to get the STA driver from a Wubi-based installation?

---

### Post by gareththered on 2011-12-26
You can mount the wubi installation file as with the loop device.

First mount the NTFS (Windows) partition from linux. For example if the Windows partition is '/dev/sda2' and you want to mount it temporarily on '/media/win' then use the command:
> sudo mkdir /media/win
sudo mount /dev/sda2 /media/winOnce this is mounted, you should be able to access the iso that wubi downloaded for you.  I believe that it should be in the same location as wubi.exe, but I haven't used wubi at all as I install from CD.
To mount the iso, use the 'loop' facility.  For example, if wubi.exe and the downloaded iso are in 'C:\wubi' and 'C:\' is still mounted on '/media/win', you can mount the iso on '/media/iso' using:-
> sudo mkdir /media/iso
sudo mount -o loop /media/win/wubi/<whatever the iso is called> /media/isoOnce this is done, you should be able to follow the above instructions to install STA.

Bear in mind, that I haven't used wubi, so if this post doesn't work, please accept my apologies!
Good luck.

---

### Post by djehuti on 2011-12-27
Thanks again for the reply. My Windows is installed on C:, and my Ubuntu on G:. I tried mounting from /dev/sda2, but it said there's no such file. Is there another way to find out where my C: files are?

---

### Post by gareththered on 2011-12-27
If you open up a terminal and type:
```
sudo fdisk -l
```you will be presented with a list of all drives and the partition on those drives.  For example, if I type the above command on my laptop, I get:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4db0465

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      821247      409600   27  Hidden NTFS WinRE
/dev/sda2          821248   205621247   102400000    7  HPFS/NTFS/exFAT
/dev/sda3       205623294   976768064   385572385+   5  Extended
/dev/sda5       205623296   267063295    30720000   83  Linux
/dev/sda6       267065344   275257343     4096000   82  Linux swap / Solaris
/dev/sda7       275273838   946067849   335397006   83  Linux
/dev/sda8       946067913   976768064    15350076   83  Linux
```which tells me I have one 500Gb hard drive (which I know anyway!) that has been partitioned into 7 partitions.  The first is the hidden Windows recovery partition, the second is my Windows partition, third is an Extended partition which holds more partitions; which are the fourth a Linux partition, fifth a Linux swap partition and the last two are Linux too.
From the above, I can see that my main Windows partition (the C:\ drive) is '/dev/sda2'.
If you run the command, you should see a similar result, but with different partitions and partition numbers.  If you struggle, paste the output of the command here.

---

### Post by westie457 on 2011-12-27
> **djehuti said:**
> Thanks again for the reply. My Windows is installed on C:, and my Ubuntu on G:. I tried mounting from /dev/sda2, but it said there's no such file. Is there another way to find out where my C: files are?

Hi, this might sound confusing as I do not have a Wubi install.

Your Windows file-system is already mounted. You will find it by opening File Browser (usually Nautilus) and looking for /host. Be careful what you do in the Windows installation as you have full access to delete any and all files. Linux does not understand Windows file permissions and vice-versa.

Once you have located the .iso file right-click and select 'open with Archive Mounter', then navigate your way to /pool/restricted/b/bcmwl. Copy the .deb package to the Desktop. Double-click on the icon and it will install with the Software Center.

Reboot and left-click on 'Network-Manager' icon at the top of the screen and you should see a list of available networks.

Any problems post back here and we will try something else.

ps If not alreadt mentioned 'NDISwrapper' will not work and it needs to be removed.

---

