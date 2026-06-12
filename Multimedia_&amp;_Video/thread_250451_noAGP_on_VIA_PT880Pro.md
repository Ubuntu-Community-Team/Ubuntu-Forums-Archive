---
title: "noAGP on VIA PT880Pro"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by obi22 on 2006-09-04
Hello!

I'm running DapperDrake on nVidia's AGP GF FX5200, VIA PT880Pro, Celeron 64bit and kernel 2.6.15-23-amd64-generic. I followed this **tseliot**'s HOWTO [http://www.albertomilone.eu/europeo/latest_nvidia_udsf.html]("http://www.albertomilone.eu/europeo/latest_nvidia_udsf.html")
for install latests nVidia drivers and all I get is:
```
cat /proc/driver/nvidia/agp/status
Status:          Disabled

```
witch brings me strange feeling that it's not working correctly :-k 

Here's more listings...

some dmesg output:
```

Linux agpgart interface v0.101 (c) Dave Jones
NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8762
nvidia: module license 'NVIDIA' taints kernel.

```

some lsmod output:
```

nvidia               5433176  20
i2c_core               26624  3 i2c_acpi_ec,nvidia,i2c_viapro

```
...and nothing for ```
lsmod |grep -i agp
```

and finally Xorg.conf:
```

...
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
...
Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option	   "NvAGP" "2"    # tried also without this line
EndSection

```

It looks like there's no AGP support at all, but nvidia driver is installed (I'm able to see NV logo before Xserver boot). 

Thank's for help!

---

