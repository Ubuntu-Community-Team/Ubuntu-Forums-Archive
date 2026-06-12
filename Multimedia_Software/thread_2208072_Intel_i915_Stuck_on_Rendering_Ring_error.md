---
title: "Intel i915: Stuck on Rendering Ring error"
date: 2014-02-26
forum: Multimedia Software
---

### Post by micheleg on 2014-02-26
HI all,

I noticed that  when I browse google maps and I play videos on youtube   my screen freezes for a while (e.g. 10 seconds).  I tried Chrome and Chromium.
Looking at dmesg output I see the following error messages ( I can provide more infos about the i915 error status)

```

[ 3113.833867] [drm:i915_hangcheck_elapsed] *ERROR* stuck on render ring[ 3113.833873] [drm] capturing error event; look for more information in /sys/kernel/debug/dri/0/i915_error_state
[ 3113.845550] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0x1804000 ctx 2) at 0x1806d78
[ 3125.855201] Watchdog[5402]: segfault at 0 ip 00007f24ca98acf8 sp 00007f24b5450700 error 6 in libcontent.so[7f24ca2cb000+eb1000]
[ 3129.841932] [drm:i915_hangcheck_elapsed] *ERROR* stuck on render ring
[ 3129.841996] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0x68c2000 ctx 2) at 0x68c4f88

```

I tired some of the suggestions given in: [https://wiki.archlinux.org/index.php/Intel_Graphics](https://wiki.archlinux.org/index.php/Intel_Graphics)  such as switching from SNA acceleration to UXA but nothing is changes.

The same error "seems" not happen with Firefox. 

Do you have any suggestion? Do you think it is due to 3D acceleration used by chrome?

Regards, Michele.



I run ubuntu 13.10 in Lenovo T410, Kernel 3.11.0-17-generic and the following video configuration:
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 21ce
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

```

---

### Post by CitadelUniversal on 2014-02-26
What's your system specs? You stated it's i915 intel chipset, I've got an Intel Pentium 4 Dual-Core i915 chipset but it doesn't slow down though I'm using Mozilla Firefox - does this happen on MS Windows.....

Also if your motherboard has multi-threading support if disabled you should enable it in the bios.

Edit: Don't read up help pages for other distro's like Arch Linux they are totally different to Ubuntu with different patches.

---

### Post by micheleg on 2014-02-26
Hi,

my system is Ubuntu 13.10, Lenovo T420 core i5 and Intel. Below more infos about my graphic card:

```

 sudo lshw -C video
PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5000(size=64)





```

---

### Post by jdfoote on 2014-03-20
Any luck? I have the same problem, with the same card.

---

### Post by juliobahar on 2014-03-29
Exactly the same problem here and have been haunting me, since I upgrade to Ubuntu 13.10. Any suggestions yet?

---

### Post by Toz on 2014-03-29
If you're getting the:
> [drm:i915_set_reset_status] *ERROR* render ring hung inside bo
...error, have a look at [this bug report]("https://bugs.freedesktop.org/show_bug.cgi?id=70151").

---

### Post by juliobahar on 2014-03-29
I did exactly as the thread mentioned installing oibaf  "Updated and Optimized Open Graphics Drivers" for intel-graphic cards. As well as updating my desktops motherboards bios. Nothing seemed to help. Chrome sit freezes on Google Maps.

And yes, I'm getting this [drm:i915_set_reset_status] *ERROR* render ring hung inside bo

What else should I do?

---

### Post by Toz on 2014-03-29
Might be a long shot, but have you tried changing accelmethod back to uxa (default has been switched to sna). To see what it is currently set to:
```
cat /var/log/Xorg.0.log | grep -i accelmethod
```

To change it back to sna, with root privileges, create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection
```
You'll need to log out and back in again to test.

Otherwise, your best bet will be to either create a new bug report or piggy-back off of an existing one. [Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1282867") is launchpad bug report.

---

### Post by juliobahar on 2014-04-04
I do believe the UXA acceleration method did work for me. Google maps never frozen since. I'm really grateful. Thank you

---

