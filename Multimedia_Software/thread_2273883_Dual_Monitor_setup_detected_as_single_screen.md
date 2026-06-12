---
title: "Dual Monitor setup detected as single screen"
date: 2015-04-16
forum: Multimedia Software
---

### Post by roman31 on 2015-04-16
Two similar monitors (BenQ) display the same picture and shown as single monitor under Ubuntu in **System Settings -> Displays**. This is **DELL Latitude e5550** laptop and both displays are connected via two DVI interfaces through **DELL E-PORT PLUS II DOCKING STATION**.
How to fix it?

  ```

$ lspci | grep -iE "vga|3d|2d"
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
03:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)

```

```

$ xrandr
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
eDP1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080      60.0*+   59.9     48.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

```

$ lshw -c video
[sudo] password for roman: 
  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:64 memory:f5000000-f5ffffff memory:d0000000-dfffffff ioport:f000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff

```


[IMG]http://i.stack.imgur.com/PIxRZ.png[/IMG]

---

### Post by wyattgorman on 2015-05-16
I have a very similar issue, I have two BenQ monitors connected via VGA and HDMI to a docking station with my Lenovo laptop. Only one screen (the HDMI) comes up in the Display panel in System Settings, but they are both listed perfectly in xrandr, etc. I can set the resolution of the one monitor to 3480x1080, which obviously stretches across both screens, but then it acts as a single long screen. I've been considering trying to get it to work with a tiling window manager, that would probably be easier. Did you figure out the issue?

---

### Post by 1+willempienaar+ on 2015-05-17
I also have this issue. I also have two monitors, one graphics card. I have set it up under xorg.conf as two screens, but they only show up as one :0.0 Display that is stretched. So I can basically drag windows between them. I have turned Xinerama off but it doesn't make a difference.

Would be great if I could seperate the screens somehow. I would like to avoid using a window manager.

---

