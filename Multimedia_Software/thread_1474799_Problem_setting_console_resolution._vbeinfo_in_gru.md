---
title: "Problem setting console resolution. vbeinfo in grub2 doesn't report all resolutions"
date: 2010-05-06
forum: Multimedia Software
---

### Post by tnek on 2010-05-06
I have a Asus EEE PC 1005P which I installed a Command-line system on using the Alternate Installer CD of Ubuntu Lucid Lynx. I do not have (or want) the X Window System installed.

I want to change my console screen resolution (not inside X) to 1024x600. But it isn't reported when I use vbeinfo inside grub2:

```
    grub> vbeinfo
    VBE info:   version: 3.0  OEM software rev: 1.0
                total memory: 8128 KiB
    List of compatible video modes:
    Legend: P=Packed pixel, D=Direct color, mask/pos=R/G/B/reserved
    0x112:   640 x 480 x 32   Direct, mask: 8/8/8/8  pos: 16/8/0/24
    0x114:   800 x 600 x 16   Direct, mask: 5/6/5/0  pos: 11/5/0/0
    0x115:   800 x 600 x 32   Direct, mask: 8/8/8/8  pos: 16/8/0/24
    0x101:   640 x 480 x 8    Packed
    0x103:   800 x 600 x 8    Packed
    0x111:   640 x 480 x 16   Direct, mask: 5/6/5/0  pos: 11/5/0/0
    Configured VBE mode (vbe_mode) = ox101
    grub> 

```Relevant parts of sudo lspci -v:

```
    ...     ...
    
    00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
            Subsystem: ASUSTeK Computer Inc. Device 83ac
            Flags: bus master, fast devsel, latency 0, IRQ 28
            ...
            Kernel driver in use: i915
            Kernel modules: i915
    
    00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
            Subsystem: ASUSTeK Computer Inc. Device 83ac
            Flags: bus master, fast devsel, latency 0, IRQ 28
            ...
    
    ...     ...
```Any ideas on how I can set the console resolution like I want it?

---

### Post by gastly on 2010-05-07
I'm having the exact same problem.
Running **vbeinfo** does not output the resolution of my monitor (**1440x900**).
But it is listed when I run ```
sudo hwinfo --framebuffer
```
I'm using the NVIDIA proprietary drivers. When I used the nouveau drivers, then there was no problem.
Any suggestions anyone?

---

### Post by oxleyk on 2010-05-09
Similar problem here. I'm trying change my consoles to 1024x768.  The boot menu screen gets changed but not the consoles.

This is nothing new, though.  I've never had success in changing the console resolution in any version of Ubuntu.

Kent (also)

---

### Post by inso_741 on 2010-05-16
hey I have the same problem and [here]("http://ubuntuforums.org/showthread.php?t=1481028") is my thread  :P

---

### Post by inso_741 on 2010-05-16
and by the way gastly, do you have an analog lcd?



sorry for the double post....I was just tryin to figure out what 'quick reply' does...

---

### Post by zong1 on 2010-06-20
I wonder if anyone managed to sort this out.  I have a similar problem. 

I installed ubuntustudio-look on Ubuntu 10.04, but it added its own usplash screen. I think it set the size to 640x480.  All it does is flicker during boot, which would be fine except when users have to enter the dmcrypt key during boot.  Oddly, they complain.

vbeinfo tells me that supported resolution sizes are upto 1024x768.  I changed the /etc/default/grub with the line 
GRUB_GFXMODE=1024x768
and ran update-grub.

However this did not remove the flicker nor change the resolution. Suspect I missed something.

---

