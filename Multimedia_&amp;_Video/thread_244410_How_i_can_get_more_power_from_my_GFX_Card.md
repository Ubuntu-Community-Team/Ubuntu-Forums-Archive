---
title: "How i can get more power from my GFX Card?"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by Kameli on 2006-08-26
Hi. I'm running on AMD Athlon 64 3000+, 1024mb 400mhz,asus k8v se deluxe and the GFX Card is Club3D GeForce 6600GT AGP 128MB.

So i'm asking that can i enable FastWrite(i heard that it will increase performance a little bit)? :)

-----------------------------------------------------------------------------

kameli@kolamachine:~$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     PCI device 1106:3188
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x
Registers:       0x1f000a1a:0x00000b02

kameli@kolamachine:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0xff000e1b:0x1f000302

It says that it's supported but can i anyway turn it on safely? =)
And i also saw one thread where there guy pasted his xorg.conf Section device and there were lines what i don't have and know. Them were:

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800 GT]"
        Driver          "nvidia"
        #BusID          "PCI:1:0:0"
        Option          "NoLogo"                        "1"
        Option          "NvAGP"                         "1"
        VideoRam        131072
        Option          "RenderAccel"                   "1"
        Option          "AllowGLXWithComposite"         "1"
        Option          "EnablePageFlip"                "1"
        Option          "AGPMode"                       "4"
        Option          "AGPFastWrite"                  "1"
        Option          "EnableDepthMoves"              "1"

So what NvAGP, RenderAccel, AllowGLXWithComposite, EnablePageFlip and EnableDepthMoves means? Can i put them on for better performance? =)

kameli@kolamachine:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
fglrx
nvidia
kameli@kolamachine:~$

Why i don't have nvidia_agp there? Is it needed? :(
And is there more tricks to get full power from my gf 6600gt and maybe little more ? =)

Sorry about my english, it's little bad =) And i'm little noob. :( :oops:

---

### Post by tseliot on 2006-08-26
post the output of this command:
```
cat /proc/driver/nvidia/agp/status
```

---

### Post by Kameli on 2006-08-26
kameli@kolamachine:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled
kkameli@kolamachine:~$

:KS

---

### Post by Kameli on 2006-08-26
Tell things to this threat things whick can make better performance from CPU and momery and GFX Card! :)

I have saw many very interesting commands in xorg.conf and i would want to know what them means! :)

8) 8) 8)

---

