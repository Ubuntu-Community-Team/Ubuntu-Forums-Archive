---
title: "Severe problems with drivers for Nvidia card (GeForce 9800 GT), (13.10, 64 bit)"
date: 2014-03-28
forum: Multimedia Software
---

### Post by cederfjard on 2014-03-28
Hi,

I'm running Ubuntu 13.10 on a Dell XPS 420, and I'm having tremendous difficulties trying to make the video card (Nvidia GeForce 9800 GT) work with any drivers at all.

With the default drivers (Nouveau, right?) it VERY occasionally works properly, similarly seldom the system starts and uses the motherboard's driver instead (which is the case as I'm writing this). Nine times out of ten though, it starts glitching pretty immediately after Grub, and after saying something about "GPU lockup" the computer hangs and the screen gets severly distorted: [https://dl.dropboxusercontent.com/u/9134494/distorted.jpeg](https://dl.dropboxusercontent.com/u/9134494/distorted.jpeg)

This has also been the case at every install (this is the fourth attempt, I've kept it pretty pristine so it's easier to troubleshoot), so I've had to set nomodeset every time to complete them.

I've tried to install other drivers for the card in an attempt to alleviate this, but that's always turned out even worse; I've never been able to boot to any graphical interface at all with any of them. I've tested the ones available at System Settings -> Software and Updates -> Additional Drivers, the relevant packages from the default repositories, the ones from the xorg-edgers PPA, and some straight from Nvidias website.

It would be very much appreciated if I could get either:

[LIST]
[*]Help on getting the default drivers to work consistently 
[*]Guidance to properly install other working drivers 
[*]Or any pointers at all as to where I may be failing 
[/LIST]
 Thanks.

Some info, please tell me if there's anything else that would be helpful to know:

sudo lshw -short
```

H/W path        Device      Class       Description
===================================================
                            system      Dell XPS420 ()
/0                          bus         0TP406
/0/0                        memory      64KiB BIOS
/0/400                      processor   Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
/0/400/700                  memory      32KiB L1 cache
/0/400/701                  memory      8MiB L2 cache
/0/1000                     memory      3GiB System Memory
/0/1000/0                   memory      1GiB DIMM DDR2 Synchronous 800 MHz (1,2 ns)
/0/1000/1                   memory      1GiB DIMM DDR2 Synchronous 800 MHz (1,2 ns)
/0/1000/2                   memory      1GiB DIMM DDR2 Synchronous 800 MHz (1,2 ns)
/0/1000/3                   memory      DIMM DDR2 Synchronous 800 MHz (1,2 ns) [empty]
/0/100                      bridge      82X38/X48 Express DRAM Controller
/0/100/1                    bridge      82X38/X48 Express Host-Primary PCI Express Bridge
/0/100/1/0                  display     G92 [GeForce 9800 GT]
/0/100/6                    bridge      82X38/X48 Express Host-Secondary PCI Express Bridge
/0/100/19       eth0        network     82566DC-2 Gigabit Network Connection
/0/100/1a                   bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                 bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2                 bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7                 bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                   multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                   bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1d                   bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                 bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                 bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7                 bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                   bridge      82801 PCI Bridge
/0/100/1e/a                 bus         TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
/0/100/1f                   bridge      82801IR (ICH9R) LPC Interface Controller
/0/100/1f.2                 storage     82801 SATA Controller [RAID mode]
/0/100/1f.3                 bus         82801I (ICH9 Family) SMBus Controller
/0/1            scsi0       storage     
/0/1/0.0.0      /dev/sda    disk        500GB WDC WD5002AALX-0
/0/1/0.0.0/1    /dev/sda1   volume      350MiB Windows NTFS volume
/0/1/0.0.0/2    /dev/sda2   volume      465GiB Windows NTFS volume
/0/2            scsi1       storage     
/0/2/0.0.0      /dev/cdrom  disk        DVD+-RW DH-16A6S
/0/3            scsi3       storage     
/0/3/0.0.0      /dev/sdb    disk        500GB ST3500620AS
/0/3/0.0.0/1    /dev/sdb1   volume      2929MiB Linux swap / Solaris partition
/0/3/0.0.0/2    /dev/sdb2   volume      462GiB Extended partition
/0/3/0.0.0/2/5  /dev/sdb5   volume      459GiB Linux filesystem partition
/0/3/0.0.0/2/6  /dev/sdb6   volume      3069MiB Linux swap / Solaris partition
/0/4            scsi6       storage     
/0/4/0.0.0      /dev/sdc    disk        1TB Desktop
/0/4/0.0.0/1    /dev/sdc1   volume      931GiB Windows NTFS volume
/0/5            scsi7       storage     
/0/5/0.0.0      /dev/sdd    disk        1TB SCSI Disk
/0/5/0.0.0/1    /dev/sdd1   volume      931GiB Windows NTFS volume
/0/5/0.0.1      /dev/sde    disk        1TB SCSI Disk
/0/5/0.0.1/1    /dev/sde1   volume      931GiB Windows NTFS volume
/0/5/0.0.2      /dev/sdf    disk        160GB SCSI Disk
/0/5/0.0.2/1    /dev/sdf1   volume      149GiB Windows NTFS volume
/0/6            scsi8       storage     
/0/6/0.0.0      /dev/sdg    disk        USB   HS-CF Card
/0/6/0.0.0/0    /dev/sdg    disk        
/0/6/0.0.1      /dev/sdh    disk        USB   HS-xD/SM
/0/6/0.0.1/0    /dev/sdh    disk        
/0/6/0.0.2      /dev/sdi    disk        USB   HS-MS Card
/0/6/0.0.2/0    /dev/sdi    disk        
/0/6/0.0.3      /dev/sdj    disk        USB   HS-SD Card
/0/6/0.0.3/0    /dev/sdj    disk        
/1              wlan0       network     Wireless interface

```

sudo lshw -c display
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G92 [GeForce 9800 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:fc000000-fcffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc80(size=128) memory:fde00000-fde1ffff

```

sudo jockey-text -l
```

kmod:nvidia_319_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_304 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_304_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_319 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)

```

---

### Post by kc1di on 2014-03-28
Hello Christian_Cederfj and welcome to Ubuntu,

You need the nvidia 304 driver for that card.
you can install it from a terminal by using this command:
```
sudo apt-get install nvidia-304
```
Note: you may have uninstall any other drivers you have already installed. 

Also note that if you seeing a problem in grub with video it's not being caused by the installed driver as that would not have been loaded at the grub screen.
I would suggest you may need to boot with the nomodeset  statement here's a page that tells you how to do that.
[http://askubuntu.com/questions/207175/what-does-nomodeset-do]("http://askubuntu.com/questions/207175/what-does-nomodeset-do")
and here:
[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by Bucky Ball on 2014-03-28
*Thread moved to **Multimedia & Video**.*

---

### Post by cederfjard on 2014-03-28
Hi Dave, thanks!

I'll try this out as soon as I get the chance. Just one thing:

> Note: you may have uninstall any other drivers you have already installed.

If I haven't personally installed any drivers after installing the OS, I don't have to worry about this, right?

---

### Post by cederfjard on 2014-03-28
Turns out nvidia-304 did the trick! I feel a little embarrassed, obviously I didn't try everything that was readily apparent...

Thanks again!

---

### Post by kc1di on 2014-03-28
Glad to be of help, enjoy ;)

---

### Post by Bucky Ball on 2014-03-28
Is it available in 'Additional Drivers'? (I think that's what it's called in a Ubuntu 13.10 desktop install.)

---

### Post by kc1di on 2014-03-28
> **Bucky Ball said:**
> Is it available in 'Additional Drivers'? (I think that's what it's called in a Ubuntu 13.10 desktop install.)

I've moved on to 14.04 but if I remember right they did away with additional drivers after 12.04 or 13.04.  also the default is nvidia-current which doesn't work with all the cards.

---

### Post by Bucky Ball on 2014-03-28
> **kc1di said:**
> ... also the default is nvidia-current which doesn't work with all the cards.

Gotcha. ;)

---

