---
title: "No TV-out for Nvidia Twinview and xorg.conf"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by jdogzilla on 2007-10-07
Hello all, I currently have a nvidia 7600 GT card connected to a Dell monitor through DVI and a 1080i flatscreen TV through the Svidio-Component cable (actually it goes nvidia card >> receiver >> tv).  I cannot seem to get the twinview display to come on the TV.  I am attaching my xorg.conf file ... can you see and tell me where I am going wrong. 

On another note, when I use the nvidia-settings utility, I can get my display out to my TV.  But when I reboot, I lose those settings and have to set them up again.  

Can someone please help?  Like in windows, is there a way that I can have my videos play directly full-screen on my TV when the card detects that the TV is connected?

Thanks

---

### Post by MrHippocampus on 2007-10-07
If you run nvidia settings with:

```
sudo nvidia-settings
```

make any changes needed and then press "Save to X Configuration File" the settings should stick after a reboot.

---

### Post by jdogzilla on 2007-10-08
That actually didn't work ... the xorg.conf file created out of this process failed the next time I booted ... it is poorly constructed and missing much of what I originally had in the xorg file prior to setting up Twinview ... I'll post the errors in my xorg.log file later and maybe that will give an indication of what is failing ... but from what I saw, it said it could not load "xf86ExecX86int10" as a result of which it could not find my connected TV.  For now, I have reverted back to my old xorg.conf file.  

Also, with Twinview and the 'rightoff' orientation option, my taskbar is stretched across both screens, which makes my clock go to the extreme right of the TV screen.  How can I setup so that the TV is just an extension screen and everything is not stretched over two screens ... should I be using "clone" instead?

---

### Post by mad chey on 2007-10-17
it seems every thread i find about this goes unsolved :(  having same problems here

---

### Post by MrHippocampus on 2007-10-17
Well, this is what I use in the "device" section of my xorg.conf and it works fine.

```

        #set twinview options
        Option "TwinView" "1"
        Option "TwinViewOrientation" "LeftOf"
        Option "MetaModes" "1280x800,nvidia-auto-select;"

        #TV standard/connector
        Option "TVStandard" "PAL-I"
        Option "TVOutFormat" "SVIDEO"

        #set laptop screen to be primary
        Option      "TwinViewXineramaInfoOrder" "DFP,TV"
```

The only changes that should need to be made are the first resolution in the MetaModes lines (you should set it to the resolution of your normal monitor) and the TVStandard (probably NTSC if your in the US)

---

