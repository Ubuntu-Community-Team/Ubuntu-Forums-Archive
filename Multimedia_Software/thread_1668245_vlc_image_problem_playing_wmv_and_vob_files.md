---
title: "vlc image problem playing wmv and vob files"
date: 2011-01-16
forum: Multimedia Software
---

### Post by red1916 on 2011-01-16
hi,

when playing dvd's, vob files and wmv files, the image comes with high contrast colors ,very intense red/green/blue. very dark too. 

I have vlc 1.1.4 installed, using ubuntu 10.10, libdvdcss2 installed.

for the rest of the video formats it seems to work fine. any ideas on what should I start debugging?  

thx in advance

---

### Post by mideal on 2011-01-17
Does still another one have this problem?

It still  occurs on my computer (since I installed 10.4 last October), too. It does not depend on video format as it happens with mp4 and flv, and as well with VLC as with standard "Video-Player".

A workaround for VLC is to start the video, pause it (just to stop annoying audio output) and  start it another time with another program instance (parallel!), then the video is shown correctly. That does work with Video-Player, as the video is opened with the already running instance.

Does anybody know how to fix it permanantly?

Thanks, Dirk

---

### Post by no2498 on 2011-01-17
this has helped with the blue tint in all the players
its a problem in totem
open totem start your video
click edit, preference, display, set the hue down till your movie look good reset to default 
with the colors you may need to set more 

i hope it helps you

---

### Post by red1916 on 2011-01-20
sorry took a while to answer but last days I have been experimenting as much as I could to recreate error and isolate as much as possible the cause:

my system information (obtained from lshw):
[I]Ubuntu 10.10 Maverick
description: Notebook
    product: 2055B46
    vendor: LENOVO
    version: ThinkPad T500
graphics:
pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:cff00000-cfffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 3650
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:45 memory:d0000000-dfffffff ioport:2000(size=256) memory:cfff0000-cfffffff memory:cff00000-cff1ffff[/I]

a new installation after following all steps to have necessary libraries to play wmv and dvd files will work perfectly

[http://www.uluga.ubuntuforums.org/showthread.php?t=766683&highlight=wmv+play](http://www.uluga.ubuntuforums.org/showthread.php?t=766683&highlight=wmv+play)

so, what is causing the fail?  Compiz (installed from the ubuntu software center). fails recreates once I have it installed and goes if I uninstall it. so my guess is that some library from the compiz windows manager is in conflict with the VLC libraries 

a workaround... VLC will show the colors (balance) distorted but gxine won't. and after gxine runs, if I close the video, VLC will work fine.

but this is as far as my knowledge goes to find the why it happens, any inputs?

thanks

---

