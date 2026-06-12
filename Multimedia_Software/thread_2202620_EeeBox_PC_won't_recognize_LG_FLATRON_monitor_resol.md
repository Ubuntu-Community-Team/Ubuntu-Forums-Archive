---
title: "EeeBox PC won't recognize LG FLATRON monitor resolution properly"
date: 2014-01-30
forum: Multimedia Software
---

### Post by Ulf_Dunkel on 2014-01-30
I run Ubuntu 13.30 on an EeeBox PC EB1007 with an LG FLATRON E2342 monitor plugged on VGA.

Firstly, Ubuntu just offered basic resolutions: 1024x724 + 800x600.
Then, I tried to adjust things by creating a /etc/X11/xorg.conf file with the following content:

```
# 2014-01-30 fd for LG FLATRON E2342

Section "Device"
        Identifier      "FLATRON E2342"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "LG"
        Horizsync       30-83
        Vertrefresh     56-75
        Modeline        "1920x1080@56"  160.00  1920 2040 2240 2560  1080 1083 1088 1118 -hsync +vsync
        Modeline        "1920x1080@60"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
        Modeline        "1920x1080@70"  204.25  1920 2056 2256 2592  1080 1083 1088 1127 -hsync +vsync
        Gamma           1
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "FLATRON E2342"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1920x1080@56"  "1920x1080@60"  "1920x1080@70"
        EndSubSection
EndSection
```

After a reboot, the system offered the 1920x1080 resolution but it looks rather slobbery, like with a shadow on everything. I am quite sure that my settings miss something, but I don't know what else I should add.

Due to the fact, that the EeeBox PC EB1007 has graphic onchip and that I didn't find any other information about it, I didn't add a "Driver" line to the "Device" section.

I'd be glad to get any hints or help. Thank you all.

---

### Post by Bucky Ball on 2014-01-30
*Thread moved to **Multimedia & Video**.*

Presuming you are using the open-source drivers, then? Please post the output of:

```
sudo lshw -C video
```

arandr is helpful for dual-monitor setups. It is in the Software Centre. Install and have a look what that offers.

---

### Post by Ulf_Dunkel on 2014-01-30
Hi there. Thank you for your reply.

```
$ sudo lshw -C video
  *-display:0
       Beschreibung: VGA compatible controller
       Produkt: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2
       Bus-Informationen: pci@0000:00:02.0
       Version: 00
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: msi pm vga_controller bus_master cap_list rom
       Konfiguration: driver=i915 latency=0
       Ressourcen: irq:41 memory:fbc80000-fbcfffff ioport:c800(Größe=8) memory:d0000000-dfffffff memory:fbb00000-fbbfffff
  *-display:1 UNGEFORDERT
       Beschreibung: Display controller
       Produkt: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2.1
       Bus-Informationen: pci@0000:00:02.1
       Version: 00
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm bus_master cap_list
       Konfiguration: latency=0
       Ressourcen: memory:fbd00000-fbd7ffff
```

This PC has only one external monitor plugged. Should I really install **arandr**?

---

### Post by Ulf_Dunkel on 2014-01-30
I have now enhanced my /etc/X11/xorg.conf file and added the driver. The first section now reads:

```

Section "Device"
        Identifier      "FLATRON E2342"
        Driver          "i915"
EndSection
```

But the screen still shows shadowed output after a reboot.

---

### Post by kostkon on 2014-01-30
Sorry to be the bearer of bad news, but,

while I was researching for a new cheap external monitor for my netbook with Pineview N4xx Atom, the same chipset like your mini PC, i.e. NM10 (and thus) with 3150 GMA for VGA, I found out that the vga output of 3150GMA can only support resolutions up to 1600x900 (I also downloaded its manual from HP and it confirmed this, it says vga port max. res is 1600x900@60Hz). That's why I specifically bought a 20in. monitor with 1600x900 native res and from a brand that offers monitors with EDIDs that generally work without problems under linux, Samsung (it was also cheap); and it only took me 15secs to set up the monitor in 12.04.

Hope that helps.

---

### Post by Ulf_Dunkel on 2014-01-30
Hi kostkon.
Thank you for pointing me this information. Why does another monitor (Samsung SyncMaster 2243LNX) with 1680x1050 show a perfectly sharp screen when its horizontal number of pixels is larger than the maximum amount supported by the 3150 GMA VGA port (1600x900)?

Now I have added more Modelines for "1440x900@60" and "1600x900@60" to my /etc/X11/xorg.conf file, but the screen still doesn't show sharp text and images after switching its resolution via the System panel.

---

### Post by kostkon on 2014-01-30
> **Ulf_Dunkel said:**
> Hi kostkon.
Thank you for pointing me this information. Why does another monitor (Samsung SyncMaster 2243LNX) with 1680x1050 show a perfectly sharp screen when its horizontal number of pixels is larger than the maximum amount supported by the 3150 GMA VGA port (1600x900)?

Now I have added more Modelines for "1440x900@60" and "1600x900@60" to my /etc/X11/xorg.conf file, but the screen still doesn't show sharp text and images after switching its resolution via the System panel.
I talked about the max res, which is 1600x900, but yes it can support up to 1680 pixels for width, I can confirm that because I remember reading about it on a forum.

Your monitor's native res is 1920x1080 so any other lower resolution will appear blurry, I am not sure you can do anything about it.

Hope that helps.

EDIT: also go up to 1080 for height, sorry, so max res of 3150 can be 1680x1050, I agree, but not more than that!

---

