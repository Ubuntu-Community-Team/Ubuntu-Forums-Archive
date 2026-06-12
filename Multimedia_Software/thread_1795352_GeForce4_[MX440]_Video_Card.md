---
title: "GeForce4 [MX440] Video Card"
date: 2011-07-02
forum: Multimedia Software
---

### Post by th1bill on 2011-07-02
I just took my AMD Athlon with 2 gig memory back-up/test-bed down and put 10.04 on with the nVidia Card in the title for my Grandson.  When I load the proprietary drive the best I get for resolution is 640x480.  Without the nVidia driver I have 1024x768 but no 3d support.  Does anyone know how I can configure the old 96 driver to at least 1024?

---

### Post by Dangertux on 2011-07-02
Did you try editing your xorg.conf?

You might wish to try adding something like this to it.
```

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation MX400 AGP"
#Monitor        "Monitor_Name" change this
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
    EndSubSection
EndSection

```Then restart xserver
```

sudo /etc/init.d/gdm restart

```That should give you other resolution options in your Nvidia X Server settings with the newer driver.

---

### Post by th1bill on 2011-07-02
Sorry for being so slow to get back to this but I am a Vietvet with the final stage of MS from being there and rest a lot.  I´ll reactivate the driver and do the edit and report back.

---

### Post by th1bill on 2011-07-02
I did the gedit xorg.conf that did not exist prior to my creating it and the highest I have is 640 before and after reboot.

Thanks for the effort but that did not work.

---

### Post by Dangertux on 2011-07-02
Dang :-/ I was hoping it did

I did find this, for the 96 series driver in question maybe it is of some use. I don't have an nvidia card anymore , so I can't really test any of this.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Thank you for your service btw :-)

Also if you didn't have xorg.conf at all you will need to generate the full config I can give you an example full config for the nvidia card in case that link doesn't work for you.

EDIT: Apparently I may have mislead you a little bit ; according to what I've read xorg.conf no longer matters as it will not be chosen over whatever is in nvidia-settings app.

---

### Post by th1bill on 2011-07-02
Just as I figured there is nothing wrong with your script but it is not saving to /etc/x11/xorg.conf.  I am, at the terminal, doing the sudo su and password and no luck at the Root Terminal also I am informed that I do not have permission to overwrite the file.

I just have no clue now.

---

### Post by th1bill on 2011-07-02
> **Dangertux said:**
> Dang :-/ I was hoping it did

I did find this, for the 96 series driver in question maybe it is of some use. I don't have an nvidia card anymore , so I can't really test any of this.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Thank you for your service btw :-)

Also if you didn't have xorg.conf at all you will need to generate the full config I can give you an example full config for the nvidia card in case that link doesn't work for you.

EDIT: Apparently I may have mislead you a little bit ; according to what I've read xorg.conf no longer matters as it will not be chosen over whatever is in nvidia-settings app.

You posted while I was writing the post following yours.  I need to r&r a bit but I&#314;l be right back.

---

### Post by BicyclerBoy on 2011-07-02
Fortunately/amazingly this version of the nvidia driver is still available with ubuntu 10.04.
Ubuntu 10.04 LTS is using Xorg 1.7.6.

The nvidia downloads copy of this driver 96.43.19 has recently been updated (6 months ago) for Xorg 1.8 & 1.9.
You would have to install 96.43.19 by the nvidia method of console login/script build etc..
It not hard but also not so easy..

If ubuntu distro version 96.43.17 does not work then perhaps the nouveau driver is a better choice because it will install from the desktop & install with 10.04 & not break with every kernel update.

The path to xorg.conf is:
/etc/X11/xorg.conf
note the capital X.

To stop/restart the X server desktop manager
[sudo] service gdm [stop|restart|start]
where [option1|option2]

---

### Post by th1bill on 2011-07-02
Right now I have killed the puter by editing the file.  I have booted it on my Natty CD and see both the xorg.conf and the xorg.conf.failsafe.  How do I delete the edited file and rename the failsafe?

And thanks in advance,

---

### Post by BicyclerBoy on 2011-07-02
[sudo] rm /etc/X11/xorg.conf

reboot into the native 10.04 installed OS..

Then run
nvidia-xconfig
this will create a basic working xorg.conf file if one does not exist & will backup any existing.

Then run
nvidia-settings...

Post your /var/log/Xorg.0.log if you still have problems.

---

### Post by th1bill on 2011-07-02
It will not boot now.  It gets to the Boot Splash and freezes.

---

### Post by Dangertux on 2011-07-02
> **th1bill said:**
> It will not boot now.  It gets to the Boot Splash and freezes.

OK is it failing to boot with the xorg.conf file?

If it is , remove the xorg.conf file by booting to he livecd like you did before. Then run Xorg --configure , this will generate a new xorg.conf, change the Driver to say Driver "vesa". This will put you at square one with no 3d effects, however, it will at least allow you to boot into xserver.

Next : you can try and make sure that the noveau driver is blacklisted in /etc/modprobe.d/blacklist.conf. 

I am not sure if that will work - As I said I can't really test this as I don't have access to this piece of hardware, I've been searching google and none of the information I am seeing seems very promising or complete. Will post again if I have a solution I think will work.

Edit : This thread MIGHT be useful look into the information posted by JohnsFine in post #8

[http://www.linuxquestions.org/questions/ubuntu-63/geforce4-mx-420-failing-on-ubuntu-10-04-a-813796/](http://www.linuxquestions.org/questions/ubuntu-63/geforce4-mx-420-failing-on-ubuntu-10-04-a-813796/)

---

### Post by BicyclerBoy on 2011-07-03
If you find yourself at a frozen boot screen because the X server fails to start..you should still be able to switch to console.
<ctrl>+<alt>+<F1> & then login..

Then edit/delete xorg.conf or run nvidia-xconfig.

---

### Post by th1bill on 2011-07-03
If I have time today, before they pick it up I&#314;l reinstall 10.04 as a dual boot, i did Mepis 8.5 and it&#347; running at 800x600.

---

