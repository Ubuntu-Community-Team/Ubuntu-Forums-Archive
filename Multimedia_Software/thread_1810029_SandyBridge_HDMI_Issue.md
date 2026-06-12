---
title: "SandyBridge HDMI Issue"
date: 2011-07-22
forum: Multimedia Software
---

### Post by Coyote007 on 2011-07-22
Hello,

I have a problem with my monitor periodically going blank. It returns to normal* display after 1-3 seconds.

*Normal display: The quality of the display is poor -- text appears out of focus, especially when running OpenGL apps, such as Blender 2.58x.

So there are two issues, the monitor blanking out and the poor quality display.

Here is my system spec:

**OS**
Ubuntu 11.04
Kernel Linux 2.6.38-10-generic
GNOME 2.32.1

**Hardware**
WDE L2410NM monitor.
DH67BL Motherboard.
Memory: 8G
Processor 0-7: i7-2600 3.4G

**From sudo lshw -C video**
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:52 memory:fe000000-fe3fffff memory:e0000000-efffffff ioport:f000(size=64)

**From sudo xrandr**
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      60.0  
   1680x1050      60.0  
   1280x1024      75.0  
   1440x900       75.0     59.9  
   1280x800       59.8  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP2 disconnected (normal left inverted right x axis y axis)


Can someone please shed some light or offer a possible direction.

Thanks for your help!

---

### Post by khelben1979 on 2011-07-22
Have you tried using an [DVI cable]("http://en.wikipedia.org/wiki/DVI_cable") instead? I've read at different places on the web that HDMI does not work so good with Linux, depending on hardware configuration and everything.

---

### Post by Coyote007 on 2011-07-22
Hi khelben1979,

No. I have not tried a DVI cable... yet.

Unless I missed it completely, I did not see the asterisk next to HDMI in the "natty supports sandybridge" section.  Are you aware of any other issue I might expect with this system setup?

Thanks for your help!

[edit]

The L2410NM monitor does not have a DVI connector. It has an HDMI, DSUB, S-Video, etc. type connectors. The MB has the 25+5 DVI connector. Will a DVI to HDMI cable suffice?

[/edit]

---

### Post by khelben1979 on 2011-07-22
> **Coyote007 said:**
> The L2410NM monitor does not have a DVI connector. It has an HDMI, DSUB, S-Video, etc. type connectors. The MB has the 25+5 DVI connector. Will a DVI to HDMI cable suffice?

I don't know, but I think it's worth a try. Another option is to connect it to DSUB on a DVI cable using a DSUB to DVI adapter. I'm using the adapter myself and I have never any display problems (BenQ 24" LED).

---

