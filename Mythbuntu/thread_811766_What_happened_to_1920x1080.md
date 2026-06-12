---
title: "What happened to 1920x1080?"
date: 2008-05-29
forum: Mythbuntu
---

### Post by Caps18 on 2008-05-29
I know that my graphics card had been working at 1920x1080, but a few days ago it went down to 1280x720 and the 1920x1080 option has disappeared (I restarted the computer, but I didn't think I changed anything).  In Mythbuntu 7.10, the screen resolution program or nvidia-settings does not have the 1920x1080 resolution choice now.

Is there a problem with my xorg.conf file do you think?

On a side note, is there a way to easily change the screen resolution from 1920x1080 to 1024x768 with a keyboard command?

Thanks

---

### Post by superm1 on 2008-05-29
> **Caps18 said:**
> I know that my graphics card had been working at 1920x1080, but a few days ago it went down to 1280x720 and the 1920x1080 option has disappeared (I restarted the computer, but I didn't think I changed anything).  In Mythbuntu 7.10, the screen resolution program or nvidia-settings does not have the 1920x1080 resolution choice now.

Is there a problem with my xorg.conf file do you think?

On a side note, is there a way to easily change the screen resolution from 1920x1080 to 1024x768 with a keyboard command?

Thanks
Check for any EDID errors in /var/log/Xorg.0.log.  If something cropped up, I'd suspect that cable connected to your TV went bad.

---

### Post by Caps18 on 2008-05-29
Do HDMI cables go bad?  

I will look at that log file and post it here tonight.

---

### Post by tedder on 2008-05-29
caps18, are you connected directly to your TV, or does it go through a receiver?

If the latter, it probably can't autodetect though the receiver.

---

### Post by Trollslayer on 2008-05-29
> **Caps18 said:**
> I know that my graphics card had been working at 1920x1080, but a few days ago it went down to 1280x720 and the 1920x1080 option has disappeared (I restarted the computer, but I didn't think I changed anything).  In Mythbuntu 7.10, the screen resolution program or nvidia-settings does not have the 1920x1080 resolution choice now.

Is there a problem with my xorg.conf file do you think?

On a side note, is there a way to easily change the screen resolution from 1920x1080 to 1024x768 with a keyboard command?

Thanks

Do you have a monitor connected at the same time? It may be picking up the EDID information from both and trying to reconcile them.

---

### Post by Caps18 on 2008-06-03
From Xorg.0.log:
> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "TV: 640x480 +0+0, DFP: nvidia-auto-select +0+0; TV: nvidia-auto-select +0+0, DFP: NULL; TV: nvidia-auto-select +1280+0, DFP: 1280x720 +0+0; TV: nvidia-auto-select +720+0, DFP: 720x480 +0+0; TV: nvidia-auto-select +800+0, DFP: 800x600 +0+0; TV: nvidia-auto-select +640+0, DFP: 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.10.51
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:2:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     SONY AVAMP (DFP-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, TV-0
(II) NVIDIA(0): Assigned Display Devices: DFP-0, TV-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "TV:640x480+0+0,DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0):     "TV:nvidia-auto-select+0+0,DFP:NULL"
(II) NVIDIA(0):     "TV:nvidia-auto-select+1280+0,DFP:1280x720+0+0"
(II) NVIDIA(0):     "TV:nvidia-auto-select+720+0,DFP:720x480+0+0"
(II) NVIDIA(0):     "TV:nvidia-auto-select+800+0,DFP:800x600+0+0"
(II) NVIDIA(0):     "TV:nvidia-auto-select+640+0,DFP:640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2304 x 768

I'm really not sure why it thinks it is 2304x768...


From /etc/X11/xorg.conf:
> Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "TV: 640x480 +0+0, DFP: nvidia-auto-select +0+0; TV: nvidia-auto-select +0+0, DFP: NULL; TV: nvidia-auto-select +1280+0, DFP: 1280x720 +0+0; TV: nvidia-auto-select +720+0, DFP: 720x480 +0+0; TV: nvidia-auto-select +800+0, DFP: 800x600 +0+0; TV: nvidia-auto-select +640+0, DFP: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


I will check one thing by only plugging in the 37" LCD that should get detected at 1920x1080 after a restart.

Does anybody know how it was working at 1920x1080, and then after a restart, it lost the 1920x1080 options?

---

### Post by Caps18 on 2008-09-19
[SOLVED]

Just for future reference:

This was caused by having it plugged into the powered HDMI splitter when the computer is restarted.  By having it plugged only into the 37" 1080p HDTV, it sets the resolution to 1920x1080 and keeps it there when plugged back into the splitter.

---

