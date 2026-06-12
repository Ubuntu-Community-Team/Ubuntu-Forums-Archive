---
title: "help getting widescreen res. on nvidia 7600 laptop."
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by syxbit on 2006-07-16
i installed the drivers through the envy script, but the screen resolution was 1024x768. (native is 1280x800)
i formatted and installed through Autimatix (same version though)
but i still can't change it
i'm shocked, as i was able to get widescreen support on my ati card. the whole reason i bought this new laptop was b/c nvidia was supposed to have better support on linux.
so far i'm not impressed.

could someone help?
thanks

---

### Post by tseliot on 2006-07-16
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

### Post by syxbit on 2006-07-16
worked
thanks a million

---

### Post by gusto5 on 2006-09-02
> **syxbit said:**
> worked
thanks a million

which solution did you use?

---

### Post by testbenchdude on 2006-12-26
Hello, I just got a Westinghouse 22w2 with a native resolution of 1680 x 1050. I went to the link supplied above and followed the directions for option 5. The only thing I changed was the part where it asks to select which resolutions to use, I selected my native res. I left the horiz and vert sync rates at default, restarted the ui as per the instructions, and presto!

Thanks a bunch, this worked like a treat.

---

### Post by Hairy_Palms on 2006-12-26
to get it working on my monitor  i had to use a program called read-edid

run "make" in the directory
    

then run "sudo make read-edid" it will print out a lot of text that should look like this
> Section "Monitor"

        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fd
        # Max dot clock (video bandwidth) 140 MHz
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
        # DPMS capabilities: Active off:yes  Suspend:no  Standby:no
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
    Identifier     "TS9"
    VendorName     "DDL"
    ModelName      "TS902W"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 76.0
    ModeLine       "1440x900" 106.5 1440 1520 1672 1904 900 903 909 934 +hsync -vsync
EndSection

edit /etc/X11/xorg.conf and replace your current monitor section with the one  you just got,

then add your resolution to your screen section
so it looks some thing like this, substitute 1440x900 for your desired resolution
> Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "TS9"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "XAANoOffscreenPixmaps"    
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

MAKE SURE THE IDENTIFIER IS THE SAME IN BOTH SECTIONS!! then just reboot, or restart your xserver and you should be able to change your resolution to widescreen :)

---

