---
title: "Disabling AGPGART to enable NVAGP in Edgy"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by Simoo on 2007-04-16
Hi all,

Thought I would put together a post of how I enabled the use of Nvidia's AGP driver (Option "NvAGP" "1" in xorg.conf) in Edgy. This assumes you have the Nvidia drivers installed.

If your like me '$ cat /proc/driver/nvidia/agp/status' will return:

Status:             Enabled
Driver:              AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:                 Disabled

You can change that by:

1. Stop AGPGART from being loaded by adding these lines to '/etc/modprobe.d/blacklist':
_______________________________________________________________________________________
# Stop hotplug from loading the via (or intel) graphics at startup so we can use the Nvidia.
# (Some people may have to disable this first).
#amd64_agp 
blacklist agpgart
#blacklist intel_agp
blacklist via-agp
#amd64_agp
_______________________________________________________________________________________

2. Edit your '/etc/X11/xorg.conf' to include the line (without quotes) "Option          "NVAGP"                 "1"" in the device section. Here is an example of mine:
_______________________________________________________________________________________
Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Option          "RenderAccel"           "true"
        Option          "NVAGP"                 "1"
## TV out setup.
        Option          "TVStandard"            "PAL-I"
        Option          "TVOutFormat"           "SVIDEO"
## Enables RGB workstation overlay visuals.  This is only supported on Quadro4 and Quadro FX $
        # Option                "Overlay"               "true"
        Option          "XvmcUsesTextures"      "true"
## I set the overscan as 0.0 then use nvidia-settings.
        Option          "TVOverScan"            "0.0"
EndSection
_______________________________________________________________________________________

3. Reboot!

Now running '$ cat /proc/driver/nvidia/agp/status' should return:

Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

Now make sure your boards support the last two options:

'$ cat /proc/driver/nvidia/agp/card'

'$ cat /proc/driver/nvidia/agp/host-bridge'

4. Providing you get 'supported' for Fast Writes and SBA you can enable them by adding this line to '/etc/modprobe.d/nvidia-kernel-nkc' after 'alias char-major-195* nvidia':

"options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1"

Reboot and 'cat /proc/driver/nvidia/agp/status' should return:

Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Enabled

I will say this gave me NO 'glxgears -printfps' speed increase but I think it does for some. I learned how to do this from lots of sources so if anyone knows more, post up!

Also, since doing this I can no longer run the 'nvidia-settings' gui without first commenting out the "options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" line.

Hope this helps people.

Simon

---

### Post by kerry_s on 2007-04-16
Hmm, i get this->

```
Command @ ~ -> cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem.        
Command @ ~ -> 

```

I have no errors in my logs. My glxgears work, i get this->

C```
ommand @ ~ -> glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
Command @ ~ -> glxgears          
3457 frames in 5.0 seconds = 691.394 FPS
4747 frames in 5.0 seconds = 949.295 FPS
5449 frames in 5.0 seconds = 1089.738 FPS
4734 frames in 5.0 seconds = 946.792 FPS
4777 frames in 5.0 seconds = 955.280 FPS
4582 frames in 5.0 seconds = 916.370 FPS
5416 frames in 5.0 seconds = 1083.093 FPS
5422 frames in 5.0 seconds = 1084.283 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
Command @ ~ -> 

```

Any ideas why it would show disabled instead of like yours->

```
Status: Enabled
Driver: NVIDIA
AGP Rate: 4x
Fast Writes: Disabled
SBA: Disabled
```

---

### Post by Simoo on 2007-04-16
if you type 'dmesg' can you see AGPGART loading or an error stating Nvidia AGP could not load?

---

### Post by 3ntity on 2007-04-23
Hey,
After appying this i get:
```
~$ cat /proc/driver/nvidia/agp/status 
Status:          Disabled
```
...while this used to give me output similar to yours originally... But i guess this isn't really vital, or is it?

'$ cat /proc/driver/nvidia/agp/card'
and
'$ cat /proc/driver/nvidia/agp/host-bridge'
both work fine though...

So what exactly does this 'patch' do? 
Cheers

---

### Post by jaybombalous on 2007-10-01
> **Simoo said:**
> if you type 'dmesg' can you see AGPGART loading or an error stating Nvidia AGP could not load?

mine says that AGPGART is loading and I don't see where there is an error for anything related to AGP. 

BTW, I am using feisty if that matters.

---

### Post by jaybombalous on 2007-10-01
```
[   42.397637] [B]agpgart: Detected NVIDIA nForce2 chipset
[   42.421388] agpgart: AGP aperture is 512M @ 0xa0000000[/B]
[   42.657836] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   42.657871] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   42.663958] input: PC Speaker as /class/input/input3
[   42.792754] hda: max request size: 128KiB
[   42.795938] hda: 40021632 sectors (20491 MB) w/2048KiB Cache, CHS=39704/16/63, UDMA(100)
[   42.795946] hda: cache flushes not supported
[   42.796002]  hda: hda1 hda2 < hda5 >
[   42.925556] parport: PnPBIOS parport detected.
[   42.925672] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   42.954655] hdb: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   42.954666] Uniform CD-ROM driver Revision: 3.20
[   43.063797] nvidia: module license 'NVIDIA' taints kernel.
[   43.382111] ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 5
[   43.382116] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK4] -> GSI 5 (level, low) -> IRQ 5
[   43.382462] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   43.640237] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 10
[   43.640242] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LACI] -> GSI 10 (level, low) -> IRQ 10
[   43.640268] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   43.958570] intel8x0_measure_ac97_clock: measured 52843 usecs
[   43.958574] intel8x0: clocking to 47411
[   44.085826] fuse init (API version 7.8)
[   44.114369] lp0: using parport0 (interrupt-driven).
[   44.145347] Adding 3028212k swap on /dev/disk/by-uuid/a84045a8-793e-453f-b939-b922fe77f715.  Priority:-1 extents:1 across:3028212k
[   44.150548] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   44.161858] EXT3 FS on sda1, internal journal
[   45.583957] NET: Registered protocol family 17
[   49.527497] No dock devices found.
[   49.564449] input: Power Button (FF) as /class/input/input4
[   49.568304] ACPI: Power Button (FF) [PWRF]
[   49.595225] input: Power Button (CM) as /class/input/input5
[   49.599033] ACPI: Power Button (CM) [PWRB]
[   49.650454] ibm_acpi: ec object not found
[   49.692682] Using specific hotkey driver
[   49.754239] pcc_acpi: loading...
[   49.994620] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   49.996297] powernow: Trying ACPI perflib
[   49.996307] powernow: ACPI perflib can not be used in this platform
[   49.996309] powernow: ACPI and legacy methods failed
[   49.996310] powernow: See http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml
[   51.374126] eth0: no IPv6 routers present
[   53.988271] **NVRM: not using NVAGP, an AGPGART backend is loaded!**

```


here is what dmesg looks like, from the first sign of anything AGP to where it says AGPGART backend loaded for whatever reason.

---

### Post by hyperair on 2007-10-10
I get this in Gutsy.

---

### Post by Anubis on 2007-11-12
> **hyperair said:**
> I get this in Gutsy.

You get what?

I'm in Gutsy and this does not work as in previous releases. What the hell is wrong with Gutsy? I had to fix one bug dealing with broken frame buffer to allow console tty.

---

### Post by hyperair on 2007-11-12
Nevermind. I gave up trying to fix my NvAGP. Anyway framebuffers aren't broken, they're just disabled. You have to add them to your initramfs.

---

