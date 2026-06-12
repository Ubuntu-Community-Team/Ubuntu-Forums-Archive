---
title: "Nvidia: Blackscreen on startup if not NvAGP0 (logs attached)"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by Chewi on 2007-04-11
Hi, on startup of X Linux dies an instant death. Blackscreen and nothing works anymore.

The only workaround is setting NvAGP to 0, which is not really an option, because i want to use beryl and be able to play some games. I need AGP.

I get this error with the Ubuntu kernel as well as a vanilla 2.6.20 compiled. With Ubuntu's driver-Package as well as 9746 and 9755.
The same result every time.

The funny thing is, before starting the x-server, looking at /proc/driver/nvidia/agp, it recognizes my host-bridge and abilities as well as the card's properly...

Any ideas plz ?



My system:
-P4-3GHz
-2gig RAM
-Sparkle 7600 GS
-ASUS-Mailbord with  Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02) (Bios up to date)
-Ubuntu Edgy (up to date) and tested on feisty

Attached are:
-nvidia-bugreport (without X running and with NvAGP0)
-xorg.conf
-/proc/driver/nvidia-stuff
-versions of kernel and xorg
-Xorg-Log, recorded with sync-mounted hdd, so it should be acuarate up to the very moment, the system crashes.

---

### Post by kerry_s on 2007-04-11
I don't think it really matters, you should still get accelaration with agpgart, which is prefered.
```

        Option "NvAGP" "integer"
                Configure AGP support. Integer argument can be one of:
                0 : disable agp 
                1 : use NVIDIA's internal AGP support, if possible 
                2 : use AGPGART, if possible 
                3 : use any agp support (try AGPGART, then NVIDIA's AGP) 
                Please note that NVIDIA's internal AGP support cannot
                work if AGPGART is either statically compiled into your
                kernel or is built as a module, but loaded into your
                kernel (some distributions load AGPGART into the kernel
                at boot up).  Default: 3 (the default was 1 until after
                1.0-1251).

```

---

### Post by Chewi on 2007-04-11
Believe me, neither 1 nor 2 nor 3 work for me...
They all end up in a blackscreen.

I'm only able to startup with NvAGP 0 :(

---

### Post by kerry_s on 2007-04-11
Have you tried feisty? Your hardware is pretty new sounding and would probably need the latest of everything to function properly.

Net installer-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

---

