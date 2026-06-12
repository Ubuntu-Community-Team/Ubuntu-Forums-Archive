---
title: "AMD graphics card and multiple displays (notebook)"
date: 2014-11-26
forum: Multimedia Software
---

### Post by herb4 on 2014-11-26
[COLOR=#222222][FONT=Verdana]I've recently installed 14.04 on my Dell Precision M4800. Since installation I've not been able to get the dual display properly setup. I've tried the [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]proprietary [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]drivers from AMD, but when those have been installed, the second monitor is not even acknowledged (I cannot mouse to it nor is it onthe display manager window). When I use the open-source drivers I am able to get the exterior monitor to work, however the performance is terrible. I get trailers on my mouse and extremely slow response time when I do anything. I think I'm close to having this work with the open source drivers but I can't figure out what I need to change to get the correct device doing the work when the notebook is docked and the external monitor running. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]When I do have the proprietary drivers installed, it appears that randr is not allowing aticonfig to do anything.  When I power cycle the external monitor, both screens will go black and X will restart. After the restart, again the laptop monitor is the only one active and the external one undetected in the system settings menu and inactive.[/FONT][/COLOR]


```

[COLOR=#222222][FONT=Verdana]adam@herbie:~$aticonfig --query-monitor [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Error:option --query-monitor is not supported when RandR 1.2 is enabled! [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]adam@herbie:~$sudo lshw -C video [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][sudo]password for adam: [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Sorry,try again. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][sudo]password for adam: [/FONT][/COLOR]
[COLOR=#222222]  [FONT=Verdana]*-display              [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]description:VGA compatible controller [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]product:Venus XT [Radeon HD 8870M / R9 M270X] [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]vendor:Advanced Micro Devices, Inc. [AMD/ATI] [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]physicalid: 0 [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]businfo: pci@0000:01:00.0 [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]version:00 [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]width:64 bits [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]clock:33MHz [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]capabilities:pm pciexpress msi vga_controller bus_master cap_list rom [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]configuration:driver=fglrx_pci latency=0 [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]resources:irq:50 memory:e0000000-efffffff memory:f7c00000-f7c3ffffioport:e000(size=256) memory:f7c40000-f7c5ffff [/FONT][/COLOR]
[COLOR=#222222]  [FONT=Verdana]*-display[/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]description:VGA compatible controller [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]product:4th Gen Core Processor Integrated Graphics Controller [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]vendor:Intel Corporation [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]physicalid: 2 [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]businfo: pci@0000:00:02.0 [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]version:06 [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]width:64 bits [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]clock:33MHz [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]capabilities:msi pm vga_controller bus_master cap_list rom [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]configuration:driver=i915 latency=0 [/FONT][/COLOR]
[COLOR=#222222]       [FONT=Verdana]resources:irq:44 memory:f5800000-f5bfffff memory:d0000000-dfffffffioport:f000(size=64) [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]adam@herbie:~$cat /etc/X11/xorg.conf [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Section"ServerLayout" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Identifier"amd-layout" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Screen0 "amd-screen" 0 0 [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]EndSection[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]Section"Device" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Identifier"intel" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Driver"intel" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Option"AccelMethod" "uxa" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]BusID"PCI:0@0:2:0" [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]EndSection[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]Section"Device" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Identifier"amd-device" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Driver"fglrx" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]BusID"PCI:1:0:0" [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]EndSection[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]Section"Monitor" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Identifier"amd-monitor" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Option"VendorName" "ATI Proprietary Driver" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Option"ModelName" "Generic Autodetecting Monitor" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Option"DPMS" "true" [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]EndSection[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]Section"Screen" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Identifier"amd-screen" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Device"amd-device" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]Monitor"amd-monitor" [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]DefaultDepth24 [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]SubSection"Display" [/FONT][/COLOR]
[COLOR=#222222]        [FONT=Verdana]Viewport  0 0 [/FONT][/COLOR]
[COLOR=#222222]        [FONT=Verdana]Depth    24 [/FONT][/COLOR]
[COLOR=#222222]    [FONT=Verdana]EndSubSection[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]EndSection[/FONT][/COLOR]

```


[COLOR=#222222][FONT=Verdana]I've gone back to the open source as at least I can use the external monitor even if the trailers give me a headache and I have to work with delayed cursor response when editing documents.  I don't know if this is a xorg.config thing that I'm just missing or if I need to continue to bang my head against the proprietary driver wall. [/FONT][/COLOR]

```

[COLOR=#222222][FONT=Verdana]adam@herbie:~$lspci | grep VGA[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]00:02.0VGA compatible controller: Intel Corporation 4th Gen Core ProcessorIntegrated Graphics Controller (rev 06)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]01:00.0VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI]Venus XT [Radeon HD 8870M / R9 M270X][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]adam@herbie:~$sudo lshw -C video[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][sudo]password for adam: [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]*-display              [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]description:VGA compatible controller[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]product:Venus XT [Radeon HD 8870M / R9 M270X][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]vendor:Advanced Micro Devices, Inc. [AMD/ATI][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]physicalid: 0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]businfo: pci@0000:01:00.0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]version:00[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]width:64 bits[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]clock:33MHz[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]capabilities:pm pciexpress msi vga_controller bus_master cap_list rom[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]configuration:driver=radeon latency=0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]resources:irq:44 memory:e0000000-efffffff memory:f7c00000-f7c3ffffioport:e000(size=256) memory:f7c40000-f7c5ffff[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]*-display[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]description:VGA compatible controller[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]product:4th Gen Core Processor Integrated Graphics Controller[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]vendor:Intel Corporation[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]physicalid: 2[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]businfo: pci@0000:00:02.0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]version:06[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]width:64 bits[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]clock:33MHz[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]capabilities:msi pm vga_controller bus_master cap_list rom[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]configuration:driver=i915 latency=0[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]resources:irq:45 memory:f5800000-f5bfffff memory:d0000000-dfffffffioport:f000(size=64)[/FONT][/COLOR]

```


[COLOR=#222222][FONT=Verdana]Any thoughts would be appreciated.[/FONT][/COLOR]

---

