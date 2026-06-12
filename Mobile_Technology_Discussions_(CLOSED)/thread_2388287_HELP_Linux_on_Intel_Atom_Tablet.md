---
title: "HELP: Linux on Intel Atom Tablet"
date: 2018-03-31
forum: Mobile Technology Discussions (CLOSED)
---

### Post by 3djake on 2018-03-31
My brother gave me a box full of tablets for me to fix. 

Amongst them I found a tablet with a Quad-Core Intel Atom(Z3735G) processor, 1GB ram and 16GB internal storage. It would be fun to get a Linux distro running on it, eventually Puppy Linux or Lubuntu.
I am having trouble getting a Live USB to boot, I keep getting a initramfs prompt.

I am using isorespin.sh and I disabled splash and get the following:
```
efi: requested map not found.
esrt: ESRT header is not in the memory map.
i2c_ i2c_0: failed to register I2c client INT33FE:00 at 0x68
i2c_ i2c_0: failed to add I2C device INT33FE:00 from from ACPI
i2c_h8id i2c_GODX0911:00: failed to get GPIO interrupt 
drm:pwm_setup_backlight failed toown the pwn ch

(initramfs) unable to find a medium containing a live file system

```

Has anyone experimented with doing this and can give me some advice on how to get it to boot the Live USB?

Thanks
Regards, Jake.

---

### Post by TheFu on 2018-03-31
Tablets are not general computers.  The BIOS used will dictate what you can and cannot do with them. Some are locked to a specific OS.  The first task is to determine the EXACT model of tablet and see what others with that model have achieved.

---

### Post by C.S.Cameron on 2018-03-31
I have an Intel Atom powered Compute Stick. 
Ubuntu was missing some drivers so I used Linuxium, which added these drivers to several versions of Ubuntu.
I have been using a Pi lately for my entertainment center, so I may not be up to date, but I think this work has been superseded by the 'isorespin.sh' script which can respin an official ISO suitable for use on Intel Atom devices.
see: [http://www.linuxium.com.au/how-tos](http://www.linuxium.com.au/how-tos)

---

### Post by 3djake on 2018-04-01
> **TheFu said:**
> Tablets are not general computers.  The BIOS used will dictate what you can and cannot do with them. Some are locked to a specific OS.  The first task is to determine the EXACT model of tablet and see what others with that model have achieved.
I know this,  but the fact that it has an Intel Atom and that it goes to grub and supports efi means that in theory with a bit of hacking I should be to get it boot to Linux with limited functionality. 
It is a cheap tablet, so I doubt anyone else has done anything with this exact same model but maybe some one else has experimented with something similar.
Model TM800A510L 
BIOS Vendor: American Megatrends
Core Version: 5.008, UEFI 2.3; PI 1.2, Project Ver: 3dair 0.13 x64

> **C.S.Cameron said:**
> I have an Intel Atom powered Compute Stick. 
Ubuntu was missing some drivers so I used Linuxium, which added these drivers to several versions of Ubuntu.
I have been using a Pi lately for my entertainment center, so I may not be up to date, but I think this work has been superseded by the 'isorespin.sh' script which can respin an official ISO suitable for use on Intel Atom devices.
see: [http://www.linuxium.com.au/how-tos](http://www.linuxium.com.au/how-tos)

Thanks, respiniso is what I am using.


I suspect there are some kernel parameters I need for it to boot, another thing is once I get to the initramfs my keyboard stops functioning, so I cannot interact with the prompt.
When I tried gentoo it did not find any block devices
```
Block device /dev/sde1 is not a valid root device
could not find the block root devices in .
```

---

### Post by 3djake on 2018-04-03
Managed to boot lubuntu from SD card. It seems that when I tried to boot from USB devices it would lose connection to USB at some point loading the kernel. I have to unplug my usb keyboard and plug it back in once lubuntu has booted for it to work.

I would like to get the touchscreen to work, any ideas?

UPDATE: I got touchscreen to work  [https://ubuntuforums.org/showthread.php?t=2388608]("https://ubuntuforums.org/showthread.php?t=2388608")

---

### Post by croosi2000 on 2018-07-22
Hi, in case anyone is still interested in a solution for getting linux on that kind of tablet to work... try using WUBI. Get it here [https://github.com/hakuna-m/wubiuefi/releases](https://github.com/hakuna-m/wubiuefi/releases)

Here a little instruction [https://www.lifewire.com/wubi-linux-installation-program-2201175](https://www.lifewire.com/wubi-linux-installation-program-2201175)

Have fun

---

### Post by thuspar on 2019-03-06
> **3djake said:**
> 

Amongst them I found a tablet with a Quad-Core Intel Atom(Z3735G) processor, 1GB ram and 16GB internal storage. It would be fun to get a Linux distro running on it, eventually Puppy Linux or Lubuntu.
.

I've just installed the latest peppermint 64bit on this same tablet, no sound, no camera, but everything else works pretty sweet. Are you still interested in finding out how?

---

### Post by sashka557 on 2019-05-02
> **thuspar said:**
> I've just installed the latest peppermint 64bit on this same tablet, no sound, no camera, but everything else works pretty sweet. Are you still interested in finding out how?


 I would like to know the complete instructions on how to put BIOS or lunux (ubuntu) on my tablet.

---

### Post by retroisbest on 2019-06-04
I have a Linx1010B which is a quad core Atom [COLOR=#000000]Z3735F with 2GB of RAM and installed xubuntu 18.04 onto it, the BIOS uses a 32 bit EFI so i to used the isorepin.sh but had to resort to Rufus boot USB creator to write to my pen drive for it to be detected by the tablets BIOS, once installed it worked great, I then created an auto rotate script for it (Which rotated the display and the touchscreen input, based on the orientation i also got it to load the onscreen keyboard) Audio was a bit touchy at first but after blacklisting the hdmi audio module and turning down the microphone levels audio now works perfectly.
[/COLOR]

---

