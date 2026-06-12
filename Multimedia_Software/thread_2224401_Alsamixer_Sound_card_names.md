---
title: "Alsamixer Sound card names"
date: 2014-05-16
forum: Multimedia Software
---

### Post by metinburak on 2014-05-16
Hello,

How can i change a sound card name shown in alsamixer?

---

### Post by metinburak on 2014-05-16
[COLOR=#000000][FONT=monospace]I am trying the udev rules for changing sound card name on my Ubuntu PC.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]On my PC, there is onboard Intel sound card,[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]First, getting udev info about sound card's pcm device:[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]burak@burak:/etc$ sudo udevadm info -a -n /dev/snd/pcmC0D0p[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]Udevadm info starts with the device specified by the devpath and then[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]walks up the chain of parent devices. It prints for every device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]found, all possible attributes in the udev rules key format.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]A rule to match, can be composed by the attributes of the device[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]and the attributes from one single parent device.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]  looking at device '/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p':[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    KERNEL=="pcmC0D0p"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    SUBSYSTEM=="sound"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    DRIVER==""[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTR{pcm_class}=="generic"[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]  looking at parent device '/devices/pci0000:00/0000:00:1b.0/sound/card0':[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    KERNELS=="card0"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    SUBSYSTEMS=="sound"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    DRIVERS==""[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{id}=="PCH"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{number}=="0"[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]  looking at parent device '/devices/pci0000:00/0000:00:1b.0':[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    KERNELS=="0000:00:1b.0"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    SUBSYSTEMS=="pci"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    DRIVERS=="snd_hda_intel"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{irq}=="49"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{subsystem_vendor}=="0x103c"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{broken_parity_status}=="0"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{class}=="0x040300"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{enabled}=="1"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{consistent_dma_mask_bits}=="64"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{dma_mask_bits}=="64"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,0000000f"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{device}=="0x1c20"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{msi_bus}==""[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{local_cpulist}=="0-3"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{vendor}=="0x8086"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{subsystem_device}=="0x1587"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{numa_node}=="-1"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    ATTRS{d3cold_allowed}=="1"[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]  looking at parent device '/devices/pci0000:00':[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    KERNELS=="pci0000:00"[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    SUBSYSTEMS==""[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    DRIVERS==""[/FONT][/COLOR]


[COLOR=#000000][FONT=monospace]To rename this device, I write a udev rule in  /etc/udev/rules.d/15-myrules.rules as:[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]KERNEL=="pcmC0Dop", NAME="mycard"[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]but rebooting machine does not change the device's name.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]Where am i doing wrong?[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]Thank you.[/FONT][/COLOR]

---

