---
title: "HD TV and laptop see each other but screen is black"
date: 2014-02-23
forum: Multimedia Software
---

### Post by nicolo.p on 2014-02-23
(please don't move to Apple section)
My machine is an Apple Macbook Air 1,1 from Early 2008, and I'm running Ubuntu 12.04 with kernel Linux 3.2.0-58-generic-pae.

When I connect it to an HD TV via the minidisplayport-DVI (Apple adapter) --> DVI-HDMI (cable) I get the TV recognized in System Settings -> Displays, but the TV only gets a completely *black screen* signal (i.e. it gets a signal, because if I unplug the cable or disable the TV screen in Ubuntu the TV then says 'no signal', but this signal is just black screen).

The TV is Philips 32pfl4007m/08 but in system settings -> displays it gets named philips consumer electronics 58''

The output from xrandr (with cable plugged in) is

    ```
Screen 0: minimum 320 x 200, current 3200 x 1080, maximum 8192 x 8192
    LVDS1 connected 1280x800+0+12 (normal left inverted right x axis y axis) 286mm x 179mm
       1280x800       61.2*+
       1024x768       60.0  
       800x600        60.3     56.2  
       640x480        59.9  
    VGA1 disconnected (normal left inverted right x axis y axis)
    HDMI1 connected 1920x1080+1280+0 (normal left inverted right x axis y axis) 1280mm x 720mm
       1920x1080      60.0*+   50.0     24.0  
       1600x1200      60.0  
       1280x1024      60.0  
       1360x768       59.8  
       1024x768       60.0  
       800x600        60.3  
       640x480        60.0  
    TV1 unknown connection (normal left inverted right x axis y axis)
       848x480        59.9 +
       640x480        59.9 +
       1024x768       59.9  
       800x600        59.9
```

Am I missing some configuration in Ubuntu? or is that a driver problem for the TV or the Apple adapter? Could it be related to Compiz or intel drivers?

From Apple page I read

> Graphics and video support Intel GMA X3100 graphics processor with
144MB of DDR2 SDRAM shared with main memory

Extended desktop and video mirroring: Simultaneously supports full
native resolution on the built-in display and up to 1920 by 1200
pixels on an external display, both at millions of colors

Built-in iSight camera

Mini-DVI port

The command `lsmod | grep i915` gives

   ```
i915                  428317  4 
    drm_kms_helper         45466  1 i915
    drm                   197641  5 i915,drm_kms_helper
    i2c_algo_bit           13199  1 i915
    video                  19115  1 i915
```
Regarding nvidia drivers
since I get
```
cat /proc/driver/nvidia/version
No such file or directory
```
I believe I'm not using any nvidia drivers.

With lspci I get
```
 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
```
also
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03) (prog-if 00 [VGA controller])
        Subsystem: Apple Inc. Device 00a2
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at 90000000 (64-bit, non-prefetchable) [size=1M]
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5110 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: intelfb, i915
    
    00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
        Subsystem: Apple Inc. Device 00a2
        Flags: bus master, fast devsel, latency 0
        Memory at 90100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>
```
and `sudo lshw -C display` gives
```
*-display:0             
           description: VGA compatible controller
           product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 03
           width: 64 bits
           clock: 33MHz
           capabilities: msi pm vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irq:42 memory:90000000-900fffff memory:80000000-8fffffff ioport:5110(size=8)
      *-display:1 UNCLAIMED
           description: Display controller
           product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
           vendor: Intel Corporation
           physical id: 2.1
           bus info: pci@0000:00:02.1
           version: 03
           width: 64 bits
           clock: 33MHz
           capabilities: pm bus_master cap_list
           configuration: latency=0
           resources: memory:90100000-901fffff
```
and `randr --prop` gives
```
Screen 0: minimum 320 x 200, current 3200 x 1080, maximum 8192 x 8192
    LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
        EDID:
            00ffffffffffff000610739c01010101
            10110103801d12780a90b59958528e26
            1e505400000001010101010101010101
            010101010101521c00a0502017303020
            36001eb3100000180000000100061020
            00000000000000000a20000000fe0042
            313333455730332056300a20000000fe
            00436f6c6f72204c43440a20202000d4
        BACKLIGHT: 3906 (0x00000f42)    range:  (0,24385)
        Backlight: 3906 (0x00000f42)    range:  (0,24385)
        scaling mode:    Full aspect
            supported: None         Full         Center       Full aspect 
       1280x800       61.2*+
       1024x768       60.0  
       800x600        60.3     56.2  
       640x480        59.9  
    VGA1 disconnected (normal left inverted right x axis y axis)
    HDMI1 connected 1920x1080+1280+0 (normal left inverted right x axis y axis) 1280mm x 720mm
        EDID:
            00ffffffffffff00410c000001010101
            03140103808048780ae692a3544a9926
            0f4a4c2108008bc08180a94001010101
            010101010101023a801871382d40582c
            450000d05200001e023a80d072382d40
            102c458000d05200001e000000fc0050
            68696c697073204654560a20000000fd
            00303e0f4611000a20202020202001c9
            020331f152101f202221051404131203
            1102160715060126091f071507508301
            00006a030c003000382d802e2ee30503
            01011d803e73382d407e2c458000d052
            00001e011d80d0721c1620102c258000
            d05200009e011d00bc52d01e20b82855
            4000d05200001e011d8018711c162058
            2c250000d05200009e00000000000002
        Broadcast RGB:    Full
            supported: Full         Limited 16:2
        audio:    auto
            supported: off          auto         on          
       1920x1080      60.0*+   50.0     24.0  
       1600x1200      60.0  
       1280x1024      60.0  
       1360x768       59.8  
       1024x768       60.0  
       800x600        60.3  
       640x480        60.0  
    TV1 unknown connection (normal left inverted right x axis y axis)
        bottom margin: 37 (0x00000025)    range:  (0,100)
        right margin: 46 (0x0000002e)    range:  (0,100)
        top margin: 36 (0x00000024)    range:  (0,100)
        left margin: 54 (0x00000036)    range:  (0,100)
        mode:    NTSC-M
            supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
                       PAL-N        PAL          480p@59.94Hz 480p@60Hz   
                       576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
                       1080i@50Hz   1080i@60Hz   1080i@59.94H
       848x480        59.9 +
       640x480        59.9 +
       1024x768       59.9  
       800x600        59.9
```

Can anybody help?

---

