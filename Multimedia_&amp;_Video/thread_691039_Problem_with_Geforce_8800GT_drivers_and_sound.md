---
title: "Problem with Geforce 8800GT drivers and sound"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by Lakk on 2008-02-08
I have just bought a new computer, including Geforce 8800GT. I even choose Nvidia instead of ATI partly because I've heard Ubuntu have better drivers for Nvidia.


Now I've tried install drivers for my 8800GT in 3 ways:

1. Using Synaptic and install nvidia-glx, then enable nvidia in xorg. - Total failure, can't lunch X at all, it can't identify my card it says.

2. Downloading the 169.09 drivers from nvidia.com and install. - I can start X, but when I login everything is a total mess on the screen, it's like stripes all over the screen and you can't see a thing, except some different colors within the stripes.

3. Using Envy, a lot of people seem to succeed with that. - this is what I get when I try to install Nvidia drivers with Envy:
```
Envy - Version 0.9.9
Ubuntu Gutsy 32bit
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.

```

But some people have succeeded installing drivers for nvidia Geforce 8800GT on Ubuntu 7.10 Gutsy Gibbon with Envy it seems, so I should be able to succeed somehow? Do someone have a tip how to get Envy to work for me too?


Also I can't get my audio to work at all, when I try to turn on the sound or open the Audiocontroller it says I don't have any Gstreamer plugins. I've tried all the packages in synaptic with Gstreamer who I thought could possibly work, but without success. What should I do?

---

### Post by sanddgroper on 2008-02-08
Hi Lakk
You say you used the Nvidia-glx driver from synaptic but not the Nvidia-glx new driver.
I think you need the new driver.
Also there has been some problems with the 8800GT card.A quick search using
8800GT may throw up some solutions

HTH

Cheers
Sandy

---

### Post by Lakk on 2008-02-08
It's the same thing with nvidia-glx-new.

I know a lot of people have problems with Geforce 8800 GT. I have read as much I could found, the people who gets it working have used Envy.

But I just tried install the nvidia drivers manually in Envy. I got it working, just one problem.. When I start Ubuntu with nvidia installed and enabled, the fan on my card start working at full power and it gets rather warm, just like it does the first seconds when you start the computer. It keeps working at full speed until I shut down Ubuntu, and then it starts again as fast as I boot Ubuntu and X is loaded.

Now I've experiment for hours with the packages I saw Envy install, and with the configurations Envy made in xorg.conf... It seems like it's the package *nvidia-kernel-2.6.22-14-386* who make the drivers work and at the same time makes my card working way to much. That packages can't be installed through synaptic, it says the packages doesn't have a version but exist in the database. So Envy get it from somewhere else I think, but you can still remove the package through synaptic. I don't even know if the information about that package is useful, I just throw out as much information as possibly hoping someone can give me the solution.

Does anyone have a clue how to fix the problem with my card working too hard just by running Ubuntu when I have the drivers enabled? 
(Right now I doesn't have the drivers enabled, it doesn't seems good for the card and besides I can't stand the sound, so I'm back at scratch with just some more information.)


And I still have the problem with the sound, I don't think it's actually a big problem, I just can't find any information about it when I search for help. Do I have to configure something? Or is it jus a gstreamer plug-in? In that case what plug-in?
The sound is even more important to me than the drivers, so please help someone!

---

### Post by Therion on 2008-02-08
Okay I'm running an 8800GT myself with no problem.  I've used Envy many times over and it's never failed me.  Have you tried using Envy to PURGE the currently installed nVidia driver-installation and then use it to *re-install*?

For your sound issues have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide") for help.

---

### Post by beyton on 2008-02-08
See: [ubuntu-ky.ubuntuforums.org/showthread.php?t=315430]("ubuntu-ky.ubuntuforums.org/showthread.php?t=315430")

This will cure your fan problem. What driver are you using with envy? I and many others had problems with 169.07, but not 169.09.

---

### Post by or1on on 2008-02-08
i run a bfg 8800gt aswell ive always just installed the drivers from nvidias site, and the latest drivers get rid of the full power fan problem..if u can get x running with the drivers perhaps your xorg,conf is just messed up like wrong horizontal or vertical sync rates for your monitor...not sure if that would make stripes in your screen but sumthing to look at...her's my module, device, monitor, and screen sections to give you sumthing to reference too just make sure you use the horizontal and vertical refresh rates for your monitor

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-G520"
    HorizSync       30.0 - 130.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1600x1200_85 +0+0; 1600x1200 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Lakk on 2008-02-08
> Okay I'm running an 8800GT myself with no problem.  I've used Envy many times over and it's never failed me.  Have you tried using Envy to PURGE the currently installed nVidia driver-installation and then use it to *re-install*?

Yes I have. Weird thing that it works for some people and some not? :???:


> 
For your sound issues have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide") for help.
Thanks, it seems a bit hard (I haven't been working with this kind of thing before) but I'm sure I will work it out. Right now I have problem with downloading anything from [ftp://.](ftp://.)...
It seems like I miss some ftp-plug-in and I can't found anything that seems to work in Firefox. It have always worked before without needing something to get installed. Do you know the exact package to install?

> See: ubuntu-ky.ubuntuforums.org/showthread.php?t=315430
Thanks, but is the fan problem just that the fan is working to hard? Won't the card overheat if I slow down the fan to normal?

> This will cure your fan problem. What driver are you using with envy? I and many others had problems with 169.07, but not 169.09.
That's really interesting information! I can only choose between:
196.07
96.43.01
71.86.01
So no, I haven't tried the 169.09 version. Only the 196.07.
I see that my Envy version is 0.9.9 and that there is a newer version. I will try the newer version now immediately and see if I get more alternatives  :)

> 
i run a bfg 8800gt aswell ive always just installed the drivers from nvidias site, and the latest drivers get rid of the full power fan problem..if u can get x running with the drivers perhaps your xorg,conf is just messed up like wrong horizontal or vertical sync rates for your monitor...not sure if that would make stripes in your screen but sumthing to look at...her's my module, device, monitor, and screen sections to give you sumthing to reference too just make sure you use the horizontal and vertical refresh rates for your monitor
I'm very aware of the horiz and vertical syncs in xorg.conf and I have the correct syncs for my monitor :) Besides that shouldn't make a different in this matter?
I tried configure and experiment with everything Envy added to xorg too. The problem isn't in there :)

Thanks a lot for the fast answers everyone! :)

---

### Post by Lakk on 2008-02-08
Now I've fixed both the drivers and the sound! :)

I used the "workaround" on [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) and got the sound working. But I'm not really satisfied with the quality. At least I have sound until I have the energy to get something better :)

The drivers didn't worked correctly at first either. I installed the latest version of Envy so I could install the 169.09 version. The installation went smoothly and when I rebooted, the drivers was installed and enabled, still things who need the drivers didn't worked. So I fixed the sound and rebooted. I was happy the sound worked and then I tested the drivers again and the drivers worked too! :)

Thanks for the help! :)

---

