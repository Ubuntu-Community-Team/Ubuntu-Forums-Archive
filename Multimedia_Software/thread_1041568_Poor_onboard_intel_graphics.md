---
title: "Poor onboard intel graphics"
date: 2009-01-16
forum: Multimedia Software
---

### Post by _jj on 2009-01-16
Hi,
Just done a completely clean install of Intrepid, my graphics performance is pretty poor!  I can't enable compiz, windows are slow to minimise, firefox is very sluggish.  I think some of the problem might be to do with my onboard graphics card working poorly.  The trouble is I am not sure where to start.  Here is some output that might help you help me.

```

lshw -class display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```
from lspci -v
```

Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
        Subsystem: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

```
from xorg.conf
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```

Any help to make my computer a bit less painful to use would be much appreciated!

---

### Post by tpd2049 on 2009-01-17
I'm having the same problem w/ this devise...except mine won't even work unless I'm in the safe mode!  I posted yesterday but no response yet...hope your post gets better response than mine...I'll be watching!

---

### Post by emshains on 2009-01-17
That's intel alright !

Have you installed the right drivers ? System->Administration->Restricted Driver Manager, or something like that. Launch it, and see whether or not you have installed the right drivers. You might still be using MESA.

---

### Post by _jj on 2009-01-17
I have noticed that if I run openbox rather than gnome the performance of (in particular) firefox is much improved, though this might be a separate issue, irritatingly it fails if I try to run a gnome session with openbox as the window manager.

I will try the restricted driver advice as soon as I am back in front of my computer (it is at work) if you know a way to check remotely I can try via ssh.

---

### Post by emshains on 2009-01-17
Well, openbox is a load lighter than gnome, so that should be normal. 

I don't really know how to check it, although, you could search for the right driver on the net, and check how to install it through ssh with apt.

---

### Post by desconocido on 2009-01-18
> **emshains said:**
> That's intel alright !

Have you installed the right drivers ? System->Administration->Restricted Driver Manager, or something like that. Launch it, and see whether or not you have installed the right drivers. You might still be using MESA.

When I look at System->Administration->Hardware Drivers, I get the message "No proprietary drivers are in use on this system". I guess this means that I am using the MESA library. Is that a bad thing?

My system actually works fine except for when I try and run Sketchup under Wine, when it fails badly.

> $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4
GLX version: 1.2

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2

$ lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

By the way, does that mean I am using Mesa version 1.3 or 7.0.3?

---

### Post by _jj on 2009-01-20
Ok, it appears I am currently running the MESA driver, how do I switch to the intel driver?  Which I found [here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=865&DwnldID=8203&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng").

Alternatively, I seem to have the package xserver-xorg-video-intel installed, how do I enable it?

From searching I notice that this seems to be a common problem with this graphics chipset, would I do better to cut my losses and buy something like [this]("http://www.amazon.co.uk/PNY-Verto-GeForce-6200-PCI/dp/B000FS4MLK/ref=sr_1_2?ie=UTF8&s=electronics&qid=1232454228&sr=1-2").  Recommendations of a better PCI/AGP 4x card for linux/ubuntu welcome!

---

