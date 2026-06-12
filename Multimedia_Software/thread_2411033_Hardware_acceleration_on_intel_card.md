---
title: "Hardware acceleration on intel card"
date: 2019-01-23
forum: Multimedia Software
---

### Post by nicolasr75 on 2019-01-23
Hi,

I have an old Dell laptop (Inspiron 6400) which I want to use for watching TV live streams and Youtube.
Since the system is x86, I could only install Ubuntu 16.04:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.5 LTS
Release: 16.04
Codename: xenial
```

My problem is that both Chromium and Firefox consume nearly 100% CPU when watching videos. Seemingly hardware acceleration is not working. For Chromium I was told to check via

```
chrome://media-internals/
video_decoder: FFmpegVideoDecoder
```

(it should be GpuVideoDecoder!)

I first checked which graphics card is in use (sorry, it's in German):

```
$ sudo lshw -c video
  *-display:0             
       Beschreibung: VGA compatible controller
       Produkt: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2
       Bus-Informationen: pci@0000:00:02.0
       Version: 03
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: msi pm vga_controller bus_master cap_list rom
       Konfiguration: driver=i915 latency=0
       Ressourcen: irq:16 memory:eff00000-eff7ffff ioport:eff8(Größe=8) memory:d0000000-dfffffff memory:efec0000-efefffff memory:c0000-dffff
  *-display:1 UNGEFORDERT
       Beschreibung: Display controller
       Produkt: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2.1
       Bus-Informationen: pci@0000:00:02.1
       Version: 03
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm bus_master cap_list
       Konfiguration: latency=0
       Ressourcen: memory:eff80000-efffffff
```


Corresponding driver files are here:

```
$ ls /usr/lib/i386-linux-gnu/dri
dummy_drv_video.so  nouveau_drv_video.so  radeon_dri.so
i915_dri.so         nouveau_vieux_dri.so  radeonsi_dri.so
i965_dri.so         r200_dri.so           radeonsi_drv_video.so
i965_drv_video.so   r300_dri.so           swrast_dri.so
kms_swrast_dri.so   r600_dri.so           virtio_gpu_dri.so
nouveau_dri.so      r600_drv_video.so     vmwgfx_dri.so

```
Here is the output of vainfo:

```
$ vainfo
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/i386-linux-gnu/dri/i915_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

Interestingly vainfo is looking for [LEFT][COLOR=#222222][FONT=Verdana]i915_drv_video.so but my system only has
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]i965_drv_video.so. Is this maybe also the cause for Chromium failing to use
hardware acceleration?

I'm out of ideas at this point. I couldn't find any resource on how to install a
driver version which has this file. Nor do I know if vaapi has configuration
options for changing the file it is looking for.

Any idea how to solve this?[/FONT][/COLOR][/LEFT]

I found some related posts but they are so deep in the details that I can't really follow:
[https://alioth-lists.debian.net/pipermail/pkg-multimedia-maintainers/2013-January/031015.html](https://alioth-lists.debian.net/pipermail/pkg-multimedia-maintainers/2013-January/031015.html)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=704801](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=704801)

---

### Post by CatKiller on 2019-01-23
> **nicolasr75 said:**
> Is this maybe also the cause for Chromium failing to use
hardware acceleration?



Not directly. Hardware acceleration wouldn't work in the browser regardless.

The Chromium developers don't trust the drivers to do the right thing in all cases, so they've simply disabled hardware acceleration for everyone on Linux. There *are* builds that will enable hardware acceleration through VA-API (the hardware acceleration that Intel uses), but you have to search them out, and possibly change some settings. 

For diagnosing where you stand with hardware acceleration, I'd suggest using a local file using an encoding that you should have hardware acceleration for, and using mpv to try playing it, since that can be made to use whichever hardware acceleration is available.

---

### Post by nicolasr75 on 2019-01-23
I will try what you suggest.

Just because I forgot to mention it:
I installed a beta Chromium with the hardware acceleration option as described here:
[https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html)
So the option is available now but it doesn't work. I still suspect that it has to do with
the missing file [LEFT][COLOR=#000000][FONT="Ubuntu Mono"]i915_drv_video.so.
[/FONT][/COLOR][/LEFT]

---

### Post by mc4man on 2019-01-23
That chipset is based on  [Intel GMA 950]("https://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-950.2177.0.html") which has no support for hardware decoding of pretty much anything, (possibly just MPEG2 videos 
 There won't be vaapi support available thru libva for it.

---

### Post by Autodave on 2019-01-24
Can you give us the specs on that machine?  CPU cores and speed, amount of RAM.  I did a little research and that could have been ordered in many different configurations.  However, the base config is probably not enough to stream full screen.

Also, are you run an ad blocker?  If not, at least try uBlock in Firefox.  If you are running an ad blocker, switch to uBlock and be sure to disable the other one.

---

