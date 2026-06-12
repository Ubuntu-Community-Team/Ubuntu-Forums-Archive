---
title: "HDMI troubleshooting on 13.10"
date: 2013-10-31
forum: Multimedia Software
---

### Post by luciany on 2013-10-31
Hi,

could you please help me test and find the connection HDMI problem on my laptop
thankms in advance for any support
lucian

**********************************************************
    product: Aspire 5750 ()    vendor: Acer
    width: 64 bits
 *-core
       description: Motherboard
       product: JE50_HR
 *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
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
             resources: irq:42 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:2000(size=64)
 *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:c0600000-c0603fff


 [FONT=arial]******************************[/FONT][FONT=arial]******************************[/FONT][FONT=arial]*************[/FONT]
[FONT=arial]xrandr -q
[/FONT]
[FONT=arial]Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 32767 x 32767
LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+1366+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i     60.1*+   50.0     60.0  
   1920x1080      24.0     24.0  
   1280x720       60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       75.1     70.1     60.0  
   1440x480i      60.1     60.1  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  
[/FONT]
[FONT=arial]**************************************************************************[/FONT]
[FONT=arial]luciany@lap00:~$ cat /var/log/Xorg.0.log| grep -i hdmi
[    34.023] (II) intel(0): Output HDMI1 has no monitor section
[    34.023] (--) intel(0): Output HDMI1 using initial mode 1920x1080i on pipe 1
[    34.684] (II) intel(0): switch to mode 1920x1080@60.0 on pipe 1 using HDMI1, position (0, 0), rotation normal
[    35.363] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[    55.348] (II) intel(0): switch to mode 1920x1080@60.0 on pipe 1 using HDMI1, position (0, 0), rotation normal
[    55.364] (II) intel(0): switch to mode 1920x1080@60.0 on pipe 1 using HDMI1, position (1366, 0), rotation normal
[/FONT]

---

### Post by Yellow Pasque on 2013-10-31
Be more specific. What is the issue?

---

### Post by luciany on 2013-10-31
hi,

my connection doesn't work.
no signal on TV
I need some basic commands to check the protocol/connec tion.

thanks
lucian

---

