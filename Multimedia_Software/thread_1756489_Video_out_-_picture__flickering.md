---
title: "Video out - picture  flickering"
date: 2011-05-12
forum: Multimedia Software
---

### Post by Diaboflo on 2011-05-12
Hi,
I just installed Mythbuntu on my old laptop (lenovo with on board graphics card). I have now the problem that when I connect the TV out to my TV the picture is flickering. It looks like the image is sometimes jumping to the left or right for a fraction of a second. This usually happens when the image is not still, ie I scroll the menue or a movie is playing. I already tried different display settings but that didn't help.
Can anyone give me some hints of what the problem might be? As far as I can see it is not an ATI or Nvida graphics card.
Cheers,
Diaboflo

---

### Post by Diaboflo on 2011-05-19
no idea anyone? Any hint is appreaciated...
Cheers,
Diaboflo

---

### Post by inobe on 2011-05-19
try to install the proprietary "ati **or** nvidia" driver in hardware drivers.

these drivers have better control over your hardware.

gallium or nouveau drivers just don't cut it for what you are trying to do, which are installed by default.

running

```
lspci
```

in terminal would reveal your graphics card information.

---

### Post by Diaboflo on 2011-05-21
Hi,
I installed the NVIDIA drivers but the problem persists... It's kind of strange, sometimes it is very bad sometimes it happens only every now and then. 
lspci gives the following, it seems the graphics are neither ATI nor NVIDIA: 
```

florian@florian-v0-01:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Lenovo Device 2075
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 2075
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0200000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Lenovo Device 2075
	Flags: bus master, fast devsel, latency 0
	Memory at d0180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

...

```

Cheers,
Flo

---

### Post by inobe on 2011-05-24
> **Diaboflo said:**
> Hi,
I installed the NVIDIA drivers but the problem persists... It's kind of strange, sometimes it is very bad sometimes it happens only every now and then. 
lspci gives the following, it seems the graphics are neither ATI nor NVIDIA: 
```

florian@florian-v0-01:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Lenovo Device 2075
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 2075
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0200000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Lenovo Device 2075
	Flags: bus master, fast devsel, latency 0
	Memory at d0180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

...

```

Cheers,
Flo


sorry to get back so late, it seems you have an intel video chipset, and not "nvidia"

you may want to search here [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Intel+945GM&as_qdr=m6&sa=Google+Search&lang=en#851](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Intel+945GM&as_qdr=m6&sa=Google+Search&lang=en#851)

---

