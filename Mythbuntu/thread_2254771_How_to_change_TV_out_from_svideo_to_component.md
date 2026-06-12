---
title: "How to change TV out from svideo to component"
date: 2014-11-29
forum: Mythbuntu
---

### Post by davefor2 on 2014-11-29
I am running mythbuntu 14.04.1 with nvidia card
I'm wondering how to change TV out settings.
During the install I selected nvidia driver with tv out to svideo.
Is there a way to change this to component with out reinstalling?
I remember something in the control center on older versions that would allow this.
Also notice that there was not a option for HDMI for tv out does this mean that if I 
install a video card with HDMI I don't need to configure TV out?

---

### Post by dannyboy79 on 2014-11-30
what sort of graphics card do you have that you think you have component output? we check what graphics chipset you're running with the following command
```
sudo lshw -C display
```
paste back everything it returns.

---

### Post by davefor2 on 2014-11-30
The card has a dongle that has the connections for component output Red, Blue and Green. Audio will still come from 
sound card
And has output for s-video
sudo lshw -C display*-display
       description: VGA compatible controller
       product: G92 [GeForce 9800 GTX+]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:49 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:2000(size=128)

---

### Post by dannyboy79 on 2014-12-03
you need to read the nvidia documentation I believe but this may help
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

---

### Post by Lester_Burnham on 2014-12-04
Hi,

This may also help [http://www.mythtv.org/wiki/NVIDIA_Component_Out](http://www.mythtv.org/wiki/NVIDIA_Component_Out)
Might help also if you add your /etc/xorg.conf
Below is from the page listed above.

[CODESection "Screen"
       Identifier     "Default Screen"
       Device         "NVIDIA Corporation NV43 [GeForce 6600]"
       Monitor        "Visual Sensa"
       Option     "UseEDID" "FALSE"
       Option     "ConnectedMonitor" "TV"
       **Option     "TvOutFormat" "Component"**
       #------------480p Group-----------------------------
       #Option     "TVStandard" "HD480p"
       #Option     "metamodes" "CRT: 720x480 +0+0"
       #------------720p Group-----------------------------
       Option     "TVStandard" "HD720p"
       Option     "metamodes" "CRT: 1280x720 +0+0" 
       #------------1080i Group-----------------------------
       #Option     "metamodes" "CRT: 1920x1080 +0+0" 
       #Option     "TVStandard" "HD1080i" 
       Option      "AddARGBGLXVisuals" "True"
   End Section

   Section "Monitor"
       Identifier     "Visual Sensa"
       HorizSync       15.0 - 620.0
       VertRefresh     15.0 - 600.0
       # You probably do not want your screen blanking while you are watching a recording
       # Option         "DPMS"
   EndSection

   SubSection  "Display"
       Depth     24
       Modes    "720x480" "1280x720" "1920x1080"
   EndSubSection][/CODE]

Lester

---

