---
title: "HOWTO: Install nVidia 260.19.12"
date: 2010-10-15
forum: Multimedia Software
---

### Post by ncohea on 2010-10-15
nVidia came out with new drivers yesterday that are not in the nvidia-current metapackage. I don't care what card you have, this [module drives it]("http://www.nvidia.com/object/linux-display-amd64-260.19.12-driver.html"). What worked for me may not necessarily work for everyone, as I am not an oracle with respect to your particular system configuration. This howto will be done in broad strokes. Down to business. For this howto, I will assume two things: first, that you download the nVidia installer to /home/username; second, that your prior setup was having nvidia-current installed!

Things we want installed
```
build-essentials linux-headers-generic linux-source
```

Thing we do NOT want installed
```
xserver-xorg-video-nouveau
```

Paranoid stuff we'd like to do just in case the above doesn't work (as it did not for me): sudo gedit /etc/modprobe.d/blacklist.conf

Somewhere in the file, add the line "blacklist nouveau"

PRINT THESE INSTRUCTIONS NOW BEFORE YOU KILL YOUR X SERVER

Now, I installed by doing (from my home user directory)

```
sudo stop gdm
sudo apt-get remove nvidia-current
sudo ./NVIDIA-Linux-x86_64-260.19.12.run -a
reboot
```

