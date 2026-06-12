---
title: "Change refresh rate?"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Julius on 2007-10-27
I just installed gutsy on my computer. My video card is an nVidia gefore 7300LE, and I installed the restricted drivers. My monitor reported a refresh rate of 75Hz which as far as I know isn't supported (in windows I never had the option to set it that high, I think), it looks blurry! 
I changed the refresh rate in System > Preferences > Screen resolution and now it's back to 60Hz (the one that looks good).

Installing nvidia-settings, which initially allowed me to change the refresh rate too, broke everything and I had to remove it.  

So now it looks good in my user, but the login screen still reports 75Hz... how can I change the refresh rate system wide?
THis is what the command get-edid | parse-edid reports:


```
        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "GERICOM C700"
        VendorName "GER"
        ModelName "GERICOM C700"
        # Block type: 2:0 3:fd
        HorizSync 24-80
        VertRefresh 49-75
        # Max dot clock (video bandwidth) 140 MHz
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
        # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

        Mode    "1280x1024"     # vfreq 60.020Hz, hfreq 63.981kHz
                DotClock        108.000000
                HTimings        1280 1328 1440 1688
                VTimings        1024 1025 1028 1066
                Flags   "+HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
EndSection
```

Should I just copy that in xorg.conf?

---

### Post by TheBigBentley on 2007-10-27
Yes I am looking for the solution to this problem as well. Desktop refresh rate is fine (75) but login screen is at 60.

---

