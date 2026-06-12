---
title: "Screen resolution persistently wrong / off-center"
date: 2008-06-03
forum: Multimedia Software
---

### Post by Tuor on 2008-06-03
Running Fiesty on an HP with a flat-panel monitor (1440x900), which keeps displaying everything shoved off-center about two inches to the right.

According to system settings, this *is* 1440x900, but it just ain't.

I've combed through threads, tampered with xorg.conf many many many times - everything there reads ok now, but I still run into this problem. Also, this has been brought up elsewhere, but my xorg.conf settings won't stick anymore. 

Any ideas? xorg.conf follows:

Section "Device"
        Identifier      "Intel"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-83
        VertRefresh     56-76
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16 Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


:confused:

---

### Post by cogadh on 2008-06-03
Are those refresh rates for your monitor accurate? If they are off it can screw up how the screen is displayed.

---

### Post by sonofusion82 on 2008-06-03
try the auto tune button or setting on your flat panel display.
there was also a tool that can be used to fine-tune X configuration, but i can't remember it right now

---

### Post by sonofusion82 on 2008-06-03
oh.. i think it is called xvidtune
trying running it in command line

---

### Post by Tuor on 2008-06-03
@cogadh: yep, I had to manually edit them into xorg.conf. Taken from the monitor's spec sheet.

@sonofusion82: neither work. That auto tune button is so cute! My screen wiggles back and forth a few pixels and then looks just as messed as ever.

sudo xvidtune gets this: 
Error: Can't open display:

I had an nVidia-based card installed and running fine until a few weeks ago, when its fan started whining. I pulled it, went to the Intel driver (i810), and things were fine until a few days ago. ???

Reinstalling all of that != success.

thanks for suggestions so far.

---

### Post by sonofusion82 on 2008-06-04
i am not too sure. xvidtune works for me. anyone can help?

---

