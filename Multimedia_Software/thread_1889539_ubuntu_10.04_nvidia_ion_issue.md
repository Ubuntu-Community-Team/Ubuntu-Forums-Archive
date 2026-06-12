---
title: "ubuntu 10.04 nvidia ion issue"
date: 2011-12-01
forum: Multimedia Software
---

### Post by ninjasFTW on 2011-12-01
Hi,
I am having some trouble wth my Ubuntu 10.04 setup running on an Nvidia Ion display.
I originally set it up about a year ago and it was working fine until a couple of weeks ago when video started stuttering and cpu usage went to 100% for a core.
I was running nvidia driver 185 and am now running 290.
however I now have an issue where gdm starts up correctly however after about 8-10 seconds the screen goes blank. I can restart the gdm service and it comes back again but then it goes blank after the same time.
If i do "alsa reload" then the same thing happens but i'm not sure if that is doing a gdm restart 
I can't see anything in /var/log/messages or dmesg
the only thing i can see in the gdm logs is gdm-session-worker[1443]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
but that appears when it starts rather than when it dies.
Does anyone have any ideas on what I can check?
DISTRIB_RELEASE=10.04
nvidia driver version: NVRM version: NVIDIA UNIX x86 Kernel Module 290.10 Wed Nov 16 19:27:25 PST 2011
 
#lsmod:
agpgart 31724 1 nvidia
 
#lshw:
*-display
description: VGA compatible controller
product: ION VGA
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: b1
width: 64 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list rom
configuration: driver=nvidia latency=0
resources: irq:22 memory:fa000000-faffffff memory:e0000000-efffffff(prefetchable) memory:f6000000-f7ffffff(prefetchable) ioport:dc00(size=128) memory:fbde0000-fbdfffff(prefetchable)
#nvidia-smi
Thu Dec 1 19:08:49 2011
+------------------------------------------------------+
| NVIDIA-SMI 2.290.10 Driver Version: 290.10 |
|-------------------------------+----------------------+----------------------+
| Nb. Name | Bus Id Disp. | Volatile ECC SB / DB |
| Fan Temp Power Usage /Cap | Memory Usage | GPU Util. Compute M. |
|===============================+======================+======================|
| 0. ION | ERR! N/A | N/A N/A |
| N/A 60 C N/A N/A / N/A | 28% 70MB / 253MB | N/A Default |
|-------------------------------+----------------------+----------------------|
| Compute processes: GPU Memory |
| GPU PID Process name Usage |
|=============================================================================|
| 0. ERROR: Not Supported |
+-----------------------------------------------------------------------------+
#nvidia-debugdump -l
Found 1 NVIDIA devices
Device ID: 0
Device name: ION
GPU internal ID: Unknown

---

### Post by inobe on 2011-12-01
sounds like the nvidia driver is causing heat or the pc case needs cleaned out.

try going back to the old driver if your case heatsinks are clean.

when you post back, let us know how you installed this driver!

---

### Post by ninjasFTW on 2011-12-01
Hi,
 
I am running a fanless AT3IONT-I DELUXE.
 
I'm not sure if it a temperature issue as nvidia-smi is not reporting any temp increases when I start up gdm.  
 
I initially installed it using by adding ppa:team-xbmc-svn/ppa to my package sources and then adding it through packagemanager.
 
I have since cleared everything and retried doing that with no result.  
My last attempt was to clear all nvidia and vdpau components and then to install the driver directly after downloading it from the nvidia site (NVIDIA-Linux-x86-290.10.run)
I have also now tried to follow my steps the first time i did it and I am getting the same error.

---

