---
title: "Working with multiple monitors"
date: 2012-03-16
forum: Multimedia Software
---

### Post by Yavin on 2012-03-16
Hello, i'm working on kubuntu 11.10 on lenovo N200. I often plug in monitors that have different native resolution and also on build in screen.

When one of the monitors have been plugged in I always need to change resolution to native and set to display only external display after reboot. It was annoying so i mark "set as default..." or something similar. 

Now I unplug external monitor and boot up kubuntu with blank internal screen (kdm works, but screen turn off after login)


[U]1. how can I restore graphic settings and not change other kubuntu settings?

2. is there (it should be?!) a way to save previous monitor setting after plug in or out different monitors (default behavior on windows)?[/U]


I have intel build in video card. I could enter console after ctrl+alt+f1. 
```
$ sudo xrandr
Can't open display
```
```
$ sudo lshw
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:fc000000-fc0fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:fc100000-fc1fffff
```

---

### Post by Yavin on 2012-03-17
I found a solution to back kubuntu alive and run in "standard resolution" on build in monitor
in file: 
> .kde/share/config/startupconfig

i have lines:

```
# krandrrc Display StartupCommands ''
krandrrc_display_startupcommands='xrandr --output LVDS1 --off
xrandr --output VGA1 --pos 0x0 --mode 1920x1080 --refresh 60
xrandr --output VGA1 --primary'
```

just need to comment it out. Don't try to "save as default" next time (if you have laptop)! Maybe I can paste there some bash script, or find some program to manage this.

_I still need an answer to second question, if someone knew._

---

