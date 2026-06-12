---
title: "Must manually reset screen resolution after reboot - ubuntu 9.04 and Nvidia 180.44"
date: 2009-06-20
forum: Multimedia Software
---

### Post by pierceit on 2009-06-20
i keep having to reset my screen resolution manually to 1440X900 on ubuntu 9.04 with Nvidia 180.44 driver -- every time I reboot it goes back to 800X600 - can anyone help?

here's my xorg.conf file:


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    Modeline "1440x900_50.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1440x900 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by mhgsys on 2009-06-20
Are you adjusting the screen resolution manually with nvidia-settings?

In that case, you might wanna try setting it with :
System > Preferences > Display.

If you get;
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

Just click NO, and set the resolution.

I don't know why exactly, but it works for my GeForce4 Ti 4200.
Everytime I used nvidia-settings (even as root and saving the file to xorg.conf) my resolution kept changing back to 800 x 600 as well.
This way it keeps my display 1280x1024 all the time.

---

### Post by pierceit on 2009-06-20
wow - this actually worked - right on!

thanks for the idea - i've tried everything else in the world, can't believe I didn't try this.

great suggestion - thanks again

---

### Post by mhgsys on 2009-06-21
Your very welcome, 

Nice to know it's working.

---

### Post by trizzfizz on 2009-07-30
I love you mhgsys!

---

### Post by Kurauzah on 2009-08-07
My sincere thanks. As a new Ubuntu user it was a hell to re-set my screen res everytime. Thanks!

---

### Post by Bobba on 2009-08-30
Fantastic!! It worked :) This has been winding me up for a good 3-4 months now, thank a lot !

---

### Post by mhgsys on 2009-11-07
:lolflag:

You're all very welcome.

---

### Post by xzing on 2009-12-06
I have been having the same problem, reboot, resolution gets messed up.  But when I tried your fix I was wondering; what should I do about the refresh rate?  I am using a Sony CPD 110-GS which is a CRT.  Ubuntu is not detecting the correct monitor and thus the refresh rate is automatically set to 50 Hz.  Any suggestions?

---

### Post by mhgsys on 2009-12-11
@Xzing

Have a look over here; 

[http://ubuntuforums.org/showthread.php?t=76387](http://ubuntuforums.org/showthread.php?t=76387)

Edit: The link to the modeline generator is down on that page; You can follow the rest of the  instructions using this generator instead.

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

### Post by gliding4me on 2009-12-12
I was also just about to get in to my xorg.conf file to see if I could resolve this issue.  I have used your fix, re-booted and voila! Many thanks.

---

### Post by silverwood99 on 2009-12-12
The only problem for me is that in the display window, the highest resolution is veerrry low. Any way to add higher ones?

---

### Post by mhgsys on 2009-12-18
@Silverwood99 >

First of all; 
You could try running sudo nvidia-settings to see what options are listed, then set the screen resolution in nvidia-settings and save it to the xorg.conf,.
Restart GDM, and check if a higher resolution is available in the display settings.

If that doesn't work 

,have a look over here; [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

and 
here
[http://ubuntuforums.org/showthread.php?t=76387](http://ubuntuforums.org/showthread.php?t=76387)

Although the link to the modeline generator is down on that page; You can follow the rest of the instructions using this generator instead.

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

