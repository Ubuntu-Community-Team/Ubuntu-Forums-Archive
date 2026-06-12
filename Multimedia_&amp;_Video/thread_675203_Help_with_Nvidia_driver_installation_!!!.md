---
title: "Help with Nvidia driver installation !!!"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by suryam80 on 2008-01-22
Hi,

   I have recently bought Acer aspire 9423 wsmi with Intel core 2 duo T5500, 17" WXGA+ NVIDIA GeForce Go 7300 128MB graphics card with windows Vista Home premium. I have installed ubuntu 7.10 gutsy on the machine after removing windows. Both wireless and wired network connections worked out of the box. But loading the graphics drivers and running the screen at its native resoution left me in lots of distress. I have tried lots of ways that have been suggested on various forums to install  the NVIDIA drivers namely, envy, going to the System -> Restricted Drivers Manager and 'Enabling' 'NVIDIA accelerated graphics driver (latest cards)' (results in successful installation) and installing NVIDIA-Linux-x86-169.09-pkg1.run (which shows successful installation after using 'sudo sh NVIDIA-blah-blah -k $(uname -r)'  from the console albeit I cannot use the card and change the resolution still). With all of the aforementioned installations I have tried 'sudo nvidia-settings' followed by 'nvidia-xconfig' which results in "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I am attaching a few suspicious lines from 'dmesg' for your benefit.

[15.848000] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[15.848000] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0001:00.0)
[15.848000] NVRM: The system BIOS may have misconfigured  your graphics card.
[15.848000] NVRM: The NVIDIA probe routine failed for 1 device(s)
[15.848000] NVRM: None of the NVIDIA graphics adapters were initialized!
[15.848000] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:

'sudo ddcprobe' results in garbled graphics which can only be recovered on restarting X server.

I would be extremely grateful if somebody address the issue. Thanks a lot in advance.

Cheers,
suryam80

---

### Post by wolfen69 on 2008-01-22
i have tried to install the nvidia driver on 4 different 7300 cards and have given up.(i tried many things) there are known issues with this card. i wound up uninstalling the nvidia driver and doing " sudo dpkg-reconfigure -phigh xserver-xorg" to get my resolution correct. no 3D for me until i get a new card.

good luck, you'll need it.

---

### Post by milia on 2008-06-17
> **suryam80 said:**
> Hi,

   I have recently bought Acer aspire 9423 wsmi with Intel core 2 duo T5500, 17" WXGA+ NVIDIA GeForce Go 7300 128MB graphics card with windows Vista Home premium. I have installed ubuntu 7.10 gutsy on the machine after removing windows. Both wireless and wired network connections worked out of the box. But loading the graphics drivers and running the screen at its native resoution left me in lots of distress. I have tried lots of ways that have been suggested on various forums to install  the NVIDIA drivers namely, envy, going to the System -> Restricted Drivers Manager and 'Enabling' 'NVIDIA accelerated graphics driver (latest cards)' (results in successful installation) and installing NVIDIA-Linux-x86-169.09-pkg1.run (which shows successful installation after using 'sudo sh NVIDIA-blah-blah -k $(uname -r)'  from the console albeit I cannot use the card and change the resolution still). With all of the aforementioned installations I have tried 'sudo nvidia-settings' followed by 'nvidia-xconfig' which results in "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I am attaching a few suspicious lines from 'dmesg' for your benefit.

[15.848000] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[15.848000] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0001:00.0)
[15.848000] NVRM: The system BIOS may have misconfigured  your graphics card.
[15.848000] NVRM: The NVIDIA probe routine failed for 1 device(s)
[15.848000] NVRM: None of the NVIDIA graphics adapters were initialized!
[15.848000] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:

'sudo ddcprobe' results in garbled graphics which can only be recovered on restarting X server.

I would be extremely grateful if somebody address the issue. Thanks a lot in advance.

Cheers,
suryam80

Only to acknowledge that I have the same problem with you suryam.

The main difference is that I have GeForce 8400M G on an Asus A8sc,
and have tried more or less the same.

First I tried installing the driver 173.14.09 (for 8M cards) using
the same code as you did. All went well but then I've got from the **dmesg | grep NV**

```
[    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bfff0000 (ACPI NVS)[B]
[   38.260946] nvidia: module license 'NVIDIA' taints kernel.[/B]
**[   39.162933] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:**
[   39.162935] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0001:00.0)
**[   39.162937] NVRM: The system BIOS may have misconfigured your graphics card.**
[   39.162962] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   39.162965] NVRM: None of the NVIDIA graphics adapters were initialized!
[ 8087.001366] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[ 8087.001368] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0001:00.0)
[ 8087.001373] NVRM: The system BIOS may have misconfigured your graphics card.
[ 8087.001397] NVRM: The NVIDIA probe routine failed for 1 device(s).
[ 8087.001400] NVRM: None of the NVIDIA graphics adapters were initialized!

```

Now, the /var/log/Xorg.0.log gives the following errors:

```
 more Xorg0log-dat2 | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) ****INVALID MEM ALLOCATION**** b: 0xc0000000 e: 0xc0000000 correcting

milia@Archimedes:~$ more Xorg0log-dat2 | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
**(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!**
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

```

The same errors I got installing the driver 173.14.05 with envyng.

Vesa is ok but...its a shame not using nvidia driver since we have it :(.

By the way, here's my kernel :

```
milia@Archimedes:~$ uname -a
Linux Archimedes 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

```

I'll check what happens with the previous kernel.

**ps:** the bolded text looks interesting...

**ps2**: suryam, maybe it'd be better if you changed the title to "The system BIOS may have misconfigured your graphics card.". It will be more specific and most likely motivate more people to read it :). I found it via googling...:).

**ps3: **I'm not sure though if its a motherboard problem or a graphics card problem. And that 'BIOS' thing makes me think about the 
first...

---

### Post by milia on 2008-06-18
**Update!!!!!**

I've flashed the latest bios (302, I had 206) and my nvidia driver
worked asap ! ! !

So maybe suryam you should do the same.

The following links hinted me that the BIOS would cause problems:

[http://www.nvnews.net/vbulletin/showthread.php?t=113682](http://www.nvnews.net/vbulletin/showthread.php?t=113682)
[http://www.nvnews.net/vbulletin/showthread.php?t=49951](http://www.nvnews.net/vbulletin/showthread.php?t=49951)

---

