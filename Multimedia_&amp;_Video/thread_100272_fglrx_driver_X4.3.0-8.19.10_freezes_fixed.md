---
title: "fglrx driver X4.3.0-8.19.10 freezes fixed"
date: 2005-12-07
forum: Multimedia &amp; Video
---

### Post by dlpfmVfH on 2005-12-07
First a description of my problem:
Updated my drivers to 8.19.10 as described in the how to's
fglrxinfo..and glxinfo all said ok...direct rendering ok etc.:) 

ran xmoto...and my screen locked up, froze everything...only way out is a hard reboot...couldn't use keyboard or mouse to get out of the black screen.:(

ran glxgears same problem hard lock black screen. fgl_glxgears also but only after a few minutes...:(

search the fora and found a solution:
disabled agp 8x and fastwrites...in xorg.conf
set it to agp 4x and fastwrite off.

it worked::) 

my xorg.conf lines I used:
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
# === Misc Options ===
    Option "AGPMask"					"0x00000210"
    Option "AGPv3Mask"					"0x00000212"
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    Option "KernelModuleParm"           "agplock=0" # AGP locked user pages: disabled
    BusID "PCI:1:0:0"    # vendor=1002, device=4152

agpmask explained:
AGPMask:
 0x00000001 = AGP 1x disable (force 2x and/or 4x)
 0x00000002 = AGP 2x disable (force 1x and/or 4x)
 0x00000004 = AGP 4x disable (force 1x and/or 2x)
 0x00000010 = fast writes disable
 0x00000200 = Sidebanding disabled
 
 AGPv3Mask:
 0x00000001 = disable AGP 4x (force 8x)
 0x00000002 = disable AGP 8x (force 4x)

Hope this helps somebody else too
:)

---

### Post by daller on 2005-12-08
Have you reported a bug on this?

---

### Post by dlpfmVfH on 2005-12-09
should I report a bug with this...because I think it comes from the driver that ati releases...because the driver before this one didn't had this problem...it resurfaces now and then...

---

### Post by ShareBuntu on 2007-08-18
I know this post is from 2005 but it seemed to have worked for me with an ATI X800 SE in Fedora 7. Thanks! :)

---