This stops the X server, removes the potentially conflicting current drivers you have, installs the new driver (and -a accepts the license agreement so that we don't get prompted), and reboots.

If this does not work, you can rollback from a LiveCD or the recovery mode with (again, from your home user directory)

```
sudo ./NVIDIA-Linux-x86_64-260.19.12.run --uninstall
sudo apt-get install nvidia-current
reboot
```

If this is incomplete, my apologies. I am just posting what worked for me.

---

### Post by Grig on 2010-10-15
1. I think you mean "build-essential" without the "s" at the end
2. I tried to purge the nouveau package but 

```
The following packages will be REMOVED:
  kdesudo{u} update-manager-kde{u} xserver-xorg-video-nouveau
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 602kB will be freed.
The following packages have unmet dependencies:
  xserver-xorg-video-all: Depends: xserver-xorg-video-nouveau but it is not going to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     xserver-xorg-video-all

```

I don't think I want that.

---

### Post by PRC09 on 2010-10-15
You could just add the ppa for x-swat....


[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick)

---

### Post by chrisinspace on 2010-10-19
> **Grig said:**
> 1. I think you mean "build-essential" without the "s" at the end
2. I tried to purge the nouveau package but 

```
The following packages will be REMOVED:
  kdesudo{u} update-manager-kde{u} xserver-xorg-video-nouveau
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 602kB will be freed.
The following packages have unmet dependencies:
  xserver-xorg-video-all: Depends: xserver-xorg-video-nouveau but it is not going to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     xserver-xorg-video-all

```

I don't think I want that.

If I understand correctly, xserver-xorg-video-all is a metapackage of device-specific drivers, not Xorg itself.  It is ok to remove because you aren't going to use any of the xorg drivers; you are going to use the nVidia proprietary driver.

Has anyone else had success with this method?  I have tried using the default "Additional Drivers" supplied by Ubuntu and the x-swat repository, but I keep having the same issue.  Everything works great except many of the GUI elements are HUGE.  The fonts are gigantic.  I can reduce some of them in the system settings, but even after decreasing all available settings to 6pt, they are too big and some fonts aren't affected at all and continue to be enormous.  Some other things like the Firefox toolbars are are also too big.  This is not an issue with the Nouveau driver.

---

### Post by frikkiethirion on 2010-10-19
Good day,
I've installed Ubuntu 10.10 (Maveric) and nvidia-current. I'm running an Intel Core Duo motherboard with quad core processor. My video card is the Leadtek 210 board with the nvidia 210 (Also known as GT218) GPU.

My card (or card+motherboard) doesn't seem to work with the nVidia propriety drivers. If I explicitly load the vesa or nouveau kernel modules and specify them in the Xorg.conf, X launches fine.

The file: /etc/modprobe.d/nvidia-graphics-drivers.conf makes sure that nouveau is blacklisted, so, during a normal boot the nvidia driver should load and X should start with nvidia propriety driver. (nvidia specified as driver in xorg.conf)

When the nvidia kernal module is loaded, syslog has the following entry:

Oct 16 21:37:16 huis kernel: [    8.263941] nvidia: module license 'NVIDIA' taints kernel.
Oct 16 21:37:16 huis kernel: [    8.263945] Disabling lock debugging due to kernel taint
Oct 16 21:37:16 huis kernel: [    9.164534] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 16 21:37:16 huis kernel: [    9.164547] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Oct 16 21:37:16 huis kernel: [    9.164721] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010


Then, when X loads:
Oct 16 22:00:44 huis kernel: [  175.466853] NVRM: RmInitAdapter failed! (0x27:0x28:1046)
Oct 16 22:00:44 huis kernel: [  175.466861] NVRM: rm_init_adapter(0) failed

Some forums suggest that I must add 'vmalloc=192MB' to the kernel boot line. This I've done, but it makes no difference.
I've reported the issue on the the nvidia forum, but it seems that they do not care about supporting the 210 card. 
([http://www.nvnews.net/vbulletin/showthread.php?p=2273650#post2273650](http://www.nvnews.net/vbulletin/showthread.php?p=2273650#post2273650))

From the syslog, I see that the card is placed on interrupt 16. If I look at /proc/interrupts, I see the following:
~$ more /proc/interrupts 
           CPU0      CPU1       CPU2       CPU3       
 16:        102        106        321        323   IO-APIC-fasteoi   uhci_hcd:
usb5, hda_intel, hda_intel
It seems asif USB is also on interrupt 16. I don't know if the video card will be 
happy about this.

Looking at what is reported about the card, the bios version cannot be resolved.
I don't know if this is an issue:
~$ cat /proc/driver/nvidia/cards/0 
Model:           GeForce 210
IRQ:             16
Video BIOS:      ??.??.??.??.??
Card Type:       PCI-E
DMA Size:        32 bits
DMA Mask:        0xffffffff
Bus Location:    0000:01.00.0

If anybody has any suggestions of what else to try, I'll be happy to test it.
Regards,
Frikkie Thirion

---

### Post by ratcheer on 2010-10-19
> **PRC09 said:**
> You could just add the ppa for x-swat....


[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates?field.series_filter=maverick")

That's what I would do. But 260.19.06 has been working just fine, for me, so I'm not going to mess with it.

Tim

---

### Post by frikkiethirion on 2010-10-25
> **frikkiethirion said:**
> Good day,
I've installed Ubuntu 10.10 (Maveric) and nvidia-current. I'm running an Intel Core Duo motherboard with quad core processor. My video card is the Leadtek 210 board with the nvidia 210 (Also known as GT218 ) GPU.

My card (or card+motherboard) doesn't seem to work with the nVidia propriety drivers. If I explicitly load the vesa or nouveau kernel modules and specify them in the Xorg.conf, X launches fine.

I've tested a nVidia GT250 in the same machine, without changing the  configuration, and that works 100% with the propriety 'nvidia-current' -- 260.19.12 driver. It seems to either be a hardware  problem on the nVidia 210, or the drivers doesn't support it properly.

---

### Post by efflandt on 2010-10-26
I have a GT 220 and have not had any trouble with the 256.53 driver in 10.10 beta (no sluggish issues others had), 260.19.06 they switched to during RC, or 260.19.12.  Actually 260.19.06 generated a rash of errors in dmesg and /var/log/messages [NVRM: os_raise_smp_barrier(), invalid context!], but that did not affect operation any.

Some people seem to be going through contortions to get 260.19.12, but it is simple now.  If using a version originally installed from the repositories or System > Administration > Additional Drivers, just go to Additional Drivers, and **remove** your current version, and reboot (which will fall back to nouveau).

**sudo add-apt-repository ppa:ubuntu-x-swat/x-updates**

**sudo apt-get update**

Go back to Additional Drivers and **activate** nvidia, reboot.

If you manually blocked or removed nouveau, or installed drivers directly from nvidia, you are on your own.

---

### Post by cigtoxdoc on 2010-10-26
I followed instructions given above and it did not add any nvidia drivers.

Ubuntu said it could not find proprietary drivers

John

---

