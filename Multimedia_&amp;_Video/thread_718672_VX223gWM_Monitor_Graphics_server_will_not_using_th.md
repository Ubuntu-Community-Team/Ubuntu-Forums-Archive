---
title: "VX223gWM Monitor Graphics server will not using this monitor"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by obievil on 2008-03-08
I installed Ubuntu 7.10 a few days ago, everythings been great on it except for one thing. 

The graphic server will not start if I have my Viewsonic VX223gWM Monitor attached to it. I can put a Standard Tube monitor to boot up with, then swap the cable and it works fine but it will not boot with the viewsonic monitor attached. 

So far I have tried the following.

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

and this command
```

md5sum /etc/X11/xorg.conf |sudo tee /var/lib/x11/xorg.conf.md5sum

```
Give me Permission denied, even though it asked for the admin password and I supplied it.

[http://ubuntuforums.org/showthread.php?t=441076](http://ubuntuforums.org/showthread.php?t=441076)

Tried installing the ATI drivers using this guide

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

the best luck I've had is to add this to my Xorg.conf file
```

        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

```
This lets me boot up to my viewsonic but says it's in a low graphics mode and it will not let me switch out of 800x600. 

Someone told me to add vega=701 to my GRUB loader, but when I opened it up everything looked commented out, and I didn't want to screw with it.

The only thing I did notice is that in Windows it only wants to run at a refresh rate of 60hz

---

