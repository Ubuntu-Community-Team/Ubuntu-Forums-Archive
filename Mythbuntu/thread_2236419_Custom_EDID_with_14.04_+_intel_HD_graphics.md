---
title: "Custom EDID with 14.04 + intel HD graphics"
date: 2014-07-26
forum: Mythbuntu
---

### Post by Marc_Aronson on 2014-07-26
I just migrated from a mythbuntu 12.04 system with Nvidia graphics to a mythbuntu 14.04 system with Intel HD graphics. 

Under 12.04/Nvidia I used a "custom edid" by adding the following to my xorg.conf file 

```
        Option "CustomEDID" "DFP-0:/home/aronson/config_files/samsung_plasma_edid.bin"
```

Alas, 14.04 doesn't have an xorg.conf file and I'm not sure if the "CustomEDID" option works with intel graphics.

Why do I want to use a custom EDID?

The HDMI port of the mythbuntu box is connected to an HDMI switch. The switch is connected to the TV. If the HDMI switch is not set to the myththbuntu box when X loads, X cannot fetch the EDID from the TV set, and x does not configure properly.

Back on 12.04 with Nvidia graphics, it would default to 640x480. The custom EDID solved this problem. 

On 14.04 with intel HD graphics, the TV reports it isn't receiving any signal until I reset X. I am hoping that a custom EDID will solve the problem here. 

Thanks for any help you can provide!

Marc

---

### Post by Marc_Aronson on 2014-07-26
OK -- after many days of trying I suddenly figured out how to add a customer EDID.

I created a file in /usr/share/X11/xorg.conf.d

What I have now learned is that intel doesn't support custom EDIDs, so the core issue is still not resolved.

ANy ideas would be greatly appreciated!

---

### Post by T.E.N. on 2014-09-07
> **Marc_Aronson said:**
> figured out how to add a customer EDID.

I created a file in /usr/share/X11/xorg.conf.dCould you let us know what this custom file looks like and how it has to be named so that both the driver (if not Intel) and xrandr may use it?

I have a hunch that not all of [https://bugs.launchpad.net/ubuntu-desktop-tests/+bug/1169984](https://bugs.launchpad.net/ubuntu-desktop-tests/+bug/1169984) ("3.8.0-18 HDMI/DisplayPort audio regression: Either oops or opening device fails with -ENODEV") #119 or similar has been fixed, as in a switched HDMI/HTPC&receiver rig probably quite similar to yours, even Ubuntu 14.04 LTS on mainline kernel 3.16.0-031600-generic (albeit with Nvidia GT520 graphics) still freezes conspicuously close to EDID-triggered changes of the speaker setup, in particular as soon as switching sound output or re-initializing audio (e.g. starting a media player, Google Talk plugin or VirtualBox).

Also HDMI audio after having had to switch often shows 2.0 when it should be 5.1, as the monitor and projector have limited (stereo) output capabilities only or none at all.

A fixed custom EDID would prevent runtime changes likely contributing to both issues.
Unless this can be made work, hardware solutions such as an EDID inserter (cf. HDMI Emulator, EDID Emulator / Reader / Writer, HDMI Detective) or similar support in the switch itself may be required.

---

### Post by Marc_Aronson on 2014-09-07
> **T.E.N. said:**
> Could you let us know what this custom file looks like and how it has to be named so that both the driver (if not Intel) and xrandr may use it?


I am happy to help in any way I can.

Just to make sure I was clear, I was not able to get the intel driver to accept the custom EDID.

My old hardware had Nvidia graphics and I was using the proprietary Nvidia graphics driver. Back on mythbuntu 12.04 I created the file "/etc/X11/xorg.conf" with the following content:

```
Section "Screen"        Option "CustomEDID" "DFP-0:/home/aronson/config_files/samsung_plasma_edid.bin"
        Option         "ConnectedMonitor" "DFP-0"
        Identifier      "Default Screen"
        Option          "UseEvents" "True"
        DefaultDepth    24
EndSection


Section "Extensions"
        Option  "Composite"     "Disable"
EndSection


Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
EndSection

```

I used an option of one of the Nvidia tools to capture the EDID file.

Here is an extract for /var/log/Xorg.0.log that might be helpful:
```
[622650.074] (**) NVIDIA(0): Option "CustomEDID" "DFP-0:/home/aronson/config_files/samsung_plasma_edid.bin"[622650.074] (**) NVIDIA(0): Enabling 2D acceleration
[622650.074] (**) NVIDIA(0): ConnectedMonitor string: "DFP-0"
[622650.536] (**) NVIDIA(GPU-0): Using ConnectedMonitor string "DFP-0".
[622650.536] (II) NVIDIA(GPU-0): Display (SONY AVAMP (DFP-0)) does not support NVIDIA 3D Vision
[622650.536] (II) NVIDIA(GPU-0):     stereo.
[622650.537] (II) NVIDIA(0): NVIDIA GPU GeForce 7100 / nForce 630i (C73) at PCI:0:16:0
[622650.537] (II) NVIDIA(0):     (GPU-0)
[622650.537] (--) NVIDIA(0): Memory: 524288 kBytes
[622650.537] (--) NVIDIA(0): VideoBIOS: 05.73.32.09.16
[622650.537] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[622650.537] (--) NVIDIA(0): Valid display device(s) on GeForce 7100 / nForce 630i at PCI:0:16:0
[622650.537] (--) NVIDIA(0):     CRT-0
[622650.537] (--) NVIDIA(0):     SONY AVAMP (DFP-0) (connected)
[622650.537] (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
[622650.537] (--) NVIDIA(0): SONY AVAMP (DFP-0): 165.0 MHz maximum pixel clock
[622650.537] (--) NVIDIA(0): SONY AVAMP (DFP-0): Internal Single Link TMDS
[622650.558] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[622650.558] (**) NVIDIA(0):     device SONY AVAMP (DFP-0) (Using EDID frequencies has been
[622650.558] (**) NVIDIA(0):     enabled on all display devices.)
[622650.558] (==) NVIDIA(0):
[622650.558] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[622650.558] (==) NVIDIA(0):     will be used as the requested mode.
[622650.558] (==) NVIDIA(0):
[622650.558] (II) NVIDIA(0): Validated MetaModes:
[622650.558] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[622650.558] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 720
[622650.559] (WW) NVIDIA(0): Unable to support custom viewPortOut 960 x 720 +160 +0
[622650.570] (**) NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option
[622650.570] (--) Depth 24 pixmap format is 32 bpp
[622650.575] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"


```

Please let me know if there is any additional information I can supply that might help!

Marc

---

