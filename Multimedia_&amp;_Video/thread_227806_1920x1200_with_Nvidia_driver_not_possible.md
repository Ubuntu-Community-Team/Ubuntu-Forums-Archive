---
title: "1920x1200 with Nvidia driver not possible"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by coolmike on 2006-08-02
Hi 

I'm using the nvidia 8762 driver and a HL LP2465 display. Unfortunately I'm not able to get the recomended resoultion of 1920x1200. Even Ubuntu belives it's using this resolution, the monitor is complaning that I use only 1600x1200 at 59.9 Hz. 

This is the interessting part of the xorg.conf file:

> 
Section "Monitor"
    Identifier     "HP LP2465"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6200?]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6200?]"
    Monitor        "HP LP2465"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200" "1680x1680" "1600x1600" "1600x1200" "1280x960" "1152x1152" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200" "1680x1680" "1600x1600" "1600x1200" "1280x960" "1152x1152" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200" "1680x1680" "1600x1600" "1600x1200" "1280x960" "1152x1152" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200" "1680x1680" "1600x1600" "1600x1200" "1280x960" "1152x1152" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1680x1680" "1600x1600" "1600x1200" "1280x960" "1152x1152" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1680x1680" "1600x1600" "1600x1200" "1280x960" "1152x1152" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


Can someone help me? Because it's not nice to work in this resolution with this screen.

Thanks
Michael

---

### Post by tseliot on 2006-08-02
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by coolmike on 2006-08-03
Hi

Thanks a lot for your help, the second link was the solution. Works perfect now and the quality is so much better!

Thanks
Michael

---

